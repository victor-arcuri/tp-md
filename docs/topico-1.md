# Tópico 1

Veja também Rosen Seção 3.4, 3.5 (final) e 5.6 (final).

## Algoritmo de Divisão

**Teorema** *$\forall\ a,b \in \mathbb{Z}$, $\exists\ q,r  \in \mathbb{Z}$ tais que $a=q\cdot b+r$ com $0\leq r<b$. Aqui, $q$ é o quociente e $r$ é o resto.*

Uma prova formal deste fato bem conhecido pode ser obtida por indução em $|a|$.

- O comando `q , r = divmod(a, b)` em Python executará a operação correspondente.
- O comando `q = a // b` retornará o quociente, enquanto `r = a % b` retornará o resto. *ATENÇÃO:* o comando `q = a/b` sempre retornará um float, o que não é o que queremos neste contexto.

. . .

**Definição** Dizemos que $b$ divide $a$, ou que $b$ é um divisor de $a$, ou que $a$ é um múltiplo de $b$ se $\exists q \in \mathbb{Z}$ tal que $qb = a$. Notação: $b \mid a$.

Exemplos: $5 \mid 15; 6 \not\mid 15; 0 \mid 0; 1 \mid -1$

A seguinte expressão booleana em Python testa a divisibilidade: `(a%b==0)`. Se quiser empacotar em uma função, temos:

```python
def DIV(b,a):
	return (a % b == 0)
```

Mas na prática manter a expressão original é mais fácil.

*[1.1] Teste os exemplos usando Colab.*

**Propriedades**
$$
\begin{array}{ll}
i)\quad & c \mid b \wedge b \mid a ~\Rightarrow ~ c \mid a \\
ii)\quad & b \mid a \wedge b \mid a' ~\Rightarrow ~ b \mid a + a' \\
iii)\quad & b \mid 0 ~~\forall b \in \mathbb{Z} \\
iv)\quad & 1 \mid a ~~\forall a \in \mathbb{Z} \\
v) &0 \mid a \iff a=0 \\
\end{array}
$$
*[1.2] Teste estas propriedades usando Colab.*

O seguinte trecho computa todos os divisores de $121 = 11 \cdot 11$:

```python
>>> n=121
>>> D121=[d for d in range(1,n+1) if n%d == 0]
>>> D121
[1, 11, 121]
```

Observe que o resultado é uma lista, a estrutura de dados mais importante do Python, denotada com `[` e `]`.

*[1.3] Calcule `D48`, a lista de divisores de $48$, e para algum outro número $m < 200$.*

As funções `len(L)` e `sum(L)` computam o número de elementos e a soma dos elementos de uma lista, respectivamente, então podemos computar o número de divisores, $\sum_{d \mid n} 1$, e a soma de todos os divisores, $\sum_{d \mid n} d$.

```
>>> len(D121)
3
>>> sum(D121)
133
```

*[1.4] Calcule esses valores para $48$ e para $m$.*

*[1.5] Um número é perfeito se ele é igual à soma de seus divisores, excluindo ele mesmo. Então se $\sum_{d \mid n} d = 2n$. Escreva um programa para encontrar todos os números perfeitos menores que 1000.*

## Máximo Divisor Comum

**Definição** O máximo divisor comum de $a$ e $b$ é o maior número $d$ que é divisor de ambos $a$ e $b$.

*Notação:* $d=\mathsf{gcd}(a,b)$

**Definição** $a$ e $b$ são coprimos (ou primos entre si) se $\mathsf{gcd}(a,b)=1$.

**Teorema** A probabilidade de que $a$ e $b$ arbitrários sejam coprimos pode ser definida como
$$
\lim_{N\rightarrow\infty}\frac{|\{1\leq a,b \leq N \wedge \mathsf{gcd}(a,b)=1 \}|}{N^2} = \frac{6}{\pi^2}
$$

## Algoritmo de Euclides

**Teorema** Sejam $a,b\in\mathbb{Z}$ e $d=gcd(a,b)$. Então, $d \mid r$ tal que
$$a=q\cdot b+r\ \mathsf{com}\ 0\le r<b$$

. . .

O Algoritmo de Euclides encontrará tal $d$.

. . .

**Algoritmo** Para $a,b\in\mathbb{Z}$ tais que $a>b$,

- defina $r_0=a$,
- defina $r_1=b$,
- enquanto $r_k\neq0$
  - defina $r_k$ recursivamente como o resto de $r_{k-2}/r_{k-1}$, ou seja, $$r_{k-2}=q_{k-1} \cdot r_{k-1} + r_k\ \mathsf{com}\ 0\le r_k<r_{k-1}$$
- retorne $gcd(a,b)=r_{k-1}$

## Algoritmo de Euclides (exemplo)

**Exemplo** $a=1057$, $b=315$, $gcd(a,b)=\ ???$

$$\begin{array}{l|ccccc||ll}
& & & & & & & r_0=1057 \\
&r_{k-2} &=& q_{k-1} \cdot r_{k-1} &+& r_k & & r_1=315 \\ \hline
k=2&1057 &=& 3\cdot 315 &+& 112 & q_1=3 & r_2=112 \\
k=3& 315 &=& 2\cdot 112 &+& 91 & q_2=2 & r_3=91 \\
k=4& 112 &=& 1\cdot 91 &+& 21 & q_3=1 & r_4=21 \\
k=5& 91 &=& 4\cdot 21 &+& 7 & q_4=4 & r_5=7 \longleftarrow \\
k=6& 21 &=& 3\cdot 7 &+& 0 & q_5=3 & r_6=0
\end{array}$$

Quando $r_k  = 0$, o algoritmo termina e a resposta é $mdc(a,b) = r_{k-1} = r_5 = 7$.

O programa a seguir calcula o MDC:

```python
def gcd_euclid_iterative(a, b):
# Calcula o MDC usando o algoritmo de Euclides (versão iterativa)
while b != 0:
(a, b) = (b, a%b) # usa uma tupla dupla
return a
```

*[1.6] Modifique o programa para mostrar todos valores intermediários de $q$ e $r$. Use este programa modificado para verificar o exemplo, e para calcular o MDC entre sua matrícula e seu número de telefone.*

*[1.7] Execute o programa modificado em $a=4181;b=2584$, dois números consecutivos da sequência de Fibonacci. O que você vê a respeito de $q$ e $r$? Por que este é o pior caso para o algoritmo de Euclides?*



$\infty$