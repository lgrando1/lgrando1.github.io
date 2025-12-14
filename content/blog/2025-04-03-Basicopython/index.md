---
title: "Lógica de Programação em Python - Introdução Passo a Passo"
author: ""
date: "2025-03-04"
slug: "logica-programacao-python-parte-1"
categories: ["Programação", "Python", "Algoritmos"]
tags: ["Python", "Lógica de Programação", "Algoritmos", "Introdução ao Python", "Variáveis", "Operações Matemáticas", "Strings"]
subtitle: "Aprenda Operações Básicas no Python"
summary: "Guia introdutório sobre lógica de programação em Python, abordando operações matemáticas, manipulação de strings e variáveis para iniciantes."
authors: []
lastmod: "2025-03-04T16:00:00-03:00"
featured: yes
image:
  caption: "Fundamentos de Programação em Python"
  focal_point: "center"
  preview_only: no
projects: []

---

# Operações básicas com Python

## Operações matemáticas

Soma (+)


```python
10+2
```




    12



Subtração (-)


```python
10-2
```




    8



Multiplicação (*)


```python
10*2
```




    20



Divisão (/)


```python
10/2
```




    5.0



Divisão inteira (//)


```python
13//2
```




    6



Módulo (%)


```python
13%2
```




    1



Exponenciação (**)


```python
13**2
```




    169



A precedência dos operadores matemáticos no Python é similar à matemática:

1 - operador **

2 - operadores *, /, // e % da esquerda para a direita

3 - operadores + e - da esquerda para a direita

Pode-se utilizar parênteses para proceder a precedência normal


```python
(5 - 3) * ((9-3)/4-8)**3
```




    -549.25



### Exercícios

Encontre o erro:

a)


```python
5 - 3 - * 4
```


      Cell In[41], line 1
        5 - 3 - * 4
                ^
    SyntaxError: invalid syntax



b)


```python
4  -
```


      Cell In[42], line 1
        4  -
            ^
    SyntaxError: invalid syntax



## Tipos de dados

- float: números de pontos flutuantes
- int: números inteiros
- str: string (valores textuais). Necessario inserir o texto entre aspas simples ou dupla

Float


```python
type(3.14)
```




    float



Inteiros


```python
type(3)
```




    int



String, com aspas duplas


```python
type("Léo")
```




    str



String, com aspas simples


```python
type('Léo')
```




    str



Possível erro de EOL, ao esquecer a aspa final:


```python
'Léo
```


      Cell In[47], line 1
        'Léo
        ^
    SyntaxError: unterminated string literal (detected at line 1)



## Concatenação e repetição de string

Concatenação:


```python
"Prof" + "Léo"
```




    'ProfLéo'



Não é possível concatenar string com valores numéricos


```python
# Possível erro:
"minha idade é " + 40
```


    ---------------------------------------------------------------------------

    TypeError                                 Traceback (most recent call last)

    Cell In[49], line 2
          1 # Possível erro:
    ----> 2 "minha idade é " + 40


    TypeError: can only concatenate str (not "int") to str


Nescessário converter para string:


```python
"minha idade é " + "40"
```




    'minha idade é 40'



Não é possível multiplicar strings:


```python
"Prof" * "Léo"
```


    ---------------------------------------------------------------------------

    TypeError                                 Traceback (most recent call last)

    Cell In[51], line 1
    ----> 1 "Prof" * "Léo"


    TypeError: can't multiply sequence by non-int of type 'str'


Mas é possível repetir os strings ao multiplicar por um valor inteiro:


```python
"Prof Léo " * 5
```




    'Prof Léo Prof Léo Prof Léo Prof Léo Prof Léo '



No caso de um valor float ocorrerá um erro:


```python
"Prof Léo" * 5.0
```


    ---------------------------------------------------------------------------

    TypeError                                 Traceback (most recent call last)

    Cell In[53], line 1
    ----> 1 "Prof Léo" * 5.0


    TypeError: can't multiply sequence by non-int of type 'float'


## Atribuição de Varíaveis

O sinal de "=" é chamado de instrução de atribuição. Uma variável é como uma gaveta na memória do computador, onde podemos armazenar um único valor.

Regras para os nomes de variáveis:

1. Nome pode ser constituido somente de uma palavra
2. Somente letras, números e o caractere underscore (_) podem ser utilizados
3. O nome não pode começar com um número
4. A distinção entre letras maiusculas e minúsculas (case sensitive)

Sempre utilize o bom senso e a consístencia para escolher os nomes das varíaveis.

Exemplos de atribuições de variáveis:


```python
a = 12
b = 13

a + b
```




    25



Mais exemplos:


```python
colher = "açucar na "
jarra = "água"

colher + jarra
```




    'açucar na água'



A variável assume o valor atribuido:


```python
colher
```




    'açucar na '



Muito cuidado, pois o [Python não é tipado](https://www.dio.me/articles/linguagens-tipadas-e-nao-tipadas-qual-e-a-melhor-para-o-seu-projeto), ou seja, as variáveis aceitam qualquer tipo de dados, o que pode dificultar a manutenção de códigos extensos:


```python
colher = 2
colher
```




    2



Um exemplo de erro devido a operação não suportadas por tipos de dados:


```python
colher + jarra
```


    ---------------------------------------------------------------------------

    TypeError                                 Traceback (most recent call last)

    Cell In[58], line 1
    ----> 1 colher + jarra


    TypeError: unsupported operand type(s) for +: 'int' and 'str'


## Algumas funções úteis:

1. len(str) -> indica a quantidade de caracteres de um string


```python
nome = "Leonardo Grando"
len(nome)
```




    15



2. print() - Função que exibe na tela os valores solicitados:


```python
print(a)
print("Léo")
print(a+b)
print("Roda " * 10)
print("O valor de a é", a)
```

    12
    Léo
    25
    Roda Roda Roda Roda Roda Roda Roda Roda Roda Roda 
    O valor de a é 12


3. input() -> coleta o dados inserido pelo usuário e é avaliado como uma string 


```python
print("Qual é o seu nome?")
nome = input()
print("O seu nome é", nome)
```

    Qual é o seu nome?
    O seu nome é Leonardo


4. Funções para converter tipos de dados:

- str() - converte para valores na forma de str
- int() - converte str ou float para valores inteiros
- float() - converte str ou int para valores flutuantes

str()


```python
str(a)
```




    '12'






```python
str(2.24)
```




    '2.24'



int()


```python
int(2.37)
```




    2






```python
int("leo")
```


    ---------------------------------------------------------------------------

    ValueError                                Traceback (most recent call last)

    Cell In[71], line 1
    ----> 1 int("leo")


    ValueError: invalid literal for int() with base 10: 'leo'


float()


```python
float("leo")
```


    ---------------------------------------------------------------------------

    ValueError                                Traceback (most recent call last)

    Cell In[73], line 1
    ----> 1 float("leo")


    ValueError: could not convert string to float: 'leo'





```python
float(5)
```




    5.0



5. Para obter ajuda sobre alguma função:


```python
help(print)
```

    Help on built-in function print in module builtins:
    
    print(*args, sep=' ', end='\n', file=None, flush=False)
        Prints the values to a stream, or to sys.stdout by default.
    
        sep
          string inserted between values, default a space.
        end
          string appended after the last value, default a newline.
        file
          a file-like object (stream); defaults to the current sys.stdout.
        flush
          whether to forcibly flush the stream.
    


## Desafios:

1. Crie um programa que solicite o nome e a idade de uma pessoa e exiba essas informações em uma sentença.
2. Dê exemplos de nomes válidos e inválidos para variáveis de um programa Python.
3. Crie um programa que peça ao usuário dois números e exiba a soma dos valores no seguinte formato:
"A soma de X e Y é Z", onde X e Y são os números fornecidos e Z é o resultado da soma.

## Algumas referências recomendadas:

**Automate the Boring Stuff with Python.** Disponível em: <https://automatetheboringstuff.com/>. Acesso em: 4 mar. 2025.

**PEP 8 – Style Guide for Python Code | peps.python.org. Python Enhancement Proposals (PEPs).** Disponível em: <https://peps.python.org/pep-0008/>. Acesso em: 4 mar. 2025.

**PY4E - Python for Everybody.** Disponível em: <https://www.py4e.com/>. Acesso em: 4 mar. 2025.

