---
title: "Processos e Threads"
type: book
weight: 20
---

> *O conceito mais central em qualquer sistema operacional é o processo: **uma abstração de um programa em execução.***

## O que é um Processo?
Um processo **é apenas uma instância de um programa em execução**, incluindo os valores atuais do contador do programa, registradores e variáveis. Cada processo tem seu próprio **espaço de endereçamento**.

Em qualquer sistema de multiprogramação, **a CPU muda de um processo para outro rapidamente**, dando a ilusão do **paralelismo**.

### Criação de Processos
Quatro eventos principais criam processos:
1.  **Inicialização do sistema** (processos de segundo plano/daemons).
2.  **Execução de uma chamada de sistema** (ex: `fork` no Linux cria um clone exato do processo pai).
3.  **Solicitação de um usuário** (clicar em um ícone, digitar comando).
4.  Início de uma **tarefa em lote**.

### Estados de Processos
Um processo pode estar em três estados:
1.  **Em execução:** Realmente usando a CPU naquele instante.
2.  **Pronto:** Temporariamente parado para deixar outro processo ser executado.
3.  **Bloqueado:** Incapaz de ser executado até que algum evento externo aconteça (ex: esperando input do teclado).

> **Processo Zombie:** Criado quando um processo filho termina antes do pai e o pai não verifica o status de saída.

## Threads (Miniprocessos)

Cada **processo** tem um espaço de endereçamento e um único thread de controle. Porém, é desejável ter múltiplos threads no mesmo espaço de endereçamento.

* **Compartilhamento:** Threads compartilham o mesmo espaço de endereçamento e dados globais.
* **Leveza:** São mais rápidos para criar e destruir do que processos.
* **Sobreposição:** Enquanto uma thread faz I/O (lento), outra pode processar dados.

### Exemplo: Processador de Texto
1.  Uma thread interage com o usuário (teclado).
2.  Outra faz reformatação em segundo plano.
3.  Uma terceira salva o backup automático no disco.
*Se fossem 3 processos separados, seria difícil compartilhar o documento na memória.*

### Concorrência e Regiões Críticas
Quando threads ou processos compartilham memória, surgem **condições de corrida**. Para evitar erros, usamos **exclusão mútua** em **regiões críticas** (partes do código que acessam recursos compartilhados).
* **Soluções:** Variáveis tipo trava, Alternância explícita, Solução de Peterson, Semáforos.