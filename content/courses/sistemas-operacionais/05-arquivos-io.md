---
title: "Sistemas de Arquivos e I/O"
date: 2025-01-01
type: book
weight: 50
---

## Sistemas de Arquivos

Um **arquivo** é uma abstração para armazenar informações no disco e lê-las depois, isolando o usuário dos detalhes físicos de setores e trilhas do HD.

### Estrutura e Atributos
* **Nomeação:** Regras como tamanho do nome, distinção de maiúsculas/minúsculas (Linux distingue `Arquivo.txt` de `arquivo.txt`; Windows não).
* **Extensões:** Indicam o tipo de arquivo (.c, .txt, .pdf).
* **Metadados:** Informações extras como data de criação, data de modificação, tamanho e permissões.

### Diretórios
São arquivos especiais que servem para agrupar outros arquivos, criando uma estrutura hierárquica (árvore).

### Alocação em Disco
Como guardar um arquivo de 10MB no disco?
1.  **Alocação Contígua:** Guarda os 10MB seguidos. Leitura muito rápida, mas difícil de achar espaço contíguo se o disco estiver fragmentado.
2.  **Lista Encadeada:** O arquivo é quebrado em blocos espalhados. Cada bloco aponta para o próximo. Resolve fragmentação, mas o acesso aleatório é lento.
3.  **i-nodes (Index Nodes):** Usado no Linux. Uma pequena tabela lista onde estão os blocos do arquivo.

---

## Sistemas de Entrada e Saída (I/O)

> *As duas tarefas principais de um computador são I/O e processamento.*

### O Hardware de I/O
Os dispositivos (Mouse, Teclado, Disco, Placa de Rede) são conectados através de um **Barramento (Bus)**.
Cada dispositivo possui um **Controlador** (hardware/chip) que conversa com a CPU.

### O Driver de Dispositivo
É o software que o SO usa para falar com o controlador. O driver abstrai a complexidade: para o SO, todos os discos funcionam igual, graças aos drivers específicos de cada fabricante.

### Métodos de Transferência
1.  **E/S Programada:** A CPU fica perguntando a todo momento: "O dado chegou? O dado chegou?". (Gasta muito processador).
2.  **Interrupção:** A CPU vai fazer outra coisa. Quando o dado chega, o dispositivo "cutuca" (interrompe) a CPU.
3.  **DMA (Acesso Direto à Memória):** Usado para dados grandes (Discos). Um chip DMA copia os dados do disco direto para a RAM, sem a CPU precisar mover um dedo.