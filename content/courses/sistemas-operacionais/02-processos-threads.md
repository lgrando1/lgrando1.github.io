---
title: "Processos e Threads"
date: 2025-01-01
type: docs
weight: 20
---

> *O conceito mais central em qualquer sistema operacional é o processo: **uma abstração de um programa em execução.***

## O Modelo de Processo

Um processo **é apenas uma instância de um programa em execução**, incluindo os valores atuais do contador do programa, registradores e variáveis.
Cada processo tem seu próprio **espaço de endereçamento** (uma lista de posições de memória que vai de 0 a algum máximo).

### A Ilusão do Paralelismo
Em qualquer sistema de multiprogramação, **a CPU muda de um processo para outro rapidamente** (dezenas ou centenas de milissegundos), dando a ilusão de que vários programas estão rodando ao mesmo tempo (pseudoparalelismo).

---

## Criação de Processos

Quatro eventos principais fazem com que processos sejam criados:

1.  **Inicialização do sistema:** Quando o SO liga, ele inicia vários processos.
    * *Primeiro plano:* Interagem com o usuário.
    * *Segundo plano (Daemons):* Rodam escondidos (ex: servidor de e-mail, gerenciador de impressão).
2.  **Execução de uma chamada de sistema:** Um processo em execução pode pedir para criar outro (ex: um navegador criando um processo para uma nova aba).
3.  **Solicitação de um usuário:** Clicar duas vezes em um ícone ou digitar um comando no terminal.
4.  **Início de uma tarefa em lote:** Em mainframes, quando há jobs na fila.

### A Chamada `fork()` (UNIX/Linux)
No Linux, a única maneira de criar um novo processo é através da chamada de sistema `fork`.
* Ela cria um **clone exato** do processo pai.
* Pai e filho têm a mesma memória e arquivos abertos, mas a partir daí seguem caminhos independentes.

#### Exemplo Prático em Python
```python
import os
import sys

pid = os.fork()

if pid < 0:
  sys.exit("Erro no Fork")

if pid == 0:
  print(f"Sou o processo FILHO. Meu PID é {os.getpid()}")
else:
  print(f"Sou o processo PAI. Criei o filho com PID {pid}")

```

---

##Estados de ProcessosDurante sua vida, um processo transita entre três estados principais:

1. **Em execução (Running):** O processo está realmente usando a CPU naquele instante.
2. **Pronto (Ready):** O processo poderia estar rodando, mas está parado temporariamente para dar vez a outro.
3. **Bloqueado (Blocked):** O processo não pode rodar até que um evento externo aconteça (ex: esperando o usuário digitar algo ou o disco ler um arquivo).

**Diagrama de Transição:**

1. *Execução -> Bloqueado:* Processo pede algo (I/O) e precisa esperar.
2. *Execução -> Pronto:* O tempo do processo acabou (Scheduler interrompe).
3. *Pronto -> Execução:* Scheduler escolhe este processo para rodar.
4. *Bloqueado -> Pronto:* O evento esperado aconteceu (I/O terminou).

---

##A Tabela de ProcessosPara gerenciar tudo isso, o SO mantém uma **Tabela de Processos** (uma lista de estruturas). Cada entrada contém o **PCB (Process Control Block)** com informações vitais:

* Estado do processo (Running, Ready, Blocked).
* Contador de programa (onde ele parou).
* Valores dos registradores da CPU.
* Arquivos abertos.
* Prioridade.

> Quando o SO troca de um processo para outro (**Mudança de Contexto**), ele salva tudo isso na tabela para poder restaurar exatamente como estava depois.

---

##Threads (Miniprocessos)Muitas vezes, um único programa precisa fazer várias coisas ao mesmo tempo.
*Por que não criar vários processos?* Porque processos são "pesados" e isolados (difícil compartilhar memória).

**A solução são as Threads:**

* **Compartilhamento:** Threads ficam dentro do *mesmo* processo e compartilham o *mesmo* espaço de endereçamento (variáveis globais, arquivos abertos).
* **Leveza:** Criar uma thread é muito mais rápido (10 a 100x) que criar um processo.

###Exemplo: Processador de TextoImagine o Word rodando com 3 threads:

1. **Thread 1:** Ouve o teclado e mouse (interação).
2. **Thread 2:** Reformata o texto e quebras de página em background.
3. **Thread 3:** Salva o arquivo no disco automaticamente a cada 5 minutos.

*Se a Thread 3 bloquear esperando o disco, a Thread 1 continua funcionando e você continua digitando!*

###Problemas de ConcorrênciaComo as threads compartilham a mesma memória, se duas tentarem escrever na mesma variável ao mesmo tempo, gera erro (**Condição de Corrida**).
Para resolver, usamos mecanismos de sincronização como **Semáforos** ou **Monitores**.

---

##Monitoramento no LinuxVocê pode ver os processos rodando agora no seu sistema usando:

* **`top` ou `htop`:** Mostra processos em tempo real, uso de CPU e Memória.
* **`ps -aux`:** Lista todos os processos do sistema.
* **`pstree`:** Mostra a árvore genealógica (quem é pai de quem).

---
