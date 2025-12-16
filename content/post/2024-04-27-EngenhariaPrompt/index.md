---
title: 'Dicas de Engenharia de Prompt'
date: '2024-04-27'
slug: prompt1
categories: []
tags: [GPT, Chat-GPT, prompt, engineering, IA, AI]
hidden: true
subtitle: ''
summary: 'Alguns padrões para otimizar a utilização de GPTs'
authors: []
lastmod: '2024-04-27T12:09:20-03:00'
featured: no
image:
  caption: ''
  focal_point: ''
  preview_only: no
projects: []
---

Outros posts sobre o tema em:

[Como Criar um Pipeline em Python para Testar Modelos no Hugging Face](https://lgrando1.github.io/post/hface/)

[Parte 1 - Instalando o Ollama no Linux](https://lgrando1.github.io/post/ollama/)

[Parte 2 - Instalando o Ollama no Windows](https://lgrando1.github.io/post/ollamawin/)

[Parte 3 - Instalando LLMs Off-line no Android - pt.1](https://lgrando1.github.io/post/llmandroid/)

[Parte 4 - Instalando LLMs Off-line no Android - pt.2](https://lgrando1.github.io/post/llmtermux/)

[Parte 5 - Quatro Maneiras de Usar LLMs Offline no Seu Computador](https://lgrando1.github.io/post/waysllms)

[Parte 6 - RAG Offline: Usando LM Studio e Ollama para Processar Documentos](https://lgrando1.github.io/post/rag/)

Realizei recentemente o curso [*Prompt Engineering for ChatGPT*](https://www.coursera.org/learn/prompt-engineering) e gostaria de compartilhar algumas anotações que realizei durante o mesmo. 

Estas ferramentas não podem ser consideradas como [fonte de fatos](https://chat.openai.com/share/36071465-b59a-44e1-a494-eaba36edc4cd), mas são excelentes como suporte para ideias e quem sabe para tirar da gaveta aquela ideia de um livro. 

O objetivo desta série é criar postagens com quatro estratégias por post. Estou utilizando como exemplo o Chat-GPT em sua versão grátis, mas você pode testar em qualquer outra ferramenta. 

Caso queira conhecer melhor o funcionamento destas ferramentas, recomendo o [texto do Stephen Wolfram](https://writings.stephenwolfram.com/2023/02/what-is-chatgpt-doing-and-why-does-it-work/) e o curso [*Prompt Engineering for ChatGPT*](https://www.coursera.org/learn/prompt-engineering) que pode ser auditado gratuitamente no Coursera. 

Os links incluem exemplos de cada item.

## 1 - São ferramentas estocásticas, por isto pode não ocorrer **repetitividade** nas respostas, já que a sua resposta depende de como elas foram treinadas:
Conforme você realiza o prompt, as ferramentas podem responder de formas diferentes, por isto é importante o refino da sua questão e testar várias estratégias. 

Ainda considerando a pergunta, quantos prêmios Nobéis o Brasil já foi agraciado? O [exemplo 1](https://chat.openai.com/share/36071465-b59a-44e1-a494-eaba36edc4cd) e o [exemplo 2](https://chat.openai.com/share/9f91d34d-87ec-49d1-bb8e-b533a0cc0972) apresentam respostas distintas para a mesma questão.

## 2 - Você pode solicitar a esta ferramenta para que ela aja conforme um personagem (ex: professor, consultor, etc.) e que a resposta seja direcionada para determinado público (jovens da terceira idade, adolescente).

A estrutura deste prompt é: 

**Aja como P e faça A** 

Onde **P** é igual ao personagem que você deseja e **A** ação que você espera dele.

Neste [exemplo](https://chat.openai.com/share/21dfd00b-cd05-44eb-9b57-3982f936b991), vou pedir para ele agir como um professor de Línguas, depois vou pedir para ele explicar o meu erro usando um exemplo de obra literária e depois para ele contextualizar um assunto atual para um cidadão do ano 1700.

## 3 - Você pode enviar novas informações para o Prompt.

Estas ferramentas possuem uma limitação do processo de treinamento. Você pode fornecer novas informações para que ele possa aprimorar a resposta.

Neste [exemplo](https://chat.openai.com/share/7adc6484-d5a0-4545-bbf9-9256a82ac82d) pedi para ele os presidentes que governaram o Brasil entre os anos 2000 a 2024 e solicitei atualização das informações com o novo presidente.

## 4 - Refinamento de questões.

Observe que a clareza com que você faz os questionamentos é importante para que você tenha respostas mais próximas do que deseja. Não adianta você pedir: Quais foram os presidentes?, se você quer uma resposta limitada por tempo. Mas você [pode pedir](https://chat.openai.com/share/34a42de3-e9c8-4d69-8941-643472f973cb) para ele como melhorar sua pergunta. 


Por enquanto são estas dicas, vimos que podem ocorrer variações nas respostas, que estas ferramentas podem agir como determinado personagem para atingir um público específico, que você pode treinar a ferramenta localmente com novas informações para que sua resposta seja mais atual e que a própria ferramenta pode lhe ajudar a refinar as suas questões.


