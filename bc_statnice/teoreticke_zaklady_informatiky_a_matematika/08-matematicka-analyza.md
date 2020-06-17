# Matematická analýza
- vlastnosti reálných funkcí
- polynomy
- spojité funkce a limity
- derivace
- neurčitý integrál
- určitý integrál
- geometrický význam
- diferenciální rovnice a jejich význam

## Vlastnosti reálných funkcí I.

_funkce_ = předpis, který každému číslu x z definičního oboru D(f) přiřadí nanejvýš jedno y z oboru hodnot H(f)

### Monotonnost funkce
_rostoucí funkce_ = x_1 < x_2 ⇒ f(x_1) < f(x_2)

_klesající funkce_ = x_1 < x_2 ⇒ f(x_2) < f(x_2)

_neklesající funkce_ = x_1 < x_2 ⇒ f(x_1) ≤ f(x_2)

_nerostoucí funkce_ = x_1 < x_2 ⇒ f(x_1) ≥ f(x_2)

_konstantní funkce_ = x_1 < x_2 ⇒ f(x_1) = f(x_2)

Funkce může klesat, růst, ... pouze na určitém _intervalu_.

## Vlastnosti reálných funkcí II.
_sudá funkce_ = f(x) = f(-x)

_lichá funkce_ = f(x) = -f(-x)

_prostá funkce_ = x_1 ≠ x_2 ⇒ f(x_1) ≠ f(x_2) (příma rovnoběžná s osou ji protne právě v jednom bodě)

_inverzní funkce_ = f(x) = y ≡ f^{-1}(y) = x

## Vlastnosti reálných funkcí III.

_shora omezená_ = ∃ A ∈ ℝ, pro všechny x ∈ D(f): A > f(x)

_zdola omezená_ = ∃ A ∈ ℝ, pro všechna x ∈ D(f): A < f(x)

_maximum funkce_ M = pro všechna x ∈ D(f): f(x) ≤ f(M)

_minimum funkce_ M = pro všechna x ∈ D(f): f(x) ≥ f(M)

_globální max/min_ - může jich být víc (může se realizovat pro více hodnot z definičního oboru)
_ostré max/min_ - je právě jedno

_periodická funkce_ - např. sin, cos, ...

## Polynomy (mnohočleny)
_polynom_ = výraz sestávající se z součtů, rozdílů, násobků a celočíselných mocnin proměnných

p(x) = Σ_{i=0}^n a_i · x^i = a_0 · x^0 + a_1 · x^1 + a_2 · x^2 + ... + a_n · a_n · x^n

a ∈ ℝ ... koeficient

n ... stupeň mnohočlenu

_sčítání a odečítání_ - sčítáme/odečítáme koeficienty se stejným exponentmproměnné

_násobení_ - každý s každým

_vozrečky:_

(A + B)^2 = A^2 + 2AB + B^2

(A - B)^2 = A^2 - 2AB + B^2

(A + B)^3 = A^3 + 3A^2B + 3AB^2 + B^3

(A - B)^3 = A^3 - 3A^2B + 3AB^2 - B^3

A^2 - B^2 = (A + B)(A - B)

p^{A + B} = p^A · p^B

p^{A - B} = p^A \ p^B

...

## Limity

### Limita posloupnosti
Posloupnost a_n má _vlastní limitu a_, jestliže ke každému ϵ > 0 existuje n_0 ∈ ℕ takové, že pro všechna n > n_0 platí |a_n - a| < ϵ.

### Limita funkce
Funkce f má v bodě x_0 _vlastní limitu ve vlastním bodě L_, jestliže platí:

( ϵ > 0)(∃ δ > 0)( x ∈ ℝ): (0 < |x - x_0| < δ ⇒ |f(x) - L| < ϵ)

### Limita zleva a zprava
Limita v bodě existuje (uvnitř definičního oboru), právě když se limity zprava a zleva rovnají.

## Spojité funkce
Funkce f je _spojitá_ v bodě x_0, jestliže je v tomto bodě definovaná a limita funkce v tomto bodě se rovná její funkční hodnotě.

Každý polynom je spojitou funkcí na celém ℝ.

Nechť f a g jsou spojité funkce v bodě x_0.

- f + g je spojitá v bodě x_0
- f · g je spojitá v bodě x_0

## Derivace
= směrnice tečny funkce

Funkce f má v bodě x_0 derivaci _a_ právě, když existuje limita (vzoreček na obrázku):

![](08/IMG_4646.JPG)

Derivace je vlastní (když a ∈ ℝ) / nevlastní (rovna kladnému nebo zápornému nekonečnu) v závislosti na limitě. Derivace zprava a zleva odpovídají limitám zprava/zleva.

-> Z defivace lze určit, jestli je funkce rostoucí/klesající.

Obrázek výše obsahuje taky některé vzorečky derivací.

## Výpočty s derivacemi

_Určení monotonnosti funkce_

- f'(x) > 0 ⇒ f je rostroucí
- f'(x) < 0 ⇒ f je klesající

_Lokální extrémy_

- f'(x) = 0 nebo derivace v tomto bodě neexistuje
- defivace mění při přechodu přes tento bod znaménko

_Konvexnost/konkávnost_

- f''(x) > 0 ⇒ f je konvexní
- f''(x) < 0 ⇒ f je konkávní

_Inflexní bod_ - druhá derivace neexistuje, nebo je rovna 0

## Neurčitý integrál (primitivní funkce)

Primitivní funkce F(x) k funkci f(x) je na každém intervalu [a,b] určena jednoznačně až na aditivní konstantu. Výsledkem je množina primiivních funkcí. Využití v newtonově integrálu.

### Určitý integrál (Newtonův integrál)

Vzoreček na obrázku:

![](08/IMG_4648.JPG)

Geometricky odpovídá velikosti plochy vymezené grafem funkce a osou x.

## Diferenciální rovnice
_diferenciální rovnice primitivního řádku_ = vztah mezi derivací funkce y'(t) v proměnné t, její hodnotou y(t) a samotnou proměnnou. F: ℝ^3 -> ℝ, F(y', y, t) = 0

Řešením diferenciální rovnice je funkce nebo třída funkcí.

př.: y'' + 2y' = 3y ... y = e^x (jedno z možných řešení)
