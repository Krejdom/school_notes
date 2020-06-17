# Funkcionální programování
- funkcionální programovací paradigmata
    - princip výpočtu
    - redukční krok
    - redukční strategie a jejich vlastnosti
    - příklady
- funkce vyšších řádů a jejich využití
- lambda funkce
- schopnost elementárního programování v Haskellu

## Funkcionální programovací paradigmata
_deklarativní paradigme_ - klade důraz na to, **co** je řešením daného problému, program je zápisem řešení

_funkce_ = předpis, jak ze vstupu vytvořit výstup

_typ funkce- = vymezení objektů, se kterými funkce pracuje a které vrací na výstup, jsou součástí definice

_skládání funkcí_ (f1 · f2) x = f1 (f2 x) ... „f1 po f2“

- program ... výraz + definice funkcí
- výpočet ... úprava výrazu
- výsledek ... dále nezjednodušitelný tvar výrazu

## Princip výpočtu

1. Definice funkcí
    - square x = x * x
    - pyth a b = square a + square b
2. Výraz
    - pyth 3 4

### Výpočet:

pyth 3 4 -> square 3 + square 4 -> 3 * 3 + square 4 -> 3 * 3 + 4 * 4 -> 9 + 4 * 4 -> 9 + 16 -> 25

## Redukční krok
= úprava výrazu, při které je vybraný podvýraz nahrazen pravou stranou definice funkce P -> Q; za redukční krok považujeme také vyčíslení jednoduché operace (aritmetické, logické, ...) aplikované na jednoduché argumenty

např. square (3 * 3) -> square 9

## Redukční strategie
= který podvýraz vyberu jako další redukční krok

_Striktní redukční strategie_ (zevnitř) - nejdříve upraví argumenty a až potom aplikuje funkci

square (3 + 5) -> square 8 -> 8 * 8 -> 64

_Normální rekukční strategie_ (zvenku) - nejdříve aplikuje funkci a až potom upraví zbytek

square (3 + 5) -> (3 + 5) * (3 + 5) -> 8 * (3 + 5) -> 8 * 8 -> 64

_Líná redukční strategie_ (v Haskellu) - normální redukční strategie, která si paamtuje hodnoty upravených podvýrazů a vyhodnocuje se jen jedenkrát

square (3 + 5) -> (3 + 5) * (3 + 5) -> 8 * 8 -> 64

## Vlastnosti redukčních strategií

### Věta o perpetualitě
Jestliže se výraz zacyklí s redukční strategií X, pak se určitě zacyklí i při využití striktní redukční strategie (head [1..])

### Věta o normalizaci
Pokud pro daný výraz existuje alespoň jedna redukční strategie, při jejímž použití se úprava výrazu nezacyklí, tak se tento výraz nezacyklí ani při použití normální redukční strategie.

### Churchova-Rosserova věta
Výsledná hodnota ukončeného výpočtu nezáleží na zvolené redukční strategii: pokud výpočet skončí, je výsledek vždy stejný.

## Funkce vyšších řádů
= alespoň jeden z argumentů nebo výsledek, který funkce vrací, je opět funke (např. (+), map)

_částečná aplikace_ - všechny funkce jsou ve skutečnosti unární a můžeme je vyhodnotit i pro neúplný výčet argumentů (např. f: (*) 3 ... f 4 -> (*) 3 4 -> 12), výsledkem je funkce, tzv. _operátorová sekce_

S každou aplikací ubude jeden výskyt "->" v typu výrazu

Má-li funkce více formálních argumentů, částená aplikace probíhá vždy od parametru nejvíce vlevo. (Pokud nepoužijeme funkci flip :: (a -> b -> c) -> b -> a -> c)

Pokud chceme zabránit částečné apliakce, použijeme n-tici (funkce curry, uncurry).

## Využití funkcí vyšších řádů
- map, filter
- operátorová sekce
- akumulační seznamové funkce (foldl, foldr), pomocí kterých můžeme aplikovat pinární operaci na všechny prvky senamu navzájem; foldl (+) 0 [x_1, ..., x_n] = x_1 + ... + x_n
- tvorba _bezparametrové definice funkce_ využívá funkce flip, curry, uncurry, (.) a operátorové sekce; f x = (not . odd) x (definice s parametrem) vs. f = not . odd (bezparametrová definice)

## Lambda funkce
= nepojmenovaná funkce, která je definovaná přímo v místě jejího užití

Příklad: map (\x -> x * x + 1) [1, 2, 3, 4, 5] -> [2, 5, 10, 17, 26]

(let f x = x * x + 1 in map f [1, 2, 3, 4, 5] je ekvivalentní)

### Lambda abstrakce = vytváření lambda funkcí
1. M ≡ x * x + 1 <- M je tělo funkce
2. λ x.M ≡ λ x (x*x + 1) <- z těla vytvoříme funkci
3. λ x.M N ≡ λ x(x*x + 1) N = N * N + 1 <- při aplikaci na argument N se všechny návazné výskyty x nahrazí za argument N

Příklad: (λ x . x * x + 1) 3 = 3 * 3 + 1 = 10

## Haskell
_Zákaldní datové typy:_ Integer, Int, Float, Fractional, Char, String ([Char]), Bool

_Víceřádková definice_
one_or_two :: Integer -> Bool
one_or_two 1 = True
one_or_two 2 = True
one_ow_two _ = False

one_or_two = jméno funkce
Integer -> Bool = typová signatura

_Typový kontext_ - omezuje některé typové proměné
(==) :: Eq a => a -> a -> Bool
