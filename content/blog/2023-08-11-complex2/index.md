---

title: Números Complexos - Pt.2 
author: '' 
date: '2023-08-11' 
slug: complexex1 
categories: [] 
tags: [ "Matemática", "números", "complexos", "aprendizagem"] 
subtitle: 'Exercícios sobre Números Complexos' 
Summary: 'Exercícios operações básicas números complexos' 
authors: [] 
lastmod: '2023-09-09T16:00:00-03:00' 
featured: yes 
image:
  caption: ''
  focal_point: ''
  preview_only: no
projects: []

---

## Pt 2 - Forma Polar/Exponencial/Funções/Cauchy-Riemann

A Parte 1 deste série considera as operações com as coordenadas cartesianas;

1. Operações Básicas com Números Complexos
   1.1 - Utilizando o Python para efetuar os cálculos
2. Representação Polar/Exponencial 
   2.1 Multiplicação e divisão de números polares
   2.2 - Utilizando o Sympy
4. Raízes de z
5. Função complexa
6. Equações de Cauchy-Riemann

Código disponível aqui: https://github.com/lgrando1/Notas_Numeros_Complexos/

## 1. Operações Básicas com Números Complexos 

Considere os números complexos abaixo:

a = 2 + 3j

b = 1j

c = 4 + 1j

d = 5 - 2j

**Calcule:**

1a) a+b = 

1b) a+c = 

1c) d-a =

1d) b-d = 

1e) a * b =

1f) b * c = 

1g) a / c = 

1h) d / c = 

Calcule do valor absoluto (módulo) dos números complexos: 

1i) |a| =

1j) |b - d| = 

Calcule o conjugado dos números complexos:

1l) $\bar{c}$

1m) $\overline{c+b}$

### 1.1 - Utilizando o Python para efetuar os cálculos:


```python
# Definindo os números

a = 2 + 3j

b = 1j

c = 4 + 1j

d = 5 - 2j
```


```python
print("1a:", a+b) 
```

    1a: (2+4j)



```python
print("1b:",a+c) 
```

    1b: (6+4j)



```python
print("1c:",d-a)
```

    1c: (3-5j)



```python
print("1d:",b-d)
```

    1d: (-5+3j)



```python
print("1e:",a * b)
```

    1e: (-3+2j)



```python
print("1f:",b * c) 
```

    1f: (-1+4j)



```python
print("1g:",a / c) 
```

    1g: (0.6470588235294118+0.5882352941176471j)



```python
print("1h:",d / c) 
```

    1h: (1.0588235294117647-0.7647058823529411j)



```python
print("1i:",abs(a))
```

    1i: 3.605551275463989



```python
print("1j:",abs(b - d))
```

    1j: 5.830951894845301



```python
print("1l:",c.conjugate())
```

    1l: (4-1j)



```python
print("1m:",c.conjugate()+b.conjugate())
```

    1m: (4-2j)


OBS: Sugestões para gráficos em Python: https://python-graph-gallery.com/

**Função no Python para plotar um número utilizando a biblioteca Matplotlib**


```python
#importar as bibliotecas
import matplotlib.pyplot as plt
import numpy as np

#criando uma função para plotar

def plotargant(x):
    ponto = np.array(x)
    
    x = ponto.real
    y = ponto.imag

    fig, ax = plt.subplots(1, figsize=(6, 4))
    ax.scatter(x, y, s = 100, color = 'red')
    ax.quiver(0, 0, x,y, units='xy', angles='xy', scale=1)

    ax.spines['left'].set_position('zero')
    ax.spines['right'].set_color('none')
    ax.spines['bottom'].set_position('zero')
    ax.spines['top'].set_color('none')

    ax.set_ylabel('Im')
    ax.set_xlabel('Re')
    #ax.show()


```


```python
print("Gráfico ponto a")
plotargant(a)
```

    Gráfico ponto a



    
![png](./index_19_1.png)
    



```python
print("Gráfico 1l")
plotargant(c.conjugate())
```

    Gráfico 1l



    
![png](./index_20_1.png)
    


## 2. Representação Polar/Exponencial 

2. Converta os números a seguir em polar:

2a) a = 2 + 3j

2b) b = 1j

2c) c = 4 + 1j

2d) d = 5 - 2j

A fórmula de Euler:

$e^{j\theta} = \cos\theta + j\sin\theta$

Pode ser utilizada para representar um número complexo na fórmula polar:

$z = re^{j\theta} = r\cos\theta+jr\sin\theta = r(\cos\theta+j\sin\theta)$

Lembrando:
$|z| = r = \sqrt{x^2 + y^2} = \sqrt{z\bar{z}}$

O principal argumento do ângulo: $-\pi < \theta < \pi$. 

Outros valores possíveis para $\theta = \theta + 2n\pi$, onde $n = \pm 1, \pm 2, ...$ 

O número complexo $z = 1+1i$ pode ser representado das seguintes formas:

1. Forma cartesiana: $z = 1+1i$
2. Forma polar: $\sqrt{2}(\cos(\frac{\pi}{4}) + i \sin(\frac{\pi}{4}))$
3. Forma exponencial: $\sqrt{2}e^{i\pi/4}$


```python
#definindo os números nos Python:

a = 2 + 3j

b = 1j

c = 4 + 1j

d = 5 - 2j

```


```python
#importando a biblioteca cmath (para cálculos dos complexos)

import cmath

cmath.polar(a)
```




    (3.605551275463989, 0.982793723247329)




```python
cmath.polar(b)
```




    (1.0, 1.5707963267948966)



Neste caso (2a) o número 2 + 3j, pode ser representado como o valor 

aproximado de r = 3,60 e o argumento de 0,98 radianos ou melhor (56,3 graus). 

Utilizando a notação de Euler:

$a = 2+3j = 3.6e^{j0.98}=3.6(\cos{0.98}+j\sin{0.98})$

Comandos interessantes para o cmath:


```python
#Para calcular o modulo de a:

abs(a)
```




    3.605551275463989




```python
#para obter o valor do angulo Theta:

cmath.phase(a)
```




    0.982793723247329




```python
# Importar a biblioteca math (para calcular o arco tangente)

import math

#que é igual a:

math.atan(a.imag/a.real)
```




    0.982793723247329




```python
#convertendo para graus

round(math.degrees(cmath.phase(a)), 1)
```




    56.3




```python
# Realizando o caminho inverso 
# a forma polar para a forma algébrica
# r*(cos(theta) + i sen(theta) para
# (x+yj)

abs(a) * (math.cos(cmath.phase(a)) + math.sin(cmath.phase(a))*1j)

```




    (2+3j)




```python
# função para plotar o número 

def plotapolar(z):
    fig, ax = plt.subplots(subplot_kw={'projection': 'polar'}, figsize=(4, 4))
    ax.plot(cmath.phase(z), abs(z), marker='o', markersize=15, color='red')
    ax.quiver(0, 0, z.real, z.imag, scale=0.1)
    plt.show()
```


```python
plotapolar(a)
```


    
![png](./index_35_0.png)
    



```python
# 2b) b = 1j

print(cmath.polar(b))

plotapolar(b)
```

    (1.0, 1.5707963267948966)



    
![png](./index_36_1.png)
    



```python
# 2c) c = 4 + 1j

print(cmath.polar(c))

plotapolar(c)
```

    (4.123105625617661, 0.24497866312686414)



    
![png](./index_37_1.png)
    



```python
#2d) d = 5 - 2j

print(cmath.polar(d))

plotapolar(d)
```

    (5.385164807134504, -0.3805063771123649)



    
![png](./index_38_1.png)
    


### 2.1 Multiplicação e divisão de números polares

Sendo:

$z_1 = r_1(\cos\theta_1 + i\sin \theta_1)$

$z_2 = r_2(\cos\theta_2 + i\sin \theta_2)$

**Multiplicação para a forma polar:**

$z_1z_2= r_1r_2[\cos(\theta_1+\theta_2) + i \sin((\theta_1+\theta_2)]$

**Divisão para a forma polar**

$\frac{z_1}{z_2}= \frac{r_1}{r_2}[\cos(\theta_1-\theta_2) + i \sin((\theta_1-\theta_2)]$

Lembrando que:

$arg(z_1z_2) = arg z_1 + arg z_2$  e 

$arg(\frac{z_1}{z_2}) = arg z_1 -arg z_2$


Calcule a multiplicação e divisão utilizando a forma polar dos números

2d) a * b =

cmath.polar(a):
(3.605551275463989, 0.982793723247329)

cmath.polar(b)
(1.0, 1.5707963267948966)

$z_1z_2= r_1r_2[\cos(\theta_1+\theta_2) + i \sin(\theta_1+\theta_2)]$

$a*b= 3.6*1[\cos(0.982+1.571) + i \sin(0.982+1.571)]$


```python
cmath.polar(a*b)
```




    (3.605551275463989, 2.5535900500422257)




```python
plotapolar(a*b)
```


    
![png](./index_42_0.png)
    



```python
abs(a)*abs(b)*(math.cos(cmath.phase(a)+cmath.phase(b))+math.sin(cmath.phase(a)+cmath.phase(b))*1j)
```




    (-3+2j)



2e) b * c =

2f) a / c =

2g) d / c =

### 2.2 - Utilizando o Sympy

A biblioteca Sympy possibilita a manipulação simbólica. O termo da unidade imaginária nesta biblioteca é o "I":


```python
from sympy import I, re, im, Abs, arg, conjugate, solve, Symbol, deg
```


```python
#Utilizando a representação do Python padrão:
z1 = 2 + 3j
z1
```




    (2+3j)




```python
#Utilizando a representação do Sympy
z = 2 +3*I
z
```




$\displaystyle 2 + 3 i$




```python
#Para obter a parte real de z
re(z)
```




$\displaystyle 2$




```python
#Para obter a parte imaginária de z
im(z)
```




$\displaystyle 3$




```python
#Para obter o módulo de z
Abs(z)
```




$\displaystyle \sqrt{13}$




```python
#Para obter o conjugado de z
conjugate(z)
```




$\displaystyle 2 - 3 i$




```python
#Para encontrar o argumento do complexo
arg(z)
```




$\displaystyle \operatorname{atan}{\left(\frac{3}{2} \right)}$




```python
#Para encontrar o valor do argumento em radianos
arg(z).n()
```




$\displaystyle 0.982793723247329$




```python
#Para encontrar o valor em graus:

deg(arg(z)).n(4)
```




$\displaystyle 56.31$




```python
# Representando a formula de Euler
# Realizando a importação necessarias:

from sympy import exp, sin, cos, symbols

# Para que o Sympy o theta

r, theta = symbols(r"r, \theta", real = True)

r*exp(I * theta)
```




$\displaystyle r e^{i \theta}$



Sympy possui os métodos "expand" e "simplify" para efetuar a manipulação algébricas de expressões:


```python
r*exp(I * theta).expand(complex=True)
```




$\displaystyle r \left(i \sin{\left(\theta \right)} + \cos{\left(\theta \right)}\right)$




```python
r*(cos(theta) + I * sin(theta)).simplify()
```




$\displaystyle r e^{i \theta}$




```python
from sympy import exp_polar, pi, I, exp, sqrt


```


```python
#Para obter a forma algebrica da forma exponencia:

from sympy import atan

expr = (r * exp(I * theta)).subs({r:sqrt(13), theta: atan('3/2')})
expr
```




$\displaystyle \sqrt{13} e^{i \operatorname{atan}{\left(\frac{3}{2} \right)}}$




```python
expr.as_real_imag()
```




    (2, 3)




```python
plotapolar(2+3j)
```


    
![png](./index_63_0.png)
    


## 3. Raízes de z

**Fórmula de De Moivre**

Se $n$ é um inteiro:

$z^n = [r(\cos\theta + i\sin\theta)]^n = r^n(\cos n \theta + i\sin n \theta)]$

Se $z = w^n$ e $w = \sqrt[n]{z}$

$\sqrt[n]{z} = \sqrt[n]{r}$

$\sqrt[n]{z} = \sqrt[n]{r}(\cos \frac{\theta + 2k \pi}{n} + i\sin \frac{\theta + 2k \pi}{n})$

n valores dentro de um circulo de raio $\sqrt[n]{r}$ com centro na origem. Poligono regular de $n$ lados. 

O valor principal de $w$ é quando $k=0$  

Se $z = 1$, temos $r = 1$ e $\theta = 0$, resultando nas $n$ raizes da unidade

$\sqrt[n]{1} = (\cos \frac{2k \pi}{n} + i\sin \frac{2k \pi}{n})$



3.1 - Encontre as raízes quadradas de 4i:

$4i = 4e^{i\frac{\pi}{2}}$

Desta forma:

r = 4, $\theta = \frac{\pi}{2}$ e n = 2

$\sqrt[2]{4e^{i\frac{\pi}{2}}} = \sqrt[2]{4}(\cos \frac{\frac{\pi}{2} + 2k \pi}{2} + i\sin \frac{\frac{\pi}{2} + 2k \pi}{2})$, k = 0,1

Para k = 0

$2* \cos(\frac{\pi}{4}) + i\sin(\frac{\pi}{4})$ 





```python
a = 2*(math.cos(pi/4)+math.sin(pi/4)*I)

abs(a) * (math.cos(cmath.phase(a)) + math.sin(cmath.phase(a))*1j)
```




$\displaystyle 1.4142135623731 + 1.41421356237309 i$



Para k = 1

$2* \cos(\frac{\pi}{4}+\pi) + i\sin(\frac{\pi}{4}+\pi)$ 


```python
a = 2*(math.cos(5*pi/4)+math.sin(5*pi/4)*I)
a
```




$\displaystyle -1.4142135623731 - 1.41421356237309 i$



As raizes são:

$= \pm (\sqrt(2) + i\sqrt(2))$


```python
#A primeira raiz pode ser obtida pelo 
sqrt(4*I).expand(complex = True)
```




$\displaystyle \sqrt{2} + \sqrt{2} i$




```python
(-27)**(1/3)
```




    (1.5000000000000004+2.598076211353316j)



3.2 - Encontre as raízes cúbicas de -27:

$-27 = 27e^{i \pi}$

Desta forma:

r = 27, $\theta = \pi$ e n = 3

$\sqrt[3]{27e^{i\pi}} = \sqrt[3]{27}(\cos \frac{\pi + 2k \pi}{3} + i\sin \frac{\pi + 2k \pi}{3})$, k = 0,1,2

Para k = 0

$3* \cos(\frac{\pi}{3}) + i\sin(\frac{\pi}{3})$ 


```python
3*cos(pi/3)+ I * sin(pi/3)
```




$\displaystyle \frac{3}{2} + \frac{\sqrt{3} i}{2}$



Para k = 1

$3(\cos {\pi} + i\sin {\pi})$


```python
3*cos(pi)+ I * sin(pi)
```




$\displaystyle -3$



Para k = 2

$3(\cos \frac{5\pi}{3} + i\sin \frac{5\pi}{3})$


```python
3*cos(5*pi/3)+ I * sin(5*pi/3)
```




$\displaystyle \frac{3}{2} - \frac{\sqrt{3} i}{2}$



3.3 - Determine $\sqrt[8]{\frac{i}{1-i}}$

$\frac{i}{i-1} = \frac{i(1+i)}{(1-i)(1+i)} = \frac{-1+i}{2} = \frac{ \sqrt 2}{2}(cos(\frac{3\pi}{4})+isin(\frac{3\pi}{4}))$

r = $\frac{1}{\sqrt{2}}$, $\theta = \frac{3\pi}{4}$, $n = 8$





{$\frac{2^{15/16}}{2} * (cos(\frac{3*\pi}{32}+\frac{k*\pi}{4})+ i* \sin(\frac{3*\pi}{32}+\frac{k*\pi}{4}), k = 0,1,2,...,7$}


```python
#Obtendo o valor numérico simplificado da primeira raiz:
(((-1+I)/2)**(1/8)).n(4)
```




$\displaystyle 0.9164 + 0.278 i$



## 4. Função complexa

Uma função complexa pode ser escrita da forma:

$f(z) = u(x,y) + iv(x,y)$

Onde:

$z = x+iy$ e $u$ e $v$ funções reais que dependem de duas variáveis $x$ e $y$

**Exemplo 1:**
$f(z) = z^2 = (x + iy)^2 = x^2-y^2 + i 2xy$

$u(x,y) = x^2-y^2$

$v(x,y) = 2xy$

Desta forma podemos calcular o valor de $z = 2 +2i$, sendo $x = 2$ e $y = 2$:

$u(x,y) = x^2-y^2 = 4-4 = 0$ 

$v(x,y) = 2xy = 8$

$f(2+2i) = u(2,2) + iv(2,3) = 8i$





```python
#Resolvendo com o Sympy:

import sympy
x, y, a, b, c = sympy.symbols('x y a b c')

#definindo a expressão:
expr = ((x+y*I)**2)

#Expandindo a expressão
expr.expand()
```




$\displaystyle x^{2} + 2 i x y - y^{2}$




```python
#Substituindo os valores de x, y = 2
expr.expand().subs([(x, 2), (y, 2)])
```




$\displaystyle 8 i$



**Exemplo 2:**
$f(z) = 2z^3 - 4z+1$, onde $z = x + iy$

$2(x+iy)^3-4(x+iy)+1$

$(2x^3-6xy^2-4x+1)+i(6x^2y-2y^3 -4y)$

$u(x,y) = 2x^3-6xy^2-4x+1$

$y(x,y) = 6x^2y-2y^3 -4y$



```python
expr2 = 2*(x+I*y)**3-4*(x+I*y)+1

expr2.expand()
```




$\displaystyle 2 x^{3} + 6 i x^{2} y - 6 x y^{2} - 4 x - 2 i y^{3} - 4 i y + 1$



**Exemplo 3:** 
$f(z) = cos(z)$


```python
expr3 = cos(x+y*I)

expr3
```




$\displaystyle \cos{\left(x + i y \right)}$




```python
from sympy import expand_trig

expand_trig(expr3)
```




$\displaystyle - i \sin{\left(x \right)} \sinh{\left(y \right)} + \cos{\left(x \right)} \cosh{\left(y \right)}$



**Exemplo 4 - $f(z) = \sqrt z  = \sqrt{x+iy}$**

Utilizando a fórmula de De Moivre para expandir a função:

Se $z = w^n$ e $w = \sqrt[n]{z}$

$\sqrt[n]{z} = \sqrt[n]{r}(\cos \frac{\theta + 2k \pi}{n} + i\sin \frac{\theta + 2k \pi}{n})$

$n = 2, \theta = arg(x+iy), r = \sqrt{x^2+y^2}$

$\sqrt[2]{x+yi} = \sqrt[4]{x^2+y^2}(\cos \frac{arg(x+iy)}{2} + i\sin \frac{arg(x+iy)}{2})$





## 5 - Equações de Cauchy-Riemann

Critério para que uma função seja derivável, em relação a $z=x+jy$

$\frac{\partial u}{\partial x} = \frac{\partial v}{\partial y}$

$\frac{\partial u}{\partial y} = -\frac{\partial v}{\partial x}$


**Exemplo**

Verificar se $f(z) = 2z^3 - 4z+1$, onde $z = x + iy$ é derivável utilizando as Equações de Cauchy-Riemann:

Encontrar u(x,y) e v(x,y): 

$2(x+iy)^3-4(x+iy)+1$

$(2x^3-6xy^2-4x+1)+i(6x^2y-2y^3 -4y)$

$u(x,y) = 2x^3-6xy^2-4x+1$

$y(x,y) = 6x^2y-2y^3 -4y$

Utilizado o Sympy para efetuar as derivadas:


```python
# Importar o módulo de derivadas
from sympy import diff

#inserindo as funções
u = 2*x**3 - 6*x*y**2-4*x+1
v = 6*y*x**2-2*y**3-4*y
```


```python
#imprimindo u
u
```




$\displaystyle 2 x^{3} - 6 x y^{2} - 4 x + 1$




```python
#imprimindo v
v
```




$\displaystyle 6 x^{2} y - 2 y^{3} - 4 y$




```python
#Derivando a função u, em relação à variável x

# A documentação do Sympy se encontra aqui: https://docs.sympy.org/latest/index.html

diff(u,x)
```




$\displaystyle 6 x^{2} - 6 y^{2} - 4$



Verificando as equações de Cauchy-Riemann:

$\frac{\partial u}{\partial x} = \frac{\partial v}{\partial y}$


```python
diff(u,x) == diff(v,y)
```




    True



$\frac{\partial u}{\partial y} = -\frac{\partial v}{\partial x}$


```python
diff(u,y) == -diff(v,x)
```




    True



$f(z)$ é derivável.

## Referências Bibliográficas

**CMATH — MATHEMATICAL FUNCTIONS FOR COMPLEX NUMBERS.** 2023. Python documentation. Disponível em: https://docs.python.org/3/library/cmath.html. Acesso em: 19 ago. 2023.


MEURER, Aaron; SMITH, Christopher P.; PAPROCKI, Mateusz; ČERTÍK, Ondřej; KIRPICHEV, Sergey B.; ROCKLIN, Matthew; KUMAR, AMiT; IVANOV, Sergiu; MOORE, Jason K.; SINGH, Sartaj; RATHNAYAKE, Thilina; VIG, Sean; GRANGER, Brian E.; MULLER, Richard P.; BONAZZI, Francesco; GUPTA, Harsh; VATS, Shivam; JOHANSSON, Fredrik; PEDREGOSA, Fabian; … SCOPATZ, Anthony. **SymPy: symbolic computing in Python**. PeerJ Computer Science, v. 3, p. e103, 2 jan. 2017. https://doi.org/10.7717/peerj-cs.103.

LUCIO S. BUSTAMANTE, F. **Números complexos com Python e SymPy**. Disponível em: <https://cienciaprogramada.com.br/2022/03/numeros-complexos-python-sympy/>. Acesso em: 1 ago. 2023.

PETRA, B.-T. **Introdução à análise complexa**. Disponível em: <https://www.coursera.org/learn/complex-analysis>. Acesso em: 8 Mai. 2023.

URSINI, Edson L. **Notas de Aulas TT413 - Métodos Matemáticos para Telecomunicacões.** [S. l.: s. n.], 2023.‌


![Not-By-AI](notai.svg "https://notbyai.fyi/")
