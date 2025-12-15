---
title: "Gerenciamento de Memória"
date: 2025-01-01
type: book
weight: 40
---

> *O espaço de endereçamento cria uma espécie de memória abstrata. É o conjunto de endereços que um processo pode usar para endereçar a memória.*

## Conceitos Fundamentais

O gerenciador de memória tem duas funções vitais:
1.  **Proteção:** Impedir que um processo (ex: Navegador) escreva na memória de outro (ex: Editor de Texto), o que causaria travamentos.
2.  **Realocação:** Permitir que o programa seja carregado em qualquer lugar da memória RAM, não apenas no endereço fixo onde foi compilado.

### Registradores Base e Limite
A forma mais simples de proteção.
* **Base:** Onde começa o programa na memória física.
* **Limite:** Qual o tamanho do programa.
* *Hardware:* Toda vez que o programa tenta acessar um endereço, a CPU verifica: `Base <= Endereço < Base+Limite`.

---

## Swapping (Troca de Processos)

O que fazer quando a soma da memória exigida pelos programas abertos é maior que a RAM instalada?
O **Swapping** move um processo inteiro que está ocioso da memória RAM para o Disco (HD/SSD), liberando espaço. Quando o usuário volta a usar aquele processo, o SO o traz de volta para a RAM.

### Gerenciamento de Espaços Livres
Como o SO sabe onde há buracos livres na RAM para colocar programas?
1.  **Mapas de Bits:** A memória é dividida em blocos pequenos. Um bit 0 significa livre, 1 significa ocupado.
2.  **Listas Encadeadas:** Uma lista `[Processo A] -> [Buraco Livre] -> [Processo B]`.

---

## Memória Virtual

A memória virtual é uma técnica que permite executar programas que são **maiores do que a memória física** disponível. Ela quebra o programa em pedaços pequenos chamados **Páginas**.

### Paginação (Paging)
* **Endereço Virtual:** O endereço que o programa "pensa" que está usando.
* **Endereço Físico:** O endereço real na RAM.
* **MMU (Memory Management Unit):** Um chip no processador que traduz Virtual -> Físico em tempo real.

### Tabela de Páginas
É um "mapa" que diz: "A Página 1 do Word está no Quadro 500 da RAM".

### Falta de Página (Page Fault)
Ocorre quando o programa tenta acessar uma página que **não está na RAM** (está no disco).
1.  A CPU gera uma interrupção (trap).
2.  O SO assume o controle.
3.  O SO escolhe uma página pouco usada na RAM para remover (**Page Replacement**).
4.  O SO carrega a página necessária do disco para a RAM.
5.  O programa continua como se nada tivesse acontecido.

> *Isso explica por que o computador fica lento quando a RAM enche: o disco é milhares de vezes mais lento que a RAM, e o SO fica trocando páginas o tempo todo (Thrashing).*