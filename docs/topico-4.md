# Grupo Multiplicativo Módulo $N$

### **Grupos cíclicos**

Um grupo finito é chamado de **cíclico** se puder ser gerado inteiramente por um único elemento, chamado de **gerador**. Isso significa que cada elemento do grupo pode ser expresso como aplicações repetidas da operação de grupo (adição ou multiplicação) no gerador.

**Definição**
Um grupo $(G, \circ)$ é **cíclico** se existe um elemento $g \in G$ (o gerador) tal que todos os elementos podem ser obtidos aplicando a operação de grupo repetidamente em $g$, onde:

- Para **grupos aditivos** (como $\mathbb{Z}_n$), isso significa a adição de $g$ consigo mesmo $n$ vezes $\underbrace{g + g + \dots + g}_{n \text{ vezes}} = n \cdot g$; ou seja, multiplicação.

- Para **grupos multiplicativos** (como $(\mathbb{Z}_n^*$), isso significa a adição de $g$ consigo mesmo $n$ vezes $\underbrace{g \cdot g \cdot \ldots \cdot g}_{n \text{ vezes}} = g^n$; ou seja, exponenciação.

##### **Exemplo: Grupo Aditivo $\mathbb{Z}_{35}^+$**

- **Elementos**: $\{0, 1, 2, \dots, 34\}$.
- **Operação**: Adição módulo 35.
- **Cíclico?** **Sim**, pois é gerada por $1$:
$$
1 + 1 + \dots + 1 \ (\text{35 vezes}) \equiv 0 \mod 35.
$$
Todo elemento $k \in \mathbb{Z}_{35}$ pode ser escrito como $k \cdot 1 \mod 35$.
- **Geradores**: Todos os números que são coprimos com 35 (ou seja, $\text{mdc}(k, 35) = 1$):
$$
\text{Geradores} = \{1, 2, 3, 4, 6, 8, 9, 11, 12, 13, 16, 17, 18, 19, 22, 23, 24, 26, 27, 29, 31, 32, 33, 34\}.
$$
Por exemplo:
- $2$ é um gerador porque seus múltiplos abrangem todos os elementos: $2, 4, 6, \cdots, 34, 1, 3, 5, \cdots$.
- $5$ **não** é um gerador porque $\text{mdc}(5, 35) = 5 \neq 1$, e gera apenas $\{0, 5, 10, 15, 20, 25, 30\}$.



*[4.1] Use Python para encontrar todos os geradores de $\mathbb{Z}_{36}^+$ e de $\mathbb{Z}_{37}^+$.*

A **função phi de Euler** (ou **função totiente de Euler**), denotada como **φ(n)**, conta o número de inteiros até **n** que são **coprimos com n** (ou seja, inteiros $1 \leq a \leq n$ com $\text{mdc}(a, n) = 1$).

**Fórmula**
Para um inteiro positivo $n$ com fatoração em primos:
$$
n = p_1^{k_1} p_2^{k_2} \cdots p_m^{k_m},
$$

A função totiente é:

$$
\varphi(n) = n \prod_{p \mid n} \left(1 - \frac{1}{p}\right).
$$

**Exemplos**
- $\varphi(10) = 4$ (coprimos: 1, 3, 7, 9).
- $\varphi(7) = 6$ (todos os números de 1 a 6, já que 7 é primo).

*[4.2] Calcule os valores de $\varphi(35),\varphi(36),\varphi(37)$ e compare com os resultados obtidos acima.*

A função phi de Euler possui muitas propriedades interessantes, incluindo:

1. **Multiplicativa**: Se $\text{mdc}(a, b) = 1$, então $\varphi(ab) = \varphi(a)\varphi(b)$.
2. **Teorema de Euler**: Se $\text{mdc}(a, n) = 1$, então $a^{\varphi(n)} \equiv 1 \mod n$.



### Grupos multiplicativos

Para multiplicação, o elemento neutro é sempre $1$, e a definição de um grupo requer que cada elemento tenha um inverso. É por isso que, módulo $N$, precisamos nos restringir aos elementos $a$ que são coprimos com $N$, pois, caso contrário, $a^{-1}$ não existe.

*[4.3] Mostre que $5$ módulo $35$ não tem inverso multiplicativo.*

**Definição**
O **grupo multiplicativo módulo $N$**, denotado como $(\mathbb{Z}/N\mathbb{Z})^*$ ou $\mathbb{Z}_N^*$, consiste em todos os inteiros entre $1$ e $N-1$ que são **coprimos com $N$** (ou seja, $\text{mdc}(a, N) = 1$).

Este é um grupo sob multiplicação módulo $N$ e possui as seguintes propriedades:

1. **Fechamento**: Se $a, b \in \mathbb{Z}_N^*$, então $a \times b \mod N \in \mathbb{Z}_N^*$.
2. **Associatividade**: $(a \times b) \times c \equiv a \times (b \times c) \mod N$.
3. **Elemento neutro**: O número $1$ é a identidade multiplicativa/elemento neutro.
4. **Inversos**: Todo elemento $a$ possui um único inverso $a^{-1}$ tal que $a \times a^{-1} \equiv 1 \mod N$.
5. **Abeliano**: $a \times b \equiv b \times a \mod N$.
6. **Ordem**: O **tamanho** do grupo é dado pela função totiente de Euler $\phi(N)$.

##### Exemplo 1. Módulo $15$ ($\mathbb{Z}_{15}^*$)

O grupo multiplicativo $\mathbb{Z}_{15}^*$ consiste em inteiros módulo 15 que são coprimos com 15 (ou seja, elementos invertíveis sob multiplicação).

$$
\mathbb{Z}_{15}^* = \{1, 2, 4, 7, 8, 11, 13, 14\}
$$
Confirma-se: $|\mathbb{Z}_{15}^*|=\varphi(15) = (5-1)(3-1)= 4 \cdot 2 = 8$.

Eis a tabela de multiplicação do grupo $\mathbb{Z}_{15}^*$:
$$
\begin{array}{c|cccccccc}
\times \ (\text{mod } 15) & 1 & 2 & 4 & 7 & 8 & 11 & 13 & 14 \\
\hline
1 & 1 & 2 & 4 & 7 & 8 & 11 & 13 & 14 \\
2 & 2 & 4 & 8 & 14 & 1 & 7 & 11 & 13 \\
4 & 4 & 8 & 1 & 13 & 2 & 14 & 7 & 11 \\
7 & 7 & 14 & 13 & 4 & 11 & 2 & 1 & 8 \\
8 & 8 & 1 & 2 & 11 & 4 & 13 & 14 & 7 \\
11 & 11 & 7 & 14 & 2 & 13 & 1 & 8 & 4 \\
13 & 13 & 11 & 7 & 1 & 14 & 8 & 4 & 2 \\
14 & 14 & 13 & 11 & 8 & 7 & 4 & 2 & 1 \\
\end{array}
$$

**Observações Principais:**
1. **Elemento Identidade**: $1$ (já que $a \cdot 1 \equiv a \mod 15$).
2. **Inversos**:
- $1^{-1} = 1$
- $2^{-1} = 8$ (já que $2 \cdot 8 = 16 \equiv 1 \mod 15$)
- $4^{-1} = 4$
- $7^{-1} = 13$
- $14^{-1} = 14$ (autoinverso).
3. **Ordem dos Elementos**:
- $2$ tem ordem 4 ($2^4 = 16 \equiv 1 \mod 15$).
- $4$ tem ordem 2.
- $7, 13, 14$ têm ordem 2.
- $8, 11$ têm ordem 4.

**Estrutura do Grupo:**

Na Aula 3 vimos que $\mathbb{Z}_3 \times \mathbb{Z}_5 = \{(g,h) \mid 0 \leq g < 3 \wedge 0 \leq h < 5 \}$. Da mesma form temos que $\mathbb{Z}_3^* \times \mathbb{Z}_5^*$ é equivalente (exceto pela notação) a $\mathbb{Z}_{15}^*$:

$$
\mathbb{Z}_3^* \times \mathbb{Z}_5^* = \mathbb{Z}_{15}^*
$$

$$
\begin{array}{c|ccccc}
&0&1&2&3&4\\ \hline
0&-&-&-&-&- \\
1&-&1=(1,1)&7=(1,2)&13=(1,3)&4=(1,4) \\
2&-&11=(2,1)&2=(2,2)&8=(2,3)&14=(2,4) \\
\end{array}
$$

Esta tabela deixa claro que os inteiros $a$ tais que $\text{mdc}(a,15)=1$ não têm inverso.

##### Exemplo 2. Módulo $35$ ($\mathbb{Z}_{35}^*$)

- **Etapa 1: Fatorar $N$**
$35 = 5 \cdot 7$ (produto de dois primos distintos).

- **Etapa 2: Calcular $\phi(35)$**
Função totiente de Euler:
$
\phi(35) = \phi(5) \times \phi(7) = 4 \times 6 = 24.
$
Portanto, $\mathbb{Z}_{35}^*$ tem **24 elementos**.

- **Etapa 3: Listar os elementos coprimos de 35**
Todos os inteiros $1 \leq a < 35$ onde $\text{mdc}(a, 35) = 1$:
$
\mathbb{Z}_{35}^* = \{1, 2, 3, 4, 6, 8, 9, 11, 12, 13, 16, 17, 18, 19, 22, 23, 24, 26, 27, 29, 31, 32, 33, 34\}.
$

- **Etapa 4: Verificar os inversos**
Cada elemento tem um inverso único módulo 35. Por exemplo:
- $2^{-1} \mod 35 = 18$ (já que $2 \times 18 = 36 \equiv 1 \mod 35$).
- $6^{-1} \mod 35 = 6$ (já que $6 \cdot 6 = 36 \equiv 1 \mod 35$).

*[4.4] -- Determine o inverso de 22 e de 23 em* $\mathbb{Z}_{35}^*$.

##### Exemplo 3. Módulo $143$ ($\mathbb{Z}_{143}^*$)

- **Etapa 1: Fatorar $N$**
$143 = 11 \cdot 13$.

- **Etapa 2: Calcular $\phi(143)$**
$
\phi(143) = \phi(11) \cdot \phi(13) = 10 \cdot 12 = 120.
$
Portanto, $\mathbb{Z}_{143}^*$ tem **120 elementos**.

- **Etapa 3: Listar os Elementos (Parcialmente)**
Elementos coprimos com 143 (muitos para listar completamente, mas exemplos incluem):
$
\mathbb{Z}_{143}^* = \{1, 2, 3, \dots, 142\} \setminus \{11, 13, 22, 26, \dots, 130, 143\}.
$
(Exclui múltiplos de 11 ou 13.)

- **Etapa 4: Verificar Inversos**
- $2^{-1} \mod 143 = 72$ (já que $2 \cdot 72 = 144 \equiv 1 \mod 143$).
- $7^{-1} \mod 143 = 41$ (já que $7 \cdot 41 = 287 \equiv 1 \mod 143$).

*[4.5] Liste todos os elementos de* $\mathbb{Z}_{24}^*$ *e faça a uma tabela de multiplicação deste grupo.*

*[4.6] Calcule $5^{-1} \mod 143$.*

# Como Calcular Inversos Modulares Usando o Algoritmo Euclidiano Estendido

Calcular o inverso multiplicativo por tentativa e erro consome muito tempo para $N$ grandes. Felizmente, existe um algoritmo eficiente: calcular inversos é um caso particular do Algoritmo Euclidiano Estendido.

#### **Teorema**
Sejam dois inteiros $a$ e $b$ (ambos não nulos), e seja  $d=\text{mdc}(a, b)$ o máximo divisor comum de $a$ e $b$. Então existem inteiros $x$ e $y$ tais que:
$$
a x + b y = d
$$

Este teorema também é conhecido como Teorema de Bézout, e $x$ e $y$ são às vezes chamados de **coeficientes de Bézout**. Esses valores são calculados por uma versão estendida do algoritmo de Euclides.

Observações:

1. O $\text{mdc}$ de $a$ e $b$ pode sempre ser expresso como uma combinação linear inteira de $a$ e $b$.

2. A equação $a x + b y = c$ tem soluções inteiras $(x, y)$ **se e somente se** $\text{mdc}(a, b)$ divide $c$.
3. Os coeficientes $x$ e $y$ não são únicos (existem infinitas soluções).

**Exemplo** Considere o algoritmo normal apresentado na Aula 1 para $a=1057, b=315, \text{mdc}(a,b)=???$

Defina $a=r_0=1057; b=r_1=315$
$$
\begin{array}{ccccc|ll}
1057 &=& 3 \cdot 315 &+& 112 & q_1=3&r_2=113 \\
315 &=& 2 \cdot 112 &+& 91 & q_2=2&r_3=91 \\
112 &=& 1 \cdot 91 &+& 21 & q_3=1&r_4=21 \\
91 &=& 4 \cdot 21 &+& 7 & q_4=4&r_5=7 \\
21 &=& 3 \cdot 7 &+& 0 & q_5=3&r_6=0 \leftarrow \\
\end{array}
$$
Se $r_k=0$ então $r_{k-1}=\text{mdc}=7$

Compare a versão simples com a versão estendida. O quociente e o resto não mudam, mas o algoritmo estendido calcula mais valores intermediários em cada etapa. O algoritmo começa com duas equações padrão e, em seguida, continua subtraindo a última equação $q_i$ vezes da equação anterior:

$$
\begin{array}{rcrcc|c}
1 \cdot 1057 & + & 0 \cdot 315 & = & 1057 & \qquad q_i\\
0 \cdot 1057 & + & 1 \cdot 315 & = & 315 & \mathsf{subtrair}\ 3\ \mathsf{vezes} \\
1 \cdot 1057 & + & -3 \cdot 315 & = & 112 & \mathsf{subtrair}\ 2\ \mathsf{vezes} \\
-2 \cdot 1057 & + & 7 \cdot 315 & = & 91 & \mathsf{subtrair}\ 1\ \mathsf{vezes} \\
3 \cdot 1057 & + & -10 \cdot 315 & = & 21 & \mathsf{subtrair}\ 4\ \mathsf{vezes} \\
-14 \cdot 1057 & + & 47 \cdot 315 & = & 7 &\\
x \cdot a\quad\ \ &+&y \cdot b\quad&=&d
\end{array}
$$
Então, descobrimos que $x=-14, y=47$.

Verificando: $-14 \cdot 1057 + 47 \cdot 315 = -14\,798 + 14\,805 = 7$

*[4.7] Use este algoritmo para calcular $x$ e $y$ para $a=23$ e $b=101$.*

*[4.8] Modifique sua implementação do algoritmo de Euclides na Parte 1 para calcular $x$ e $y$ (os coeficientes de Bézout). Use seu algoritmo para calcular $\text{mdc}(19,1001)$ usando este método.*

### Calculando inversos

A AEE pode ser usada para calcular inversos multiplicativos de forma eficiente:

**Corolário**: Se $a$ e $N$ são primos entre si ($\text{mdc}(a, N) = 1$), então $a$ tem um inverso multiplicativo $a^{-1}$ módulo $N$.

O **Algoritmo Euclidiano Estendido (AEE)** resolve para inteiros $x$ e $y$ tais que:
$$
a \cdot x + N \cdot y = \text{mdc}(a, N)
$$
Quando $\text{mdc}(a, N) = 1$, a equação se torna:
$$
a \cdot x \equiv 1 \mod N
$$
Aqui, $x$ é o **inverso multiplicativo** de $a$ módulo $N$, denotado $a^{-1} \mod N$.

*[4.9] Mostre como calcular $23^{-1} \mod 101$ usando o resultado da questão 4.8. Dica: considere $ax+101\cdot y=d$ módulo $101$.*

*[4.10] Use 4.8 para calcular $19^{-1} \mod 1001$.*