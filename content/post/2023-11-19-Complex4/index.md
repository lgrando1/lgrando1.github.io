---
title: Números Complexos - Pt. 4
author: ''
date: '2023-11-19'
slug: complex4
categories: []
tags: [ "Matemática", "números", "complexos", "aprendizagem", "Taylor"]
subtitle: 'Expansão de algumas séries de Taylor'
Summary: 'Expansão tanto algebricamente, quanto utilizando biblioteca Sympy no Python'
authors: []
lastmod: '2023-11-19T16:00:00-03:00'
featured: yes
image:
  caption: ''
  focal_point: ''
  preview_only: no
projects: []

---

## Desenvolvimentos dos componentes da Série de Taylor

Para expandir computacionalmente é possivel utilizar a função sympy.series. 

A documentação desta função do Sympy pode ser encontrada [aqui](https://docs.sympy.org/latest/modules/series/series.html#more-intuitive-series-expansion)

O código fonte deste Jupyter Notebook pode ser encontrado [aqui](https://github.com/lgrando1/Notas_Numeros_Complexos/blob/main/Aula21_Novembro_taylor.ipynb)


```python
# importando as funções nescessarias para a expansão das funções:
from sympy import Symbol, cos, series, E, sin, ln, cosh, sinh
z = Symbol('z')
```

## Series de Taylor

Utiliza-se a seguinte expressão para o desenvolvimento das expressões das séries de Taylor:

$f(z)=\sum_{k=0}^{\infty}(z-a)^k\frac{f^{k}(a)}{k!}$

Desenvolva as séries de Taylor para as funções a seguir nos pontos determinados:

### A) $f(z) = e^z$ para $a = 0$

Calculando as derivadas:

$f^0(z)=e^z \Rightarrow f^0(0) = 1$ 

$f^1(z)=e^z \Rightarrow f^1(0) = 1$

$f^2(z)=e^z \Rightarrow f^2(0) = 1$

$f^3(z)=e^z \Rightarrow f^3(0) = 1$

$f^4(z)=e^z \Rightarrow f^4(0) = 1$

Para k = 0

$(z-0)^0 \frac{f^0(0)}{0!} = 1$

Para k = 1

$(z-0)^1 \frac{f^1(0)}{1!} = z$

Para k = 2

$(z-0)^2 \frac{f^2(0)}{2!} = \frac{z^2}{2!}$

Para k = 3

$(z-0)^3 \frac{f^3(0)}{3!} = \frac{z^3}{3!}$

Para k = 4

$(z-0)^4 \frac{f^4(0)}{4!} = \frac{z^4}{4!}$

Então:

$f(z) = 1 + z + \frac{z^2}{2!} + \frac{z^3}{3!} + \frac{z^4}{4!}... $


```python
#Computacionalmente:

series(E**(z),z)
```




$\displaystyle 1 + z + \frac{z^{2}}{2} + \frac{z^{3}}{6} + \frac{z^{4}}{24} + \frac{z^{5}}{120} + O\left(z^{6}\right)$



### B) $f(z) = \cos(z)$ para $a = 0$

Calculando as derivadas:

$f^0(z)=\cos(z) \Rightarrow f^0(0) = 1$ 

$f^1(z)=-\sin(z) \Rightarrow f^1(0) = 0$

$f^2(z)=-\cos(z) \Rightarrow f^2(0) = -1$

$f^3(z)=\sin(z) \Rightarrow f^3(0) = 0$

$f^4(z)=\cos(z) \Rightarrow f^4(0) = 1$

Para k = 0

$(z-0)^0 \frac{f^0(0)}{0!} = 1$

Para k = 1

$(z-0)^1 \frac{f^1(0)}{1!} = 0$

Para k = 2

$(z-0)^2 \frac{f^2(0)}{2!} = -\frac{z^2}{2!}$

Para k = 3

$(z-0)^3 \frac{f^3(0)}{3!} = 0$

Para k = 4

$(z-0)^4 \frac{f^4(0)}{4!} = -\frac{z^4}{4!}$

Então:

$f(z) = 1 - \frac{z^2}{2!} + \frac{z^4}{4!} ... $


```python
#Computacionalmente:

series(cos(z),z)
```




$\displaystyle 1 - \frac{z^{2}}{2} + \frac{z^{4}}{24} + O\left(z^{6}\right)$



### C) $f(z) = \sin(z)$ para $a = 0$

Calculando as derivadas:

$f^0(z)=\sin(z) \Rightarrow f^0(0) = 0$ 

$f^1(z)=\cos(z) \Rightarrow f^1(0) = 1$

$f^2(z)=-\sin(z) \Rightarrow f^2(0) = 0$

$f^3(z)=-\cos(z) \Rightarrow f^3(0) = -1$

$f^4(z)=\sin(z) \Rightarrow f^4(0) = 0$

$f^5(z)=\cos(z) \Rightarrow f^5(0) = 1$

Para k = 0

$(z-0)^0 \frac{f^0(0)}{0!} = 0$

Para k = 1

$(z-0)^1 \frac{f^1(0)}{1!} = z$

Para k = 2

$(z-0)^2 \frac{f^2(0)}{2!} = 0$

Para k = 3

$(z-0)^3 \frac{f^3(0)}{3!} = -\frac{z^3}{3!}$

Para k = 4

$(z-0)^4 \frac{f^4(0)}{4!} = 0$

Para k = 5

$(z-0)^5 \frac{f^5(0)}{5!} = \frac{z^5}{5!}$

Então:

\box{$f(z) = z - \frac{z^3}{3!} + \frac{z^5}{5!} ... $


```python
#Computacionalmente:

series(sin(z),z)
```




$\displaystyle z - \frac{z^{3}}{6} + \frac{z^{5}}{120} + O\left(z^{6}\right)$



### D) $f(z) = \frac{1}{z}$ para $a = 1$

Calculando as derivadas:

$f^0(z)=\frac{1}{z} \Rightarrow f^0(1) = 1$ 

$f^1(z)=-\frac{1}{z^2} \Rightarrow f^1(1) = -1$

$f^2(z)=\frac{2}{z^3} \Rightarrow f^2(1) = 2!$

$f^3(z)=-\frac{3!}{z^4} \Rightarrow f^3(1) = -3!$

$f^4(z)=\frac{4!}{z^5} \Rightarrow f^4(1) = 4!$

Para k = 0

$(z-1)^0 \frac{1}{0!} = 1$

Para k = 1

$(z-1)^1 \frac{-1}{1!} = -(z-1)$

Para k = 2

$(z-1)^2 \frac{2!}{2!} = (z-1)^2$

Para k = 3

$(z-1)^3 \frac{3!}{3!} = -(z-1)^3$

Para k = 4

$(z-1)^4 \frac{4!}{4!} = (z-1)^4$

Então:
 
$f(z) = 1 -(z-1) + (z-1)^2 - (z-1)^3 + (z-1)^4 ... $


```python
#Computacionalmente:

series(1/z, z, 1)
```




$\displaystyle 2 + \left(z - 1\right)^{2} - \left(z - 1\right)^{3} + \left(z - 1\right)^{4} - \left(z - 1\right)^{5} - z + O\left(\left(z - 1\right)^{6}; z\rightarrow 1\right)$



### E) $f(z) = \ln(z)$ para $a = 1$

Calculando as derivadas:

$f^0(z)= \ln(z) \Rightarrow f^0(1) = 0 $

$f^1(z)=\frac{1}{z} \Rightarrow f^1(1) = 1$ 

$f^2(z)=-\frac{1}{z^2} \Rightarrow f^2(1) = -1$

$f^3(z)=\frac{2}{z^3} \Rightarrow f^3(1) = 2!$

$f^4(z)=-\frac{3!}{z^4} \Rightarrow f^4(1) = -3!$


Para k = 0

$(z-1)^0 \frac{0}{0!} = 0$

Para k = 1

$(z-1)^1 \frac{1}{1!} = (z-1)$

Para k = 2

$(z-1)^2 \frac{-1}{2!} = -\frac{(z-1)^2}{2}$

Para k = 3

$(z-1)^3 \frac{2!}{3!} = \frac{(z-1)^3}{3}$

Para k = 4

$(z-1)^4 \frac{3!}{4!} = -\frac{(z-1)^4}{4}$

Então:
 
$f(z) = (z-1) -\frac{(z-1)^2}{2} + \frac{(z-1)^3}{3} -\frac{(z-1)^4}{4} ... $


```python
#Computacionalmente:

series(ln(z),z, 1)
```




$\displaystyle -1 - \frac{\left(z - 1\right)^{2}}{2} + \frac{\left(z - 1\right)^{3}}{3} - \frac{\left(z - 1\right)^{4}}{4} + \frac{\left(z - 1\right)^{5}}{5} + z + O\left(\left(z - 1\right)^{6}; z\rightarrow 1\right)$



### F) $f(z) = \cosh(z)$ para $a = 0$

Calculando as derivadas:

$f^0(z)= \cosh(z) \Rightarrow f^0(0) = 1 $

$f^1(z)= \sinh(z) \Rightarrow f^1(0) = 0$ 

$f^2(z)= \cosh(z) \Rightarrow f^0(0) = 1 $

$f^3(z)= \sinh(z) \Rightarrow f^1(0) = 0$

$f^4(z)= \cosh(z) \Rightarrow f^0(0) = 1 $


Para k = 0

$(z-0)^0 \frac{1}{0!} = 1$

Para k = 1

$(z-0)^1 \frac{0}{1!} = 0$

Para k = 2

$(z-0)^2 \frac{1}{2!} = \frac{z^2}{2}$

Para k = 3

$(z-0)^3 \frac{0}{3!} = 0$

Para k = 4

$(z-0)^4 \frac{1}{4!} = \frac{z^2}{4!}$

Então:
 
$f(z) = 1 + \frac{z^2}{2} + \frac{z^4}{4!} ... $


```python
#Computacionalmente:

series(cosh(z),z)
```




$\displaystyle 1 + \frac{z^{2}}{2} + \frac{z^{4}}{24} + O\left(z^{6}\right)$



### G) $f(z) = \sinh(z)$ para $a = 0$

Calculando as derivadas:

$f^0(z)= \sinh(z) \Rightarrow f^1(0) = 0$ 

$f^1(z)= \cosh(z) \Rightarrow f^0(0) = 1 $

$f^2(z)= \sinh(z) \Rightarrow f^1(0) = 0$

$f^3(z)= \cosh(z) \Rightarrow f^0(0) = 1 $

$f^4(z)= \sinh(z) \Rightarrow f^0(0) = 0 $

$f^5(z)= \cosh(z) \Rightarrow f^0(0) = 1 $

Para k = 0

$(z-0)^0 \frac{0}{0!} = 0$

Para k = 1

$(z-0)^1 \frac{1}{1!} = z$

Para k = 2

$(z-0)^2 \frac{0}{2!} = 0$

Para k = 3

$(z-0)^3 \frac{1}{3!} = \frac{z^3}{3!}$

Para k = 4

$(z-0)^4 \frac{0}{4!} = 0$

Para k = 5

$(z-0)^5 \frac{1}{5!} = \frac{z^5}{5!}$

Então:
 
$f(z) = z + \frac{z^3}{3!} + \frac{z^5}{5!} ... $


```python
#Computacionalmente:

series(sinh(z),z)
```




$\displaystyle z + \frac{z^{3}}{6} + \frac{z^{5}}{120} + O\left(z^{6}\right)$



### H) $f(z) = \frac{1+2z}{z^3+z^4}$, para $a = 0$


```python
#Computacionalmente:

series((1+2*z)/(z**3+z**4),z)
```




$\displaystyle \frac{1}{z^{3}} + \frac{1}{z^{2}} - \frac{1}{z} + 1 - z + z^{2} - z^{3} + z^{4} - z^{5} + O\left(z^{6}\right)$



![Not-By-AI](notai.svg "https://notbyai.fyi/")
