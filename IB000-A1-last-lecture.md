### Různá mocnost nekonečen

***Nelze najít bijekci mezi $$$\mathbb N \rightarrow P(\mathbb N)$$$***

- bijekce podle $$$f(n) = \{n\}$$$ pro každé $$$n \in \mathbb N$$$
- Předpokládejme pro spor, že $$$g: \mathbb N \rightarrow P(\mathbb N)$$$ je surjekce.

- "tabulka"
- Vybereme množinu $$$A$$$, definovanou: $$$A = \{a \not \in g(a)\}$$$ (beru diagonálu -- pokud číslo v a-tém sloupci i řádku, tzn. $$$a$$$
- as


*Pozn.:*

- $$$M^*$$$ ... množina všech konečných posloupností prvků množiny M
- $$$M^* = \bigcup \limits_{n\in \mathbb N} M ^ n$$$


*Def.:*

- Množina $$$M$$$ se nazývá **spočitatelná**, právě když existuje injekce $$$f: M \rightarrow \mathbb N$$$

*Pozn.:*

- spočitatelné jsou např.: $$$\emptyset, \{2, 42, 69\}, \mathbb N, \mathbb Z, \mathbb Q, 2^*, \mathbb N^2 $$$


***Důkaz*** $$$f: 2^* \rightarrow \mathbb N$$$

- $$$f(a_n, a_{n-1}, ..., a_1, a_0) = \sum \limits_{i = 0} ^n a_i \cdot 2^{n-1}$$$ tady nastane problém s $$$(0, 0, 0, 1, 0) = (1, 0)$$$

- řešení: $$$f(a_n, a_{n-1}, ..., a_1, a_0) = (\sum \limits_{i = 0} ^n a_i \cdot 2^{n-1}) + 2^n - 1 $$$ a je to bijekce!

***Pozn.:*** -- z předchozího důkazu plyne

- spočetná je každá množina, kterou jde popsat konečnou abecedou

***Existují-li injekce $$$f: A \rightarrow B \wedge g: B\rightarrow A \Leftrightarrow$$$ existuje bijekce $$$ h: A \rightarrow B$$$***