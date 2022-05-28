# Logika

- výroková a predikátová logika
    - opreace
    - syntax
    - sémantika
- kvantifikátory
- pravdivost, splnitelnost, dokazatelnost
- normální formy
    - konjunktivní
    - disjunktivní
    - prenexní
    - Hornovy klauzule

## Výroková logika: syntax
_Abeceda výrokové logiky:_

- spočetně mnoho znaků pro výrokové proměnné: x_1, x_2, x_3, ...
- logické spojky: ¬, ∧, ∨, ⇒, ⇔
- závorky: ()

_Formule ve výrokové logice:_

- výroková proměnná
- negace formule
- konjunkce, disjunkce, implikace a ekvivalence formulí

## Výroková logika: sémantika
_interpretace (pravdivostní ohodnocení)_ = zobrazení, které každé výrokové proměnné přiřadí hodnotu _pravda_ (1), nebo _nepravda_ (0)

_valuace_ je funkce přiřazující formuli hodnotu 0, nebo jedna na základě její interpretace

v(x_i) = I(x_i)

v(¬φ) = 0 jestliže v(φ) = 1, jinak 1

v(φ_1 ∧ φ_2) = 0 jestliže v(φ_1) = 0 nebo v(φ_2) = 0, jinak 1

v(φ_1 ∨ φ_2) = 0 jestliže v(φ_1) = 0 a současně v(φ_2) = 0, jinak 1

v(φ_1 ⇒ φ_2) = 0 jestliže v(φ_1) = 1 a současně v(φ_2) = 0, jinak 1

v(φ_1 ⇔ φ_2) = 0 jestliže v(φ_1) ≠ v(φ_2), jinak 1

## Predikátová logika: pojmy
_predikát_ = n-ární relace vyjadřující vlastnosti nebo vztahy

_nulární predikát (sentence)_ odpovídá proměnné

_nulární funkce_ = konstanta

_term_ = konstanta, proměnná, nebo funkční symbol arity n aplikovaný na n termů

_atomická formule_ = predikátový symbol arity n aplikovaný na n termů

_literál_ = atomická formule nebo její negace

_klauzule_ = disjunkce literálů

_vázaný výskyt proměnné_ = každý výstyt x ve formuli ∀x.φ respektive ∃x.φ

_volný výskyt proměnné_ = každý výskyt, který není vázaný

## Predikátová logika: syntax
_Abeceda predikátové logiky:_

- spočetně mnoho znaků pro proměnné: x_1, x_2, x_3, ...
- spočetně mnoho predikátových symbolů: P, Q, ...
- spočetně mnoho funkčních symbolů: f, g, ...
- logické spojky: ¬, ∧, ∨, ⇒, ⇔
- kvantifikátory: ∀, ∃
- závorky a čárka: (),

_Formule v predikátové logice:_

- atomické formule
- negace formule
- konjunkce, disjunkce, implikace, ekvivalence formulí
- kvantifikace formule

## Predikátová logika: sémantika
_univerzum_ = neprázdný soubor prvků
_valuace (pravdivostní ohodnocení)_ = zobrazení přiřazující proměnným prvky univerza

Každému n-árnímu predikátovému symbolu P je přiřazena n-ární relace P_𝓜 na M, kde M je univerzum a 𝓜 je reprezentace.

Každému m-árnímu funkčnímu symbolu je přiřazena funkce f_𝓜 : M^m -> M

Každé volně se vyskytující proměnné je přiřazen prvek univerza.

## Kvantifikátory
_univerzální kvantifikátor ∀_ = zobecnění konjunkce pro nekonečné domény

∀x.P(x) ... pro každý prvek x z domény platí P(x)

_existenční kvantifikátor ∃_ = zobecnění disjunkce pro nekonečné domény

∃x.P(x) ... exisuje alespoň jeden prvek x domény, pro který platí P(x)

## Pravdivost, splnitelnost, dokazatelnost
Formule φ je _pravdivá při valuaci_ v, pokud v(φ) = 1

Formule φ je _nepravdivá při valuaci_ v, pokud v(φ) = 0

Formule φ je _tautologie_, pokud pro každou valuaci v platí v(φ) = 1; zapisujeme ⊨ φ

Formule φ je _kontradikce (nesplnitelná)_, pokud pro každou valuaci v platí v(φ) = 0, zapisujeme ⊨ ¬φ, nebo φ ⊨

Formule φ je _splnitelná_, pokud existuje valuace v taková, že v(φ) = 1

Formule φ je _dokazatelná z neprázdného souboru formulí_ T, pokud existuje důkaz T ⊢ φ

Formule φ je _dokazatelná_, pokud je dokazatelná z prázdného souboru formulí ⊢ φ

## Normální formy
_konjunktivní normální forma_ = konjunkce klauzulí
př. ¬A ∧ (B ∨ C) ∧ (D ∨ ¬E)

_úplná konjunktivní normální forma_ = každá klauzule obsahuje všechny proměnné

_disjunktivní normální forma_ = disjunkce konjunkcí literálů
př. ¬A ∨ (B ∧ C) ∨ (D ∧ ¬E)

_úplná disjunktivní normální forma_ = každá konjunkce obsahuje všechny proměnné

### Prenexní normální forma
Má kvantifikátory pouze na začátku a vnitřek je v NKF (NDF)

_Algoritmus převodu:_

1. Eliminace zbytečných kvantifikátorů
2. Přejmenování proměnných, aby u každého kvantifikátoru byla jiná proměnná
3. Eliminace spojek různých od: ¬, ∧, ∨
4. Přesunutí negací dovnitř
    - ¬∀x φ -> ∃x ¬φ
    - ¬(φ_1 ∧ φ_2) -> φ_1 ∨ φ_2
5. Přesunutí kvantifikátorů na začátek
    - φ_1 ∨ ∃x.φ_2 -> ∃x.(φ_1 ∨ φ_2)
    - ∃x.φ_1 ∨ φ_2 -> ∃x.(φ_1 ∨ φ_2)
    - ekvivaletně s ∧ a ∀ a kombinacemi
6. Převod nekvantifikované podformule do NKF nebo NDF

Příklad: ∀x∀y∃z∀w.((P(x,y) ∨ ¬Q(z)) ∧ (R(v, w) ∨ R(y, w)))

## Hornovy klauzule
_klauzule_ = disjunkce literálů

_Hornova klauzule_ = klauzule s nejvýše jedním pozitivním literálem, např {p, ¬q, ¬r} (= p ∨ ¬q ∨ ¬r; také p :- r, q. v Prologu)

Dělíme na:

- _fakta_ = právě jeden pozitivní literál, např. p.
- _pravidla_ = právě jeden pozitivní literál a alespoň jeden negativní literál, např. p :- q.
- _cíle_ = bez pozitivních literálů, např. ?-p.

Hornovy klauzule využívá Prolog.
