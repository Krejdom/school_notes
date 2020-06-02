# Množiny, relace a zobrazení

- základní množinové operac
- relace a jejich vlastnosti
    - ekvivalence a rozklady
    - uspořádání a uspořádané množiny
- skládání relací, zobrazení
    - injekce
    - surjekce
    - bijekce

## Množiny
_množina_ = soubor prvků, který je těmito prvky plně určen

x ∈ M „x je prvkem množiny M“

x ∉ M „x není prvkem množiny M“

∅ je prázdná množina

_mohutnost (kardinalita) množiny_ = počet prvků množiny

|∅| = 0, |{∅}| = 1, |{a, b, c}| = 3

_podmnožina (inkluze)_ A ⊆ B = každý prvek A je prvkem B

_vlastní podmnožina_ A ⊊ B = A ⊆ B a zároveň A ≠ B

## Základní množinové operace
_sjednocení_ A ⋃ B = {x | x ∈ A ∨ x ∈ B}

_průnik_ A ⋂ B = {x | x ∈ A ∧ x ∈ B}

_distributivita_ A ⋂ (B ⋃ C) = (A ⋂ B) ⋃ (A ⋂ C) (stejně s prohozenými operacemi)

_asociativita_ A ⋂ (B ⋂ C) = (A ⋂ B) ⋂ C (stejně se sjednocením)

_komutativita_ A ⋂ B = B ⋂ A (stejně se sjednocením)

_rozdíl_ A \ B = {x | x ∈ A ∧ x ∉ B}

_symetrický rozdíl_ A △ B = (A ⋃ B) \ (A ⋂ B)

_potenční množina_ 2^A = { B | B ⊆ A}

## Relace
_relace_ mezi množinami A_1, ..., A_k pro k ∈ ℕ je libovolná podmnožina jejich kartézského součinu

Podle počtu množin rozlišujeme _unární_, _binární_ či _termární_ relace.

_totální funkce_ z množiny A do B je relace _f_ mezi A a B taková, že pro každé x ∈ A existuje právě jedno y ∈ B takové, že (x, y) ∈ f (častěji píšeme f(x) = y)

A je _definiční obor_

B je _obor hodnot_

_parciální funkce_ podobně jako u totální funkce, jen pro každé x ∈ A existuje _nejvýš_ jedno y ∈ B

## Vlastnosti binárních relací (R ⊆ A^2)
_reflexivní_ = pro každé a ∈ A platí (a, a) ∈ R

_ireflexivní_ = pro každé a ∈ A platí, (a, a) ∉ R

_symetrická_ = pro každé a, b ∈ A platí, že jestliže (a, b) ∈ R, pak také (b, a) ∈ R

_antisymetrická_ = pro každé a, b, ∈ A platí, že jestliže (a, b) ∈ R a zároveň (b, a) ∈ R, pak a = b

_tranzitivní_ = pro každé a, b, c ∈ A platí, že jestliže (a, b), (b, c) ∈ R, pak také (a, c) ∈ R

Reflexivita, symetrie a tranzitivita jsou uzavíratelné vlastnosti (na rozdíl od ireflexivity a antisymetrice). V-uzávěr relace R pro libovolnou uzavíratelnou vlastnost V je nejmenší množina R^V taková, že R ⊆ R^V a zároveň R^V má vlastnost V.

## Ekvivalence a uspořádání
Relace je _ekvivalence_ právě, když je:

- reflexivní
- symetrická
- tranzitivní

Relace je _částečné uspořádání_ právě, když je:

- reflexivní
- antisymetrická
- tranzitivní

(relace může být symetrická i antisymetrická zároveň)

## Rozklad
_Rozklad_ na M je množina podmnožin N ⊆ 2^M splňující tyto podmínky:

- ∅ ∉ N
- pokud A, B ∈ N, pak buď A = B, nebo A ⋂ B = ∅
- ⋃_{A ∈ N} = M

_Třída rozkladu_ je prvek množiny N (popsané výše)

## Uspořádané množiny
_Uspořádaná množina_ je dvojice (M, ≤), kde M je množina a ≤ je (částečné) uspořádání na M

_lineární (úplné) uspořádání na M = každé dva prvky jsou v ≤ srovnatelné

příklad: uspořádání po složkách, lexikografické uspořádání

## Pojmy uspořádaných množin I.
_minimální prvek_ = neexistuje žádný menší prvek

_maximání prvek_ = neexistuje žádný větší prvek

_nejmenší prvek_ = všechny ostatní prvky jsou větší

_největší prvek_ = všechny ostatní prvky jsou menší

x ∈ M _pokrývá_ y ∈ M právě, když x ≠ y, y ≤ x a neexistuje žádné z ∈ M takové, že x ≠ y ≠ z a y ≤ z ≤ x

A ⊆ M je _řetězec_ v uspořádání ≤ právě, když (A, ≤) je lineárně uspořádaná množina.

## Pojmy uspořádaných množin II.

x ∈ M _je dolní závora_ množiny A ⊆ M právě, když pro každé y ∈ A platí x ≤ y.

x ∈ M _je horní závora_ množiny A ⊆ M právě, když pro každé y ∈ A platí y ≤ x.


_infimum_ = největší dolní závora

_supermum_ = nejmenší horní závora

## Skládání funkcí

Mějme funkce f: A -> B a g: B -> C; pak (g ∘ f): A -> C (čti „gé po ef“); (g ∘ f)(x) = g(f(x)).

## Vlastnosti funkcí

Funkce f: A -> B je:

_injektivní (prostá)_ = pro každé x, y ∈ A, x ≠ y, platí f(x) ≠ f(y) (každé x má své vlastní y)

_surjektivní_ = pro každé y ∈ B existuje x ∈ A takové, že f(x) = y (každé y má svoje x)

_bijektivní (vzájemně jednoznačná)_ = injektivní a zároveň surjektivní