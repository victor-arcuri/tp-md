# 3 -- Classes de congruência



**Definição** Seja $m$ um inteiro. Dizemos que $a$ é congruente a $b$ módulo $m$, ou que $a$ e $b$ pertencem à mesma classe de congruência, se $a-b$ for múltiplo de $m$, ou seja, existe $k \in \mathbb{Z}$ tal que
$$
a-b = k\cdot m
$$
Notação matemática:
$$
a \equiv b \pmod m
$$

Em outras palavras, significa que o resto módulo $m$ é o mesmo em ambos os casos. Em Python, C e Python, `%` é o operador mod, então isso significa que o teste
```
a % m == b % m
```
retorna `True`.

Usamos aritmética modular no dia a dia:

- $8272107104 \equiv 8274104 \pmod {1000}$ apenas verificando os três últimos dígitos.
- $2 \equiv 14 \pmod {12}$, então ambos representam 2 horas, de noite ou de tarde.
- $3 \equiv 24 \pmod{7}$, então o 3º e o 24º dia de um mês caem no mesmo dia da semana
- *Curiosidade:* as datas 04/04, 06/06, 08/08, 10/10 e 12/12 de um ano caem todos no mesmo dia da semana; em 2025, esta é uma sexta-feira. Isso ocorre porque, em todos os casos, o número de dias entre duas destas datas é $30+31+2=63$ ou $31+30+2=63$, um múltiplo de $7$. Também temos que 09/05, 05/09 e 07/11 e 11/07 caem no mesmo dia da semana. Março e fevereiro são mais complicados por causa dos anos bissextos. Mas o último dia de fevereiro, matematicamente conhecido como 00/03, também cai neste dia. Se não for um ano bissexto, o último dia de janeiro, 31/01, também.



### Adição modular

É possível realizar a adição módulo $n$:
$$
a \text{\ mod\ } n+b \text{\ mod\ } n = (a+b) \text{\ mod\ } n
$$
Observe que obtemos as propriedades de um grupo Abeliano:

- **fechado** $\forall\ a,b \in G: a + b \in \mathbb{Z}_n^*$

- **associativo** $\forall\ a,b,c \in \mathbb{Z}_n^*: (a + b) + c = a + (b + c)$

- **elemento neutro de existência** $\forall\ a \in \mathbb{Z}_n^*: a + 0 = 0 + a = a$

- **elemento inverso de existência** $\forall\ a \in \mathbb{Z}_n^*\ \exists\ -a: a + (-a) = (-a) + a = 0$

- **comutativo** $\forall\ a,b \in \mathbb{Z}_n^*: a + b = b+a$




### Exemplo: calcular ou verificar os dígitos de verificação do CPF

Para calcular ou verificar o primeiro dígito de verificação do CPF  (aquele imediatamente seguindo o hífen), considera-se os primeiros nove dígitos, $x_0 x_1 \ldots x_8$,
e calcula-se $d_1 = (1\cdot x_0+2 \cdot x_1 + \cdots + 9 \cdot x_8) \bmod 11$. Um resto módulo 11 poderia dar 10, que é mapeado para 0. Então se $d_1 = 10$ então $x_{9} := 0$; senão, $x_{9} := d_1$.

Calcula-se ou verifica-se também o segundo dígito, assim:
$x_{10} = (0 \cdot x_0+1 \cdot x_1 + 2 \cdot x_2 \cdots + 8 \cdot x_8 + 9 \cdot x_{9}) \bmod 11$ onde, de novo, um eventual resto 10 resulta no dígito 0.

[3.1] Escreva uma função `ver_cpf()` que verifica se um CPF é válido (retornar `True`) ou não (retornar `False`)


A adição modular também é usada na criptografia.

### Exemplo: Cifra de Vigenère usando o grupo aditivo módulo $26$

- Usamos conjunto $\{0, 1, 2, \dots, 25\}$ sob adição módulo $26$.
- Representamos os números por letras: A=0, B=1, ..., Z=25
- Definimos a 'adição' de letras. Exemplo:  $Z+D=25 + 3 = 2 = C \pmod 26$.

- Sejam $p$ a mensagem original, $k$ a chave, e $c$ a mensagem cifrada. Para cifrar usamos a adição: $c_i = (p_i + k_i) \pmod 26$ em cada letra das mensagens.

Exemplo:
1. **Texto claro**: $p=$`"CRYPTO"`
- Converta para números: $C=2, R=17, Y=24, P=15, T=19, O=14$.
2. **Chave**: $k=$`"KEY"` (repetido como `"KEYKEY"`).
- Converta para números: $K=10, E=4, Y=24$.
3. **Texto cifrado**: $c=$`"MVWZXM"`.

[3.2] Verifique este exemplo usando Python. Use as seguintes funções para converter entre letras e números

```
# Versão  usando string e index()
def numero_para_letra_v2(numero):
    """Converte um número (0-25) para letra (A-Z) usando string e index."""
    letras = "ABCDEFGHIJKLMNOPQRSTUVWXYZ"
    if not 0 <= numero <= 25:
        raise ValueError("O número deve estar entre 0 e 25.")
    return letras[numero]

def letra_para_numero_v2(letra):
    """Converte uma letra (A-Z) para número (0-25) usando string e index()."""
    letras = "ABCDEFGHIJKLMNOPQRSTUVWXYZ"
    if not letra.isalpha() or not letra.isupper() or len(letra) != 1:
        raise ValueError("A entrada deve ser uma única letra maiúscula (A-Z).")
    return letras.index(letra)
```

**Parte 2: Decifrar**: $P_i = (C_i - K_i) \pmod 26$
1. **Texto cifrado**: $c=$`"MVWZXM"` → $M=12, V=21, W=22, Z=25, X=23, M=12$.
2. **Chave**: $k=$`"KEYKEY"` → $K=10, E=4, Y=24$.
4. **Texto claro Recuperado**: $p=$`"CRYPTO"`.

[3.3] Verifique este exemplo de descriptografia.


**Principais Conclusões**
- Vigenère usa **aritmética modular** ($\mathbb{Z}_{26}$) para generalizar deslocamentos.
- A segurança depende do **comprimento da chave** e da **aleatoriedade**.
- O grupo aditivo $\mathbb{Z}_n$ é fundamental para cifras clássicas.



### Como fica no mundo digital, dos bits 0 e 1

[3.4] Crie uma tabela para todas as quatro adições possíveis módulo 2. Compare-a com uma tabela da operação ou-exclusivo (xor). O que você vê?

# Produto direto de grupos aditivos

**Definição** Sejam $G_1$ e $G_2$ dois grupos. Então, o produto direto $G$ tem

- defina $$G_1 \times G_2 = \{(g_1,g_2)|g_1 \in G_1 \wedge g_2 \in G_2\}$$;

- operação $(g_1,g_2) \cdot (h_1,h_2) := (g_1 h_1, g_2 h_2)$

**Exemplo**

$\mathbb{Z}_3 \times \mathbb{Z}_5 = \{(g,h) \mid 0 \leq g < 3 \wedge 0 \leq h < 5 \}$

$(2,4)+(0,3)=(2+0\!\pmod 3, 4+3 \!\pmod 5)=(2,2)$

Na verdade, $\mathbb{Z}_3 \times \mathbb{Z}_5$ é equivalente (exceto pela notação) a $\mathbb{Z}_{15}$:
$$
\mathbb{Z}_3 \times \mathbb{Z}_5 = \mathbb{Z}_{15}
$$

$$
\begin{array}{c|ccccc}
&0&1&2&3&4\\ \hline
0&0=(0,0)&6=(0,1)&12=(0,2)&3=(0,3)&9=(0,4) \\
1&10=(1,0,0)&1=(1,1)&7=(1,2)&13=(1,3)&4=(1,4) \\
2&5=(2,0)&11=(2,1)&2=(2,2)&8=(2,3)&14=(2,4) \\
\end{array}
$$

[3.5] Produza uma tabela semelhante para $n = 35$

# Outro exemplo: 11 x 13 = 143

![Captura de tela 2021-07-01 140847](.\Screenshot 2021-07-01 140847.png)

Vimos que $\mathbb{Z}_{143}^+ \cong \mathbb{Z}_{11}^+ \times \mathbb{Z}_{13}^+$. Isso pode ser generalizado:

**Teorema** Sejam $n$ e $m$ coprimos. Então
$$
\mathbb{Z}_{nm}^+ \cong \mathbb{Z}_n^+ \times \mathbb{Z}_m^+
$$
significando que ambos os grupos são isomorfos. Ou seja, os grupos são idênticos, exceto pela notação usada nos elementos.

Outra maneira de afirmar isso é por meio do teorema chinês do resto.

# Teorema Chinês do Resto

**Intuição** Suponha que se saiba que $a \equiv 3 \!\pmod {11}$ e $a \equiv 5 \!\pmod {13}$. Existe apenas um valor $\pmod {143}$ que satisfaz ambas as equações. A tabela acima mostra que esse valor é $135$.

Esta afirmação pode ser generalizada.

### **Teorema Chinês do Resto (TCR)**
O Teorema Chinês do Resto afirma que, para um sistema de módulos **coprimos em pares** $n_1, n_2, \dots, n_k$ e números inteiros dados $a_1, a_2, \dots, a_k$, existe uma **solução única** $x$ módulo $N = n_1 \cdot n_2 \cdots n_k$ para o sistema de congruências:

$$
\begin{cases}
x \equiv a_1 \pmod {n_1} \\
x \equiv a_2 \pmod {n_2} \\
\vdots \\
x \equiv a_k \pmod {n_k}
\end{cases}
$$

Além disso, se $x$ é uma solução, então toda solução é congruente a $x \pmod N$.


### **Exemplo**
Encontre um inteiro $x$ tal que:
$$
\begin{cases}
x \equiv 2 \pmod 3 \\
x \equiv 3 \pmod 5 \\
x \equiv 2 \pmod 7
\end{cases}
$$

#### **Solução Passo a Passo**
1. **Verifique se os módulos são primos entre si**:
$mdc(3,5) = 1$, $mdc(3,7) = 1$, $mdc(5,7) = 1$.
→ O TCR se aplica, pois todos os módulos são primos entre si.

2. **Calcule $N = 3 \times 5 \times 7 = 105$**.

3. **Encontre soluções parciais**:
- **Para** $x \equiv 2 \pmod 3$:
- Seja $x = 5 \times 7 \times k_1 = 35k_1$.
- Use tentativa e erro para encontrar um múltiplo de 35 que seja $2 \pmod 3$. Ou seja, encontre $k_1 \in \{1,2\}$ tal que $35k_1 \equiv 2 \pmod 3$.
- $k_1 = 1$ está correto, já que $35 k_1 \equiv 25 \equiv 2 \pmod3$
- A solução parcial é $x_1 = 35 \times 1 = 35$.
- Observe que $35 = (2,0,0) \pmod {(3,5,7)}$

- **Para** $x \equiv 3 \pmod 5$:
- Seja $x = 3 \times 7 \times k_2 = 21k_2$.
- Use tentativa e erro para encontrar um múltiplo de 21 que seja $3 \pmod 5$. Ou seja, encontre $k_2 \in \{1,2,3,4\}$ tal que $21k_2 \equiv 3 \pmod 5$.
- $k_2 = 3$ é aceitável, já que $21 k_2 = 21 \cdot 3 = 63 \equiv 3 \pmod 5$
- A solução parcial é $x_2 = 21 \times 3 = 63$.

- Observe que $63 = (0,3,0) \pmod {(3,5,7)}$

- **Para** $x \equiv 2 \pmod 7$:
- Seja $x = 3 \times 5 \times k_3 = 15k_3$.
- Encontre um múltiplo de 15 que seja $2 \pmod 7$.
- Resolva $15k_3 \equiv 2 \pmod 7$.
- Como $15 \equiv 1 \pmod 7$, temos $k_3 \equiv 2 \pmod 7$.
- Portanto, $k_3 = 2 + 7m$, e a solução parcial é $x_3 = 15 \times 2 = 30$.
- Observe que $30 = (0,0,2) \pmod {(3,5,7)}$

4. **Combine as soluções parciais**:
A solução geral é:
$$
\begin{array}{l}
x \equiv x_1 + x_2 + x_3 \pmod 105 \\
x=(2,0,0)+(0,3,0)+(0,0,2) \pmod {3,5,7} \\
x \equiv 35 + 63 + 30 \pmod 105 \\
x \equiv 128 \pmod {105} \implies \\
x \equiv 23 \pmod {105} \\
\end{array}
$$

5. **Verificação**:
- $23 \pmod 3 = 2$ ✓
- $23 \pmod 5 = 3$ ✓
- $23 \pmod 7 = 2$ ✓

#### **Resposta final**:
A menor solução positiva é $x = 23$. Todas as soluções têm a forma $x = 23 + 105k$ para o inteiro $k$.

[3.6] Use Python para encontrar uma solução para
$$
\begin{cases}
x \equiv 5 \pmod 7 \\
x \equiv 4 \pmod {11} \\
x \equiv 10 \pmod {13}
\end{cases}
$$
Verifique sua resposta.

### **Principais Conclusões**
- A TCR garante uma **solução única** módulo $N$ se os módulos forem primos entre si.
- Usado em criptografia (por exemplo, descriptografia RSA), hashing e cálculos rápidos.