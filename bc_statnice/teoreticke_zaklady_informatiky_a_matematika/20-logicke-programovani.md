# Logické programování
- logické progrmovací paradigma
    - princip výpočtu
    - unifikace
    - výpočetní stromy
    - dotazy
    - volné proměnné
- schopnost elementárního programování v Prologu

## Logické programovací pardigma
- _Deklarativní_ programovací paradigma (co se má dělat -- vs. imperativní = jak se to má dělat)
- Mechanická _dedukce nových informací_ na základě uvedených _údajů_ a jejich vzájemných _vztahů._
- Výpočet odpovídá logickému dokazování (sporem).
- Prolog (třešinička na dortu neimperativního programování)
- Využití v umělé inteligenci.

_program_ = databáze pravidel a faktů + cíl

_výpočet_ = dokazování cíle pomocí unifikace a SLD rezoluce

_výsledek_ = pravda/nepravda/seznam hodnot volných proměnných

## Princip výpočtu: kódování
_Hornovy klauzule:_

Fakta: pocasi(prsi). a. rodice(matka, otec).

Pravidla: stav(mokro) :- pocasi(prsi).

Cíl: ?-stav(mokro). ?-stav(X).

_termy_ = konstanta, proměnná, nebo funkce, jejíž argumenty jsou termy

Termy jsou základní stavební jednotkou Prology:

- atomy: 'pepa_1', pepa, '2'
- čísla, 2, 5
- proměnné: X
- strukturované termy - funktor následovaný sekvencí (má danou aritu)  argumentů (termů) v závorkách : pocasi(prsi)

## Unifikace =
Dva termy jsou _unifikovatelné_, pokud jsou stejné (a=a), nebo je možné zvolit hodnoty proměnných použitých v unifikovaných termech tak, aby po dosazení hodnot byly termy identické.

neunifikace \=

### Algoritmus
1. Pokud jsou t1 a t2 konstanty a jsou shodné, unifikují se.
2. Pokud t1 proměnná a t2 term, unifikují se, t1 je instanciované hodnotou t2 (a naopak).
3. Pokud t1 a t2 jsou strukturované termy, unifikují se pokud mají stejný funktor i aritu a všechny korespondující páry argumentů se unifikují a všechny instanciace proměnných z vnořených unifikací jsou kompatibilní.

## Princip výpočtu: SLD strom
- Při výpočtu se konstruuje a prochází SLD (selektivní lineární definitní rezoluce) strom.
- Fakta se používají v pořadí, v jakém jsou uvedena.

### Konstrukce výpočetního stromu:
1. Prohledávání databáze faktů pro první podcíl.
2. Vytvoření nového vrcholu pro vyhovující položku.
3. Unifikace prvního podcíle s hlavou nalezené položky.
4. Na hranu zapisujeme unifikační přiřazení/čerstvou proměnnou.
5. Prázdný list znamená úspěch.
6. Pokud nenalzneme vyhovující položku, vytvoříme list "fail".

DFS! pravá rekurze! nejdřív fakta, potom pravidla

Dokazujeme neplatnost požadovaného tvrzení - sporem.

## Řezy !/O
- Vždy jako podcíl uspěje.
- Prořezává výpočetní strom -> zrychluje výpočet.
- Pokud se narazí v těle pravidla na !, ostatní fakta a pravidla se pro právě řešený cíl neberou potaz = UPNUTÍ
- Pokud se narazí v těle pravidla na operátor !, všechny unifikace vyplývající z podcílů vyskytuících se v těle pravidla před operátorem ! se fixují = PROŘEZÁNÍ

_zelené řezy_ = množina řešení po odstranění řezu je shocné (čistě z důvodu optimalizace)

_červené řezy_ = po odstranění řezu je možno najít jiné další řešení (nedoporučuje se používat)

## Prolog

- není korektní otec(X) = X
- není úplný (cyklí)

man(heno).
informatik(heno).
chytry(heno).
idealman(X) :- man(X), informatik(X), chytry(X).

?- idealman(X). -> X = heno.

seznamy: [a, b, c]

[a, b, c] = [H|T] -> H = a, T = [b, c]

_anonymní proměnná_ - značíme podtržítkem

?- length([a, b, c], X).
X = 3.

?- islist([a, b, c]).
true.

member(X, [X|_]).
member(X, [_|T]) :- member(X, T).

