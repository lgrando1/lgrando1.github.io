---
title: "Escalonamento de CPU (Scheduling)"
date: 2025-01-01
type: book
weight: 30
---

> *O scheduling (escalonamento) da CPU é a base dos sistemas operacionais multiprogramados. Alternando a CPU entre os processos, o sistema torna o computador mais produtivo.*

## O Problema do Escalonamento

Se apenas uma CPU está disponível, **uma escolha precisa ser feita sobre qual processo será executado**. A parte do sistema operacional que faz esta escolha é o **Escalonador (Scheduler)**.

### Ciclo de Picos (Bursts)
Os processos não usam a CPU o tempo todo de forma igual. Eles alternam entre:
1.  **Pico de CPU:** O programa está calculando, processando dados.
2.  **Pico de I/O:** O programa está esperando o disco, a rede ou o usuário digitar algo.

> **Objetivo:** O SO deve aproveitar quando um processo entra em *Pico de I/O* (espera) para dar a CPU para outro processo que precisa de *Pico de CPU*.

---

## Tipos de Escalonamento

### 1. Sem Preempção (Cooperativo)
Uma vez que a CPU é dada a um processo, ele a mantém até que termine ou faça uma chamada de sistema (como esperar por I/O) voluntariamente.
* *Problema:* Se o programa travar num loop infinito, o computador congela.

### 2. Com Preempção
O SO pode interromper um processo à força (usando um relógio de hardware/interrupção) para dar a vez a outro. É o modelo usado em todos os sistemas modernos (Windows, Linux, macOS, Android).

### O Despachante (Dispatcher)
É o módulo que efetivamente realiza a troca:
1.  Salva o contexto do processo atual.
2.  Muda para o modo núcleo.
3.  Salta para o local do novo programa.

---

## Critérios de Desempenho

Como saber se um algoritmo de escalonamento é bom?
* **Utilização da CPU:** Manter a CPU ocupada o máximo possível (ideal: 40% a 90%).
* **Throughput:** Quantos processos são concluídos por hora/segundo.
* **Turnaround:** Tempo total desde que você abriu o programa até ele terminar.
* **Tempo de Espera:** Quanto tempo o processo ficou parado na fila de "Prontos".

---

## Algoritmos de Scheduling

### 1. FCFS (First-Come, First-Served)
O primeiro que chega é o primeiro a ser atendido. É como uma fila de banco.
* **Vantagem:** Simples de implementar.
* **Desvantagem:** Efeito Comboio (se um processo pesado chegar primeiro, todos os leves atrás dele ficam travados esperando).

### 2. SJF (Shortest Job First)
O algoritmo olha para a fila e escolhe o processo que tem o **menor próximo pico de CPU**.
* **Vantagem:** Garante o menor tempo médio de espera.
* **Desvantagem:** Impossível saber o futuro com precisão (como saber quanto tempo o processo vai demorar?). Pode causar *Starvation* (processos longos nunca rodam).

### 3. Por Prioridade
Cada processo recebe um número de prioridade. A CPU vai para o de maior importância.
* *Prioridade Estática:* Definida pelo administrador.
* *Prioridade Dinâmica:* O SO aumenta a prioridade de quem espera muito.

### 4. Round-Robin (Circular)
É o algoritmo clássico de sistemas de tempo compartilhado.
* Cada processo recebe uma fatia de tempo (**Quantum**), geralmente 10-100ms.
* Se o processo não terminar nesse tempo, ele sofre preempção e vai para o final da fila.
* Isso garante que o sistema pareça interativo e responsivo.