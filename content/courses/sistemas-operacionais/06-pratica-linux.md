---
title: "Prática: Linux, Docker e AWS"
type: book
weight: 60
---

## Instalação e Configuração (WSL)
O **WSL (Windows Subsystem for Linux)** permite rodar Linux dentro do Windows.

```bash
# Instalar WSL (PowerShell)
wsl --install

# Instalar pacotes no Ubuntu/Debian
sudo apt update
sudo apt install neovim g++ tmux wget
Ferramentas Essenciais
Neovim (nvim)
Editor de texto terminal.

i: Entrar no modo de inserção.

ESC: Sair do modo de inserção.

:w: Salvar.

:q: Sair.

Tmux
Multiplexador de terminais. Permite dividir a tela em vários painéis.

ctrl + b seguido de %: Divisão vertical.

ctrl + b seguido de ": Divisão horizontal.

Containers (Docker)
Um container é um ambiente isolado com todas as dependências necessárias para rodar uma aplicação.

Diferença para Máquina Virtual
O Docker usa o kernel do host e isola processos usando cGroups (controle de recursos) e Namespaces (isolamento de visão), sendo muito mais leve que uma VM completa.

Comandos Básicos
Bash

# Baixar imagem
docker pull python:3.12-slim

# Rodar container interativo
docker run -it python:3.12-slim

# Listar containers ativos
docker ps
Dockerfile
Arquivo para criar imagens personalizadas:

Dockerfile

FROM alpine
RUN apk add cmatrix
CMD cmatrix
Construir: docker build -t minha-imagem .

AWS EC2
Para rodar suas aplicações na nuvem:

Criar uma instância EC2 (servidor virtual).

Conectar via SSH.

Instalar Docker e implantar seu container.