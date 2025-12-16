---
title: "Testando Modelos de IA com o HuggingFace." 
author: '' 
date: '2024-03-24' 
slug: hface
categories: [] 
tags: [ "Hugging Face", "IA", "ML", "Generativos", "Python"] 
subtitle: 'Como testar modelos do Hugging Face em tarefas de IA/ML' 
Summary: 'Como Criar um Pipeline em Python para Testar Modelos no Hugging Face' 
authors: [] 
lastmod: '2024-03-24T16:00:00-03:00' 
featured: yes 
image:
  caption: ''
  focal_point: ''
  preview_only: no
projects: []

---

<meta name="fediverse:creator" content="@lgrando@cwb.social">

Outros posts sobre o tema em:


[Dicas de Engenharia de Prompt](https://lgrando1.github.io/post/prompt1/)


[Parte 1 - Instalando o Ollama no Linux](https://lgrando1.github.io/post/ollama/)

[Parte 2 - Instalando o Ollama no Windows](https://lgrando1.github.io/post/ollamawin/)

[Parte 3 - Instalando LLMs Off-line no Android - pt.1](https://lgrando1.github.io/post/llmandroid/)

[Parte 4 - Instalando LLMs Off-line no Android - pt.2](https://lgrando1.github.io/post/llmtermux/)

[Parte 5 - Quatro Maneiras de Usar LLMs Offline no Seu Computador](https://lgrando1.github.io/post/waysllms)

[Parte 6 - RAG Offline: Usando LM Studio e Ollama para Processar Documentos](https://lgrando1.github.io/post/rag/)

A plataforma [**Hugging Face**](https://huggingface.co/) é uma portal onde a comunidade de aprendizado de máquina colabora com modelos, conjunto de dados e aplicações.


Ao acessar o site e clicar no link [Models](https://huggingface.co/models) é possível buscar por variados modelos voltados para várias tarefas de aprendizado de máquina, visão computacional, processamento natural de linguagem, áudio, dados tabulares, aprendizado por reforço e outros tipos.


Neste post apresentaremos uma introdução de como utilizar estas bibliotecas em sua máquina (ou no Google Colab). Como exemplo, é demostrado a realização de duas tarefas: o preenchimento de máscaras de texto (completar um espaço de um texto) e o resumo de um texto. 


São dois modelos/exemplos simples, mas o objetivo é realmente despertar a curiosidade em conhecer mais sobre esta plataforma.


Algumas considerações: 
1. Ao baixar o modelo em sua máquina, alguns modelos são grandes, como o segundo modelo deste tutorial que possui mais do que 1,5 GB. Neste [link](https://huggingface.co/docs/huggingface_hub/en/guides/manage-cache) é possível ver como gerenciar o cache destes modelos;
2. Se atente ao modelo que você testará, pois já foram encontrados [problemas de segurança](https://www.bleepingcomputer.com/news/security/malicious-ai-models-on-hugging-face-backdoor-users-machines/);
3. Se atente também nas licenças de conteúdo dos modelos e também possíveis dependências. Se atente a documentação presente em cada página dos modelos;
4. Alguns modelos de aprendizados de máquinas exigem bastantes recursos computacionais, ao escrever este post, várias vezes o Jupyter acabou resetando. Apenas para comparativo, este computador é um Core i5 de nona geração (Intel i5 - 9300H) e 8 GB de RAM. Infelizmente ainda não consegui ativar a GPU para tarefas de Machine Learning no Linux. No Google Colab é possível ativar o [suporte ao GPU](https://colab.research.google.com/notebooks/gpu.ipynb) mesmo no tier grátis.        


Alerta feitos, vamos aos modelos:


Primeiro é necessário a biblioteca [Transformers](https://huggingface.co/docs/transformers) para poder baixar e treinais os modelos pré-treinados. 


No momento da escrita deste post estão disponíveis 564772 modelos.


Aqui esta presente a [documentação](https://huggingface.co/docs/transformers/en/installation) de como instalar esta biblioteca.  




```python
import transformers
from transformers import pipeline


#Apenas para suprimir erros, não nescessário. 
import logging
logging.getLogger("transformers").setLevel(logging.ERROR)
```


## Tarefa 1 - preenchimento de máscaras


Para realizar a tarefa de **preenchimento de máscaras**, utilizaremos o modelo [BERTimbau Base (aka "bert-base-portuguese-cased"](https://huggingface.co/neuralmind/bert-base-portuguese-cased) [1] 




Iremos utilizar neste caso a versão base. 


A tarefa realizada será "fill-mask" e iremos pedir que ele devolva 5 respostas para a frase "Batatinha quando nasce, esparrama pelo [MASK]" onde [MASK] é o texto que será preenchido pelo token.


[1] SOUZA, Fábio e NOGUEIRA, Rodrigo e LOTUFO, **Roberto. BERTimbau: pretrained BERT models for Brazilian Portuguese.** 2020, [S.l: s.n.], 2020. 


A primeira linha do código abaixo indicar a tarefa a ser executada e o modelo a ser utilizado e a segunda linha aplica o modelo para o texto escolhido.




```python
mascarar = pipeline("fill-mask", model="neuralmind/bert-base-portuguese-cased")
texto = mascarar("Batatinha quando nasce, esparrama pelo [MASK]")
```




```python
for x in range(len(texto)):
  print(texto[x])
```


    {'score': 0.3925571143627167, 'token': 8105, 'token_str': 'chão', 'sequence': 'Batatinha quando nasce, esparrama pelo chão'}
    {'score': 0.10256581008434296, 'token': 1831, 'token_str': 'corpo', 'sequence': 'Batatinha quando nasce, esparrama pelo corpo'}
    {'score': 0.05736977979540825, 'token': 1147, 'token_str': 'mundo', 'sequence': 'Batatinha quando nasce, esparrama pelo mundo'}
    {'score': 0.047487251460552216, 'token': 388, 'token_str': 'ar', 'sequence': 'Batatinha quando nasce, esparrama pelo ar'}
    {'score': 0.023149045184254646, 'token': 9169, 'token_str': 'rosto', 'sequence': 'Batatinha quando nasce, esparrama pelo rosto'}




Observe nas resposta acima que o maior "score" foi para a frase que contém o token "chão".


## Tarefa 2 - Resumo de textos


Para realizar o processo de **resumo de texto** ("summarization"), iremos utilizar como exemplo o modelo [facebook/bart-large-cnn](https://huggingface.co/facebook/bart-large-cnn) [2] 


Utilizaremos o texto que está presente na própria página do modelo. 


[2] LEWIS, Mike e colab. **BART: Denoising sequence-to-sequence pre-training for natural language generation, translation, and comprehension.** CoRR, v. abs/1910.13461, 2019. Disponível em: <http://arxiv.org/abs/1910.13461>.




```python
resumir = pipeline("summarization", model="facebook/bart-large-cnn")
```




```python
texto = """The tower is 324 metres (1,063 ft) tall, about the same height as an 81-storey 
building, and the tallest structure in Paris. Its base is square, measuring 125 metres 
(410 ft) on each side. During its construction, the Eiffel Tower surpassed the Washington 
Monument to become the tallest man-made structure in the world, a title it held for 
41 years until the Chrysler Building in New York City was finished in 1930. 
It was the first structure to reach a height of 300 metres. Due to the addition of a 
broadcasting aerial at the top of the tower in 1957, it is now taller than the Chrysler 
Building by 5.2 metres (17 ft). Excluding transmitters, the Eiffel Tower is the 
second tallest free-standing structure in France after the Millau Viaduct."""
```




```python
resumo = resumir(texto, max_length = 40, min_length = 10, do_sample=False )
```




```python
print(resumo)
```


    [{'summary_text': 'The tower is 324 metres (1,063 ft) tall, about the same height as an 81-storey building. Its base is square, measuring 125 metres (410 ft'}]




## Conclusão


Este post apresentou como testar modelos de aprendizado de máquinas utilizando a biblioteca Transformers do Hugging Face. 






