# Tópico 2: Números primos

**Definição** $n$ é primo se tiver apenas dois divisores, a saber, $1$ e ele mesmo.

*[2.1] Escreva um teste em Python para verificar se $n$ é primo.*

**Teorema** Existem infinitos primos.

**Demonstração (Euclides)** Considere $n=(2\cdot 3\cdot 5\cdot \ldots\cdot p_{max})+1$. Certamente $n>p_{max}$ e $p_i\not\mid\n$ para todo $i$ (já que $p_i \mid n-1$). Portanto, ou $n$ é primo, ou o produto de primos maiores que $p_{max}$.

### Fatos sobre números primos

**Definição** Um primo de Mersenne é um primo da forma $M_k=2^k-1$

$$\begin{array}{c|ccccccccc}
k & 2 & 3 & 5 & 7 & 13 & 17 & 19 & 31 & \ldots \\ \hline
2^k & 4 & 8 & 32 & 128 & 8192 & 131072 & 524288 & 2147483648 & \ldots \\
M_k & 3 & 7 & 31 & 127 & 8191 & 131071 & 524287 & 2147483647 & \ldots
\end{array}$$

Existe uma competição mundial para encontrar o maior primo; sempre da forma $M_k=2^k-1$. São mais simples de encontrar porque: $M_k\ \mathsf{primo} \stackrel{\not\Leftarrow}{\Rightarrow}k\ \mathsf{primo}$. Caso contrário, os primos de Mersenne não têm importância prática.

*[2.2] Encontre na internet qual é o maior número primo conhecido no momento. É um primo de Mersenne?*

**Definição** Um primo de Fermat é um primo da forma $F_k = 2^{2^k}+1$

$$\begin{array}{c|cccccc}
k & 1 & 2 & 3 & 4 & 5 & \ldots \\ \hline
2^k & 2 & 4 & 8 & 16 & 32 & \ldots \\
F_k & 5 & 17 & 257 & 65537 & 4294967297 & \ldots
\end{array}$$

- Fermat observou que $F_1,F_2,F_3,F_4$ são primos e conjecturou que todos os outros eram primos.

- De fato, nenhum primo de Fermat $F_k$ foi encontrado para $k>4$.

- Os primos de Fermat são usados em criptografia devido à sua representação binária simples.

*[2.3] Qual é a representação binária de $257$ e de $65537$? Você consegue encontrar um comando em Python que faça isso para você?*

## Quantos números primos existem?

**Definição** A função $\pi(x)$ conta todos os números primos até $x$.

$$\pi(x) = | \{ 1<p\leq x : p \ \mathsf{é\ primo}\}|$$

**Exemplos** $\pi(10)=|\{2,3,5,7\}|= 4$

A expressão $\pi(x)/x$ representa a densidade de primos entre todos os inteiros.

**Teorema dos Números Primos**
$$\lim_{N\rightarrow\infty}\frac{\pi(N)}{N}\sim\frac{1}{\ln(N)}$$

A demonstração deste teorema é muito difícil.

![](PrimeNumberTheorem.png)

*[2.4] Use este teorema para estimar quantos números primos existem com tamanhos de 1024 bits, 1536 bits e 2048 bits* (os tamanhos usados na criptografia)

**Teorema de Fermat** Se $p$ é primo, então $a^{p-1}\equiv 1 \pmod{p}$ para todo $a \in [1,p-1]$.

Exemplo: $2^{10} = 1024 = 93 \cdot 11 + 1\equiv 1 \pmod{11}$

```python
>>> pow(2,10)
1024
>>> pow(2,10,11)
1
```

*[2.5] Use Python para testar o Teorema de Fermat para outros valores de $a$ e $p$.*

O inverso do teorema de Fermat pode ser usado como um teste de primalidade, pois se $n$ não satisfaz a equação para algum $a$, então não pode ser primo.

**Contra-positivo** Se $a^{n-1}\not\equiv 1 \pmod{n}$ para algum $a \in [1,n-1]$, então $n$ é composto.



**Teste de primalidade de Fermat** Para $n,k\in\mathbb{N}$,

- repita $k=10$ vezes:
- escolha aleatoriamente $a \in [2,n-2]$
- defina $b\equiv a^{n-1} \pmod{n}$
- se $b \neq 1$ retorne **composto** (com testemunha $a$)
- retorne **(provavelmente) primo**

O teste de primalidade de Fermat não fornece certeza absoluta sobre $n$ ser primo ou não, pois alguns números são imunes a esse teste.

**Definição** Um número de Carmichael é um composto $n$ tal que ${a^{n-1}\equiv 1\pmod{n}}$ para todo $a \in [2,n-1]$.

**Exemplo** $561 = 3\cdot 11\cdot 17$, ou $41041 = 7\cdot 11\cdot 13$

Mas os números de Carmichael são raros. Até 10000 são apenas 7, a saber $561, 1105, 1729, 2465, 2821, 6601, 8911$. A probabilidade de por acaso testar um número de Carmichael é muito pequena, então não nos preocuparemos com eles.

Isso nos leva ao seguinte programa para primalidade, que você pode usar na próxima questão.

```python
import random

def fermat_primality_test(n, k=10):
		"""
		Teste de primalidade de Fermat para verificar se n é provavelmente primo.

		Argumentos:
				n (int): O número a ser testado.
				k (int): O número de testes aleatórios a serem realizados (padrão=10).

		Retorna:
				bool: Verdadeiro se n passar em todos os testes (provavelmente primo), Falso se composto.
"""
		if n <= 1:
				return False
		elif n <= 3:
				return True # 2 e 3 são primos
		elif n % 2 == 0:
				return False # Números pares >2 são compostos

		for _ in range(k):
				a = random.randint(2, n - 2) # Escolha um valor aleatório a onde 1 < a < n-1
				if pow(a, n - 1, n) != 1: # Calcula a^(n-1) mod n eficientemente
						return False # Definitivamente composto
				return True # Provavelmente primo
```

*[2.6] Construa um número primo com seu nome*

1. Crie uma frase com cerca de 45 letras, incluindo seu nome. Cada aluno de uma dupla/tripla deve fazer isso.
2. Converta para um número como segue: $A=01, ..., Z=26, \mathsf{space}=27$ etc. Concatenando os dígitos, você obterá um número com cerca de 90 dígitos.
3. Adicione 10 dígitos aleatórios no final para obter um número ímpar de 100 dígitos $n$ e teste se $n$ é um número primo. Caso contrário, altere os últimos 10 dígitos até que $n$ seja primo.
4. Você pode usar `fermat_primality_test(n, k=10)`.

