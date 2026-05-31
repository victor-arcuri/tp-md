# Tópico 5

## Fórmula de Gauss

**Teorema** *Para todo inteiro positivo $n$, temos $\sum_{d|n} \varphi(d) = n$*

Exemplo: $n=10: \varphi(1)+\varphi(2)+\varphi(5)+\varphi(10)=1+1+4+4=10$

*[5.1] Verifique este teorema para* $n=35,36,37$

Apresentamos a intuição da demonstração usando $n=20$ como exemplo. Existe uma relação clara entre a ordem dos elementos $a$ em $\mathbb{Z}_p^*$ e a representação de frações, como mostramos neste exemplo:

$$
\begin{array}{c|ccccc ccccc ccccc ccccc}
a & 1 & 2 & 3 & 4 & 5 & 6 & 7 & 8 & 9 & 10 & 11 & 12 & 13 & 14 & 15 & 16 & 17 & 18 & 19 & 20 \\ \hline
\frac{a}{20}& 
\frac{1}{20}&\frac{1}{10}&\frac{3}{20}&\frac{1}{5}&
\frac{1}{4}&\frac{3}{10}&\frac{7}{20}&\frac{2}{5}&
\frac{9}{20}&\frac{1}{2}&\frac{11}{20}&\frac{3}{5}&
\frac{13}{20}&\frac{7}{10}&\frac{3}{4}&\frac{4}{5}&
\frac{17}{20}&\frac{9}{10}&\frac{19}{20}& 1 \\
ord(a) & 20 & 10 & 20 & 5 & 4 & 10 & 20 & 5 & 20 & 2 &
20 & 5 & 20 & 10 & 4 & 5 & 20 & 10 & 20 & 1 
\end{array}
$$


É claro que a ordem de um elemento (o denominador da fração simplificada) é sempre um divisor de 20. Observe também que $a$ tem ordem $d=20$ em $\mathbb{Z}^+$ exatamente quando a fração $\frac{a}{20}$ não pode ser simplificada, o que ocorre quando $mdc(a,20)=1$. Portanto, o número de elementos distintos $a$ com ordem 20 é $\varphi(20)=8$. Esse mesmo argumento também se aplica a elementos de ordem $d=10, 5, 4, 2, 1$. Logo, como cada $a$ tem alguma ordem $d$, temos que:

$$
20 = \varphi(20)+\varphi(10)+\varphi(5)+\varphi(4)+\varphi(2)+\varphi(1)=8+4+4+2+1+1
$$

Generalizando para $n$ arbitrário, obtemos uma demonstração formal.



## A estrutura de $\mathbb{Z}_p^*$

**Teorema** *Se $p$ é primo, então o grupo multiplicativo* $\mathbb{Z}_p^*$ *é cíclico de ordem $p-1$.*

Em outras palavras, $Z_p^* \cong C_{p-1}$, logo deve existir um elemento $g$ de ordem $p-1$, chamado gerador (e em alguns contextos, raiz primitiva da unidade).

**Exemplo:** 2 é um gerador módulo 11, como mostra a lista a seguir:
$$
\begin{array}{l|cccccccccc}
g=2 & g^0 & g^1 & g^2 & g^3 & g^4 & g^5 & g^6 & g^7 & g^8 & g^9 & g^{10} \\
\hline
g^i \pmod {11} & 1 & 2 & 4 & 8 & 5 & 10 & 9 & 7 & 3 & 6 & 1
\end{array}
$$

*[5.2] Identifique quais outros elementos módulo 11 são geradores e quais não são.*

Na verdade, observando a tabela, podemos filtrar rapidamente os outros geradores. Por exemplo, é óbvio que 4=2^2 não pode ser um gerador; nenhuma das potências pares de 2 pode ser um gerador. Nem $2^5 = 10 ≡ -1$. Os únicos geradores possíveis são as potências de $2$ com expoente coprimo com 10: $2^1 = 2, 2^3 = 8, 2^7 = 7$ e $2^9 = 6$. Usamos esse argumento na demonstração acima e na próxima demonstração.

*[5.3] Encontre geradores para* $p = 257, 1009, 65537$

A demonstração do teorema está além do escopo do projeto e é apresentada apenas para fins de completude. Idealmente, bastaria mostrar um gerador $g$ para cada primo $p$, mas, surpreendentemente, isso é impossível porque **não existe nenhum método ou algoritmo determinístico** conhecido que forneça um gerador $g$ dado $p$. Mas, usando um argumento de contagem engenhoso, podemos mostrar que um elemento de ordem $p-1$ deve existir.

Para $p$ fixo, seja $N(d)$ o número de elementos de ordem $d$ em $\mathbb{Z}_p^* = \{a \mid mdc(a,p)=1\}$. Sabemos que o grupo tem ordem $p-1$, então $d$ divide $p-1$. Somando todos os elementos por sua ordem, temos que:
$$
p-1 = \sum_{d|p-1} N(d)
$$
Não sabemos se para cada $d | p-1$ existe um elemento de ordem $d$, mas *se* existir, então devem existir vário;  $\varphi(d)$ para ser preciso. Isso ocorre porque o grupo cíclico $a, a^2, a^3, ..., a^d=1$ é isomorfo ao grupo aditivo $\mathbb{Z}_d^+$, que possui $\varphi(d)$ elementos de ordem $d$. Veja a demonstração da fórmula de Gauss acima.

Assim, para todo $d$, temos que $N(d) \leq \varphi(d)$, e portanto:
$$
p-1 = \sum_{d|p-1} N(d) \leq \sum_{d|p-1} \varphi(d)
$$
Mas, devido à fórmula de Gauss, a soma à direita também é igual a $p-1$, então devemos ter igualdade:
$$
p-1 = \sum_{d|p-1} N(d) = \sum_{d|p-1} \varphi(d) = p-1
$$
Portanto, $N(d) = \varphi(d)$ para todo $d|p-1$. Em particular, $N(p-1)=\varphi(p-1)>0$, o que prova que deve existir pelo menos um elemento de ordem $p-1$, um gerador.




## O Logaritmo Discreto

**Definição** Seja $p$ um número primo e seja $g \in \mathbb{Z}_p^*$ um gerador. Suponha que:
$$
h \equiv g^x \!\pmod p
$$
Então dizemos que $x$ é o *logaritmo discreto* (ou índice) de $h$ módulo $p$ (com gerador $g$).

**Continuando o exemplo anterior**: com $p=11$ e $g=2$:
Obtemos o logaritmo discreto lendo a tabela acima de trás para frente. Por exemplo, o logaritmo discreto de $5$ é $4$, pois $2^4 \equiv 5 \!\pmod{11}$. Da mesma forma, o logaritmo discreto de $9$ é $6$.

[5.4] *Encontre um gerador para* $p=17$ *e crie uma tabela de logaritmos, de* $Z_{17}^*$ a $Z_{16}^+$.

## O problema do logaritmo discreto

Alice escolhe um número primo muito grande $p$ juntamente com um gerador $g$ para $\mathbb{Z}_p^*$. Ela também escolhe um expoente aleatório $x \in \{1,\ldots,p-1\}$ e calcula $h = g^x \pmod p$. Agora ela envia $g, h, p$ para Bob, mas mantém $x$ em segredo, desafiando-o a calcular seu valor. Mas para $p$ suficientemente grande, digamos $2^{10}+2^9=1536$ bits, Bob não consegue recuperar $x$ com os valores atuais.

**Suposição:** *O problema do Logaritmo Discreto é uma função unidirecional: calcular $h$ dados $g$, $x$ e $p$ é fácil (o Python faz isso para nós, usando `pow(g,x,p)`), enquanto calcular $x$ dados $p, $g$ e $h$ é computacionalmente inviável.*

Essa premissa é a base de muitos protocolos criptográficos. Apresentamos aqui o mais importante deles, conhecido como protocolo de troca de chaves de Diffie-Hellman (*Diffie-Hellman Key Exchange*).

Suponha que você more em Belo Horizonte e queira se comunicar de forma privada com um amigo que está em Tóquio. O protocolo a seguir resulta em uma chave privada compartilhada $k$ que ninguém mais consegue calcular, mesmo interceptando todas as mensagens.

##### Protoclo DHKE
1. Alice e Bob concordam com um número primo grande $p$ e um gerador $g$. Eles podem até encontrar bons exemplos na internet, e seus valores não precisam ser ocultados.

2. Alice gera um número aleatório $a \in Z_{p-1}^+$, calcula $A = g^a \pmod p$. Ela envia $A$ para Bob, mantendo $a$ em segredo.

3. Agora Bob faz o mesmo: ele gera um número aleatório $b \in Z_{p-1}^+$, calcula $B = g^b \pmod p$. Ele envia $B$ para Alice, mantendo $b$ em segredo.
4. Ao receber a mensagem $B$, Alice calcula sua chave $k_A = B^a \!\pmod p$.
5. Ao receber a mensagem $A$, Bob calcula sua chave $k_B = A^b \!\pmod p$.

Isso completa o protocolo básico. Observe que Alice e Bob agora compartilham a mesma chave porque $k_A \equiv B^a \equiv (g^b)^a \equiv g^{ba} \equiv g^{ab} \equiv (g^a)^b \equiv A^b \equiv k_B$, toda a aritmética módulo $p$.

Mesmo que o adversário veja $A=g^a$ e $B=g^b$, ele não pode calcular a chave $k$. É verdade que ele pode calcular $AB=(g^a)(g^b)=g^{a+b}$, mas $g^{a+b}\neq g^{ab}=k$.

$$
\begin{array}{lcl}
\mathsf{Alice}&&\mathsf{Bob} \\ \hline
&\qquad\longleftarrow p,g \longrightarrow \qquad \\
&\mbox{(cálculos\ mod\ }p)&\\
a \in \mathbb{Z}_{p-1}^+ &&b \in \mathbb{Z}_{p-1}^+ \\
A = g^a && B=g^b \\
&\longrightarrow A \longrightarrow &\\
&\longleftarrow B \longleftarrow &\\
k_A = B^a && k_B = A^b \\
\end{array}
$$

*[5.5] Implemente uma versão simplificada do protocolo DHKE usando* $p= 2^{64} - 2^{32} + 1$ e $g=7$. *Simule os passos de Alice e Bob acima e verifique se* $k_A \equiv k_B$.

### Usos em criptografia

Sistemas baseados em logaritmos discretos são amplamente utilizados em criptografia.

- A troca de chaves Diffie-Hellman (DHKE) é usada em protocolos como SSH, SSL/TSL, IPSec, Whisper, ...
- Uma variação da DHKE resulta no algoritmo de criptografia Elgamal;
- Uma variação leva a assinaturas digitais.

Observe que o protocolo acima usa a propriedade de que $Z_p^*$ é cíclico. Mas se substituirmos $Z_p^*$ por outro grupo cíclico, a matemática continua funcionando. Há cerca de 20 anos, as pessoas começaram a usar o grupo de pontos em uma curva elíptica como tal grupo, e muitos protocolos de internet, incluindo o HTTPS, usam curvas elípticas hoje. O mesmo vale para muitas blockchains. Por exemplo, o Bitcoin e o Ethereum usam a curva elíptica conhecida como secp256k1 para seus algoritmos de assinatura digital.

Com o possível advento dos computadores quânticos, as curvas elípticas não são consideradas seguras a médio prazo (10 anos), e novos algoritmos criptográficos estão sendo desenvolvidos com base em diferentes problemas computacionais, conhecidos como criptografia baseada em reticulados.





















