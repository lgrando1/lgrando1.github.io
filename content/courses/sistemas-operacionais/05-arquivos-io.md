---
title: "Sistemas de Arquivos e I/O"
type: book
weight: 50
---

## Sistemas de Arquivos
Um arquivo fornece uma maneira de armazenar informações no disco e lê-las depois, isolando o usuário dos detalhes físicos de armazenamento.

### Conceitos
* **Nomeação:** Regras de nomes (maiusculas/minusculas, extensões).
* **Tipos:** Regulares (texto, binário), Diretórios, Especiais (dispositivos).
* **Atributos (Metadados):** Tamanho, data de criação, permissões, dono.
* **Diretórios:** São arquivos especiais que mantêm a estrutura do sistema (pastas).

### Gerenciamento de Disco
Como armazenar um arquivo de *N* bytes?
1.  **Alocação Contígua:** Rápida, mas difícil de expandir o arquivo (precisa mover tudo).
2.  **Lista Encadeada / Blocos:** O arquivo é dividido em blocos espalhados pelo disco. Resolve a fragmentação, mas o acesso aleatório é lento.

## Sistemas de I/O (Entrada e Saída)

> *As duas tarefas principais de um computador são I/O e processamento.*

### Hardware
* **Dispositivos:** Armazenamento (disco), Transmissão (rede), Interface Humana (teclado/mouse).
* **Controladores:** Chips que controlam fisicamente o dispositivo.
* **Drivers:** Software que conversa com o controlador. O driver abstrai o hardware para o SO.

### DMA (Acesso Direto à Memória)
Permite que o controlador de disco escreva dados diretamente na memória RAM sem incomodar a CPU a cada byte, liberando o processador para outras tarefas.