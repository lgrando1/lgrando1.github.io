---
title: "Prática: Linux, Docker e AWS"
date: 2025-01-01
type: docs
weight: 60
---

## Instalação e Configuração (WSL)

O **WSL (Windows Subsystem for Linux)** permite rodar um ambiente GNU/Linux completo diretamente no Windows, sem a sobrecarga de uma máquina virtual tradicional.

Para instalar, abra o **PowerShell** como Administrador e execute:

```powershell
wsl --install

```

Por padrão, será instalado o **Ubuntu**. Após o comando, reinicie o computador. Ao abrir o terminal do Linux pela primeira vez, será solicitado que você crie um **nome de usuário** e uma **senha** (UNIX).

###Gerenciamento de Pacotes (`apt`)No Ubuntu/Debian, usamos o `apt` para instalar programas:

```bash
# Atualizar a lista de repositórios
sudo apt update

# Instalar pacotes essenciais
sudo apt install neovim g++ tmux wget git

```

---

##Comandos Básicos do LinuxO terminal é a principal ferramenta de interação.

###Manipulação de Arquivos* `pwd`: Mostra o diretório atual.
* `ls`: Lista arquivos (`ls -la` mostra arquivos ocultos e permissões).
* `cd pasta`: Entra no diretório.
* `mkdir pasta`: Cria um novo diretório.
* `touch arquivo.txt`: Cria um arquivo vazio.
* `rm arquivo.txt`: Remove um arquivo (**Cuidado:** não tem lixeira).
* `rm -r pasta`: Remove um diretório e tudo dentro dele.
* `cp origem destino`: Copia arquivos.
* `mv origem destino`: Move ou renomeia arquivos.

###Permissões de ArquivosNo Linux, as permissões são divididas em **Leitura (r=4)**, **Escrita (w=2)** e **Execução (x=1)**.

| Valor | Permissão | Descrição |
| --- | --- | --- |
| 7 | rwx | Leitura, Escrita e Execução |
| 6 | rw- | Leitura e Escrita |
| 5 | r-x | Leitura e Execução |
| 4 | r-- | Somente Leitura |

**Exemplos:**

```bash
chmod 700 arquivo  # Só o dono tem acesso total.
chmod 777 arquivo  # Todos têm acesso total (inseguro).
chmod +x script.sh # Torna o arquivo executável.

```

---

##Editores e Terminal###Neovim (`nvim`)Um editor de texto modal e poderoso.

* **Modo de Inserção:** Pressione `i` para começar a digitar.
* **Sair do Modo de Inserção:** Pressione `ESC`.
* **Salvar:** Digite `:w` e `ENTER`.
* **Sair:** Digite `:q` e `ENTER`.
* **Salvar e Sair:** Digite `:wq`.

###Tmux (Terminal Multiplexer)Permite dividir a tela do terminal em vários painéis e manter sessões ativas mesmo se a conexão cair.

**Atalhos comuns (Padrão `Ctrl+b`):**

* `Ctrl+b` seguido de `"`: Divide a tela horizontalmente.
* `Ctrl+b` seguido de `%`: Divide a tela verticalmente.
* `Ctrl+b` seguido de setas: Navega entre os painéis.
* `Ctrl+b` seguido de `c`: Cria uma nova janela.

---

##Containers (Docker)> *Um container é um ambiente de runtime com todos os componentes necessários (código, dependências, bibliotecas) para executar a aplicação sem depender da máquina host.*

###Como funciona?Diferente de uma Máquina Virtual (VM) que virtualiza o hardware, o Docker virtualiza o SO usando recursos do Kernel Linux:

* **cGroups:** Controlam o uso de recursos (CPU, RAM) para que um processo não consuma tudo.
* **Namespaces:** Isolam a visão do processo (ele acha que é o único rodando no sistema).

###Comandos Essenciais```bash
# Baixar uma imagem do Docker Hub
docker pull python:3.12-slim

# Rodar um container interativo (-it cria um terminal tty)
docker run -it python:3.12-slim

# Listar containers em execução
docker ps

# Listar imagens baixadas
docker images

```

###DockerfileÉ a "receita" para criar sua própria imagem. Exemplo:

```dockerfile
# Imagem base
FROM alpine

# Comandos de instalação
RUN apk add neovim

# Comando inicial ao rodar o container
CMD ["echo", "Container Iniciado!"]

```

Para construir a imagem:

```bash
docker build -t minha-imagem .

```

---

##Nuvem (AWS EC2)O **Amazon EC2** (Elastic Compute Cloud) permite alugar servidores virtuais.

###Conectando via SSHAo criar uma instância, você baixa uma chave de acesso (`.pem`). Para conectar:

1. Mude a permissão da chave (por segurança):
```bash
chmod 400 minha-chave.pem

```


2. Conecte via terminal:
```bash
ssh -i "minha-chave.pem" ubuntu@ec2-ip-da-maquina.compute-1.amazonaws.com

```



Uma vez conectado, você tem um terminal Linux remoto onde pode instalar Docker, rodar servidores web e implantar suas aplicações.

```

```