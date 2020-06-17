# Korektnost a složitost algoritmu
- parciální a totální korektnost
- důkazy korektnosti
- asymptotická složitost
- o-notace
- zdůvodnění korektnosti a složitosti základních algoritmů
    - řadicí algoritmy
    - binární vyhledávání

## Korektnost I.
_vstupní podmínka_ - ze všech možných vstupů pr daný algoritmus vymezujeme ty, pro které je algoritmus definován

_výstupní podmínka_ - pro každý vstup daného algoritmu splňující vstupní podmínku určuje, jak má vypadat výsledek odpovídající danému vstupu

_invariant cyklu_ - tvrzení o algoritmu, které platí před a po vykonání každé iterace cyklu

Přesněji: {I} while P do {P ∧ I} XXX {P ∧ I} od / {¬ P ∧ I}

## Korektnost II.
Algoritmus je _parciálně korektní_, pokud pro každý vstup, který splňuje vstupní podmínku a algoritmus na něm skončí, výstup splňuje výstupní podmínku.

Algoritmus je _úplný_ (konvergetntní), pokud pro každý vstup splňující vstupní podínku výpočet skončí.

Algoritmus je _totálně korektní_, právě když je parciálně korektní a úplný.

## Důkazy korektnosti

### Korektnosti iterativního algoritmu
- Pro každý cyklus určíme invariant.
- Začínáme od nejvíce zanořených cyklů
- Pomocí invariantu dokážeme
    - konečnost výpočtu cyklu
    - efekt cyklu
- Dokazujeme platnost tří fází:
    - _inicializace_ = platnost invariantu před vykonáním cyklu
    - _iterace_ = invariant platí před i po každé iteraci
    - _ukončení_ = cyklus skončí a platný invariant garantuje požadovaný efekt cyklu

### Korektnost rekurzivního algoritmu
- Pomocí matematické indukce

## Asymptotická složitost
_Složitost_ vyjadřuje náročnost algoritmu na zdroje výpočtu: čas, paměť, počet procesorů, ...

_Délka výpočtu_ konkrétního algoritmu na konkrétním vstupu odpovídá počtu elementárních operací, ze kterých se výpočet skádá

_Časová složistost algoritmU_ je funkce f na množině přirozených čísel taková, že výpočet algoritmu pro každý vstup délky n má délku nejvýše f(n). Obvykle vyjadřujeme asymptoticky.

## Asymptotická notace
o(g) = {f | ∃ c > 0, n_0 ∈ ℕ :  n ≥ n_0 : f(n) ≤ f(n) ≤ c · g(n)}

= množina funkcí rostoucích stejně rychle jako g, nebo pomaleji

Ω(g) = {f | ∃ c > 0, n_0 ∈ ℕ :  n ≥ n_0 : c · g(n) ≤ f(n)}

= množina funkcí rostoucích stejně rychle jako g, nebo rychleji

Θ(g) = o(g) ∪ Ω(g)

= množina funkcí rostoucích stejně rychle jako g

### Vlastnosti
- _tranzitivita_ = f(n) ∈ Θ(g(n)) a g(n) ∈ Θ(h(n)) ⇒ f(n) ∈ Θ(h(n)) (stejně pro o, Ω)
- _reflexivita_ f(n) ∈ θ(f(n)) (stejně pro o, Ω)
- _symetrie_ f(n) ∈ Θ(g(n)) ≡ g(n) ∈ Θ(f(n))
- _transpozice_ f(n) ∈ O(g(n)) ≡ g(n) ∈ Ω(f(n))

## Binární vyhledávání: korektnost
_Invariant_: na začátku každé iterace platí, že jestli se x nalézá v S, tak se nalézá mezi pozicemi f (first) a l (last).

- Inicializace: Na začátku je i = floor((f + l)/2), takže tvrzení platí.
- Iterace: Pokud x ≠ S[i] a x < S[i], nachází se x mezi pozicemi f a i. Pokud x > S[i], mezi i a l. Pokud je vrácena hodnota i, invariant také platí.
- Ukončení: Cyklus končí buď protože S[i] = x, nebo protože f = l ≠ x.

Složitost: o(log_2 n)

## Řadicí algoritmy

Bubble sort | Θ(n^2) | invariant:  a[n-i-1:] ve finální pozici
Insert sort | Θ(n^2) |
Merge sort | Θ(n · log_2 n) |
Quick sort | Θ(n^2) | očekávaná složitost Θ(n · log_2 n)
Heap sort | Θ(n · log_2 n) |
Counting sort | Θ(n + k) | (hodnoty z intervalu 0..k)
Radix sort | Θ(d(n+k)) | čísla z d číslic, číslicové řazení Θ(n)
Bucket sort | Θ(n) + ∑_{n = 0}^{n-1} o(n_i^2)





