---
title: "Fundamentos e Estruturas"
type: docs
weight: 10
date: 2025-01-01
---

> **A função do sistema operacional é fornecer aos programas do usuário um modelo do computador melhor**, mais simples e mais limpo, assim como lidar com o gerenciamento de todos os recursos mencionados. *A maioria dos computadores tem dois modos de operação: **modo núcleo e modo usuário.***

## O Sistema Operacional

O sistema operacional opera em **modo núcleo** (também chamado modo supervisor). Nesse modo, **ele tem acesso completo a todo o hardware e pode executar qualquer instrução** que a máquina for capaz de executar. O resto do software opera em **modo usuário**, no qual apenas um subconjunto das instruções da máquina está disponível.

A diferença entre os **modos** exerce papel crucial na maneira como os sistemas operacionais funcionam. **Os sistemas operacionais são enormes, complexos** e têm vida longa.

### Funções do SO

Os sistemas operacionais realizam **duas funções essencialmente não relacionadas**:
1.  Fornecer a programadores de aplicativos recursos abstratos limpos em vez de recursos confusos de hardware.
2.  Gerenciar esses recursos de hardware.

> *Sistemas operacionais transformam o **feio em belo**.* Usando essa **abstração**, os programas podem criar, escrever e ler arquivos, sem ter que lidar com detalhes complexos de como o hardware funciona.

### Gerenciamento de Recursos (Multiplexação)

O gerenciamento de recursos inclui a **multiplexação** (compartilhamento) de recursos de duas maneiras diferentes:
* **Multiplexado no tempo:** Diferentes programas ou usuários se revezam usando-o (ex: impressora, CPU).
* **Multiplexado no espaço:** Cada cliente tem direito a uma parte do recurso simultaneamente (ex: memória principal).

## Hardware e Chamadas de Sistema

O sistema operacional está intimamente ligado ao hardware. A CPU, memória e dispositivos de E/S estão todos conectados por um **sistema de barramento (*bus*)**.

### Processadores e Memória
* **CPU:** O "cérebro". Possui **registradores** internos para armazenamento de variáveis e resultados temporários, cruciais para a multiplexação de tempo.
* **Memória Cache:** Memória temporária rápida (L1, L2) para evitar busca direta na RAM.
* **Memória Principal:** Armazena instruções e dados de programas em execução.

### Chamadas de Sistema (System Calls)
As chamadas de sistema são a interface entre o **espaço do usuário** e os **serviços do kernel**.
Exemplo: Ao criar uma pasta (`mkdir`), o comando no terminal invoca uma *system call* que pede ao Kernel para alterar o disco.

> **API:** Define um **conjunto de normas que possibilita a comunicação** entre plataformas. Ex: POSIX é uma API padrão para sistemas UNIX/Linux.

## Estruturas do Sistema Operacional

### 1. Monolítico
Todo o sistema operacional **é implementado como um único programa de grande porte**. Todas as funcionalidades (memória, arquivos, processos) residem no kernel.
* *Exemplos:* MS-DOS, versões antigas do UNIX.

### 2. Microkernel
O kernel é mínimo e **fornece apenas as funcionalidades básicas**. Funcionalidades adicionais (drivers, sistema de arquivos) rodam como processos de usuário. Um erro no driver de áudio não derruba o computador.
* *Exemplos:* MINIX, Redox OS.

### 3. Híbrido
Combina elementos dos dois anteriores. O kernel contém funcionalidades essenciais, mas utiliza módulos.
* *Exemplos:* Linux, Windows, macOS.

### 4. Sistemas Virtuais
Cria uma máquina virtual que **simula uma arquitetura de hardware** para cada processo.