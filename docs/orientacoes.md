# Orientações Trabalho Prático

## Projeto

### Objetivo

O projeto é explorar e aprender alguns feitos básicos do teoria de números,  usando o ambiente Jupyter, uma extensão de Python, como calculadora.

O projeto tem 5 tópicos:

1. O algoritmo de Euclides para calcular o MDC.
2. Números primos; fazer um primo com seu nome
3. Adição modular; o teorema chinês dos restos
4. Multiplicação modular; calcular inversos
5. Criptografar uma mensagem usando o sistema de Elgamal.

Estes tópicos correspondem com as seções 3.4 a 3.7 do livro de Rosen, mas em ordem diferente.

### Instruções

- O projeto vale 10% da nota final.

- Você pode fazer duplas ou triplas; cada um precisa entregar uma cópia e listar o nome dos parceiros.

- Você deve usar o ambiente de programação Jupyter. É possível instalar Jupyter localmente, mas talvez mais fácil usar COLAB da Google Drive, opção Nova --> Mais opções --> Google Colaboratory

- O Jupyter guarda as informações num Notebook, que permite digitar observações entre os comandos. Este arquivo pode ser salvado num arquivo com extensão .ipynb ou .html.

- O trabalho têm 5 partes, mas você deve entregar um arquivo só, com todas as respostas.

 
## Manipulação de listas em Python

Este projeto é uma oportunidade de aprender listas em Python e programação funcional.

A estrutura de dados mais importante do Python é a lista, denotada com `[` e `]`.

```python
>>> L = [i for i in range(10)]

>>> L

[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
```

Python permite fazer uma operação numa lista inteira

```python
>>> Q = [i*i for i in L]

>>> Q

[0, 1, 4, 9, 16, 25, 36, 49, 64, 81]
```

Ainda, pode filtrar os resultados, dependendo de uma cláusula booleana no final

```python
>>> R = [i*i for i in L if (i%3 ==2)]

>>> R

[4, 25, 64]
```

Desta forma fica bem fácil listar todos os divisores de `n`

```python
>>> n=100

>>> [d for d in range(1,n+1) if (n % d==0)]

[1, 2, 4, 5, 10, 20, 25, 50, 100]

>>> n=121

>>> D121 = [(d,n//d) for d in range(1,n+1) if (n % d==0)]

>>> D121

[(1, 121), (11, 11), (121, 1)]
```

Calcule `D48`, a lista de divisores de $48$, e para algum outro número $m < 200$.

As funções `len(L)` e `sum(L)` computam o número de elementos e a soma dos elementos de uma lista, respectivamente, então podemos computar o número de divisores, $\sum_{d|n} 1$, e a soma de todos os divisores, $\sum_{d|n} d$.

```python
>>> len(D121)

3

>>> sum(D121)

133
```

Calcule esses valores para $48$ e para $m$.

Um número é perfeito se $\sum_{d|n} d = 2n$. Escreva um programa para encontrar todos os números perfeitos menores que 1000.

Você pode testar de um número é primo, contando quantos divisores tem:

```python
>>> n=97

>>> D97 = [d for d in range(1,n+1) if (n % d==0)]

>>> len(D97)

2

>>> len(D97)==2

True
```

Para testar se existe um divisor para $n$, é suficiente ir até $\sqrt{n}$.

```python
>>> import.math

>>> n = 1001

>>> round(math.sqrt(n)+1)

33

>>> [(d,n//d) for d in range(2,round(math.sqrt(n)+1)) if (n % d==0)]

[(7, 143), (11, 91), (13, 77)]

>>> n = 1009   # o menor primo > 1000

>>> [(d,n//d) for d in range(2,round(math.sqrt(n)+1)) if (n % d==0)]

[]
```