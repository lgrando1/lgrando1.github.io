---
title: "Gerenciamento de Memória"
type: book
weight: 40
---

> *O espaço de endereçamento cria uma espécie de memória abstrata. É o conjunto de endereços que um processo pode usar.*

## Conceitos Básicos
Dois problemas precisam ser resolvidos: **proteção** (um processo não pode escrever na memória do outro) e **realocação** (o programa pode ser carregado em qualquer lugar da RAM).

### Swapping (Troca de Processos)
Estratégia para lidar com falta de memória. Consiste em trazer um processo do disco para a RAM, executá-lo, e depois salvá-lo de volta no disco para dar lugar a outro.

### Gerenciamento de Espaços Livres
* **Mapas de bits:** A memória é dividida em unidades de alocação; bits 0 indicam livre, 1 indicam ocupado.
* **Listas encadeadas:** Uma lista mantém registro de segmentos livres e ocupados.
    * *First fit:* Pega o primeiro buraco que couber.
    * *Best fit:* Pega o menor buraco que couber (deixa sobras pequenas).
    * *Worst fit:* Pega o maior buraco disponível.

## Memória Virtual e Paginação

> *Permite executar programas maiores que a memória física, movendo pedaços (páginas) entre RAM e disco.*

### Paginação
O espaço de endereçamento virtual é dividido em **páginas**. A memória física é dividida em **quadros de página**.
A **MMU (Memory Management Unit)** mapeia endereços virtuais para físicos usando uma **Tabela de Páginas**.

### Falta de Página (Page Fault)
Quando um programa tenta acessar um endereço que não está na RAM, ocorre uma falta de página. O SO deve:
1.  Escolher uma página pouco usada na RAM para remover (swapping).
2.  Carregar a página necessária do disco para a RAM.
3.  Atualizar a tabela de páginas e retomar a execução.