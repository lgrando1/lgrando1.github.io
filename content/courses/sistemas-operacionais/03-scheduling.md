---
title: "Escalonamento de CPU (Scheduling)"
type: book
weight: 30
---

> *O scheduling da CPU é a base dos sistemas operacionais multiprogramados. Alternando a CPU entre os processos, o sistema operacional pode tornar o computador mais produtivo.*

## O Problema
Se apenas uma CPU está disponível, **uma escolha precisa ser feita sobre qual processo será executado**. A parte do sistema operacional que faz esta escolha é o **escalonador (scheduler)**.

### Ciclo de Picos de CPU e I/O
Processos alternam entre **picos de CPU** (cálculo) e **picos de I/O** (espera por disco/rede). O scheduler deve aproveitar os momentos de espera de I/O de um processo para dar a CPU a outro.

### Tipos de Escalonamento
* **Sem Preempção (Cooperativo):** O processo mantém a CPU até terminar ou fazer uma chamada de espera voluntária.
* **Com Preempção:** O SO pode interromper um processo à força (ex: interrupção de relógio) para dar a vez a outro.

## Critérios de Avaliação
* **Utilização da CPU:** Manter a CPU ocupada (40% a 90%).
* **Throughput:** Número de processos concluídos por unidade de tempo.
* **Turnaround:** Tempo total desde a submissão até a conclusão do processo.
* **Tempo de espera:** Tempo gasto esperando na fila de prontos.

## Algoritmos de Scheduling

### 1. FCFS (First-Come, First-Served)
O primeiro que chega é o primeiro a ser atendido. Simples, mas o tempo médio de espera pode ser longo (efeito comboio).

### 2. SJF (Shortest Job First)
Associa a cada processo a duração do próximo pico de CPU. A CPU é dada ao processo com o **menor** pico. Ótimo para throughput, mas difícil prever o futuro.

### 3. Prioridades
A CPU é alocada ao processo com maior prioridade (definida interna ou externamente). Problema: *Starvation* (processos de baixa prioridade podem nunca executar).

### 4. Round-Robin (Circular)
Cada processo recebe uma fatia de tempo (**quantum**). Se não terminar nesse tempo, sofre preempção e vai para o final da fila. É o sistema usado em computadores pessoais para dar a ilusão de interatividade.