# Grafové problémy
- ohodnocené grafy
- definice nejkratší cesty
- minimální kostra grafu
- algorimy pro hledání nejkratších cest
    - Dijkstra
    - Bellman-Ford
- algoritmy pro hledání minimální kostry grafu

## Ohodnocené grafy

_vážený (ohodnocený) graf_ = graf G spolu s ohodnocením hran reálnými čísly w: E(G) -> R

_kladně vážený graf_ = w(e) > 0 pro všechny hrany e

_vážená vzdálenost_ mezi dvěma vrcholy v grafu je minimální z cest, které začínají a končí mezi těmito vrcholy

d_G^w(u, v) = min{d_G^w(P) : P je cena cesty z u do v}

_vážená délka_ = d_G^w = Σ_{e ∈ E(P)} w(e) součet ohodnocení hran, které nálež cestě P

## Dijkstrův algoritmus
Hledání nejkratší cesty mezi dvěma vrcholy v kladně váženém grafu (souvislém).

1. Vložíme počáteční vrchol do prioritní fronty a nastavíme mu vzdálenost 0.
2. Dokud není fronta prázdná:
    1. Vybereme vrchol, jehož vzdálenost od počátku je nejmenší a odebereme ho z úschovny
    2. Pokud je tento vrchol cílovým vrcholem, skončíme.
    3. Pro všechny hrany vycházející z tohoto vrcholu, buď doplníme sousední vrchol do fronty (pokud tam ještě není), se vzdáleností počítanou přes aktuální vrchol, nebo pokud je vzdálensost přes aktuální vrchol kratší, přepočítáme ji a nahradíme.

Složitost algoritmu záleží na použité implementaci prioritní fronty.

## Bellmanův-Fordův algoritmus
Hledání nejrakší cesty mezi dvěma vrcholy nebo detekce záporného cyklu.

1. Iniciálnímu vrcholu nataví vzdálenost 0, ostatním nekonečno.
2. Postupně procházíme všechny vrholy a pro každou hranu, která vychází z vrcholu, aktualizujeme vzdálenost do sousedních vrcholů.
3. Bod 2 opakujeme, dokud se nám ve dvou po sobě jdoucích iteracích nezmění žádná vzdálenost.

## Minimální kostra grafu
_problém minimální kostry_ (MST) ve váženém souvislém grafu (G, w) hledá kostru T ⊂ G s nejmenší možnou vahou (přes všechny kostry G)

_Algoritmy řešící MST:

- Kruskalův algoritmus
- Jarníkův (Primův) algoritmus
- Borůvkův algoritmus

### Kruskalův algoritmus
Hladové hledání minimální kostry grafu.

1. Seřadíme všechny hrany grafu od nejmenší po největší w(e_1) ≤ w(e_2) ≤ w(e_3)
2. Inicializujeme prázdnou kostru.
3. Od nejmenší ohodnocené hray přidáváme hrany do kostry, pokud by přidáním nevznikla kružnice.

### Jarníkův (Primův) algoritmus
Hledání minimální kostry grafu (souvislý, vážený).

1. Vybereme libovolný počáteční vrchol a vložíme jej do úschovny U <- {(u, Ø)} a do kostry T <- (V(G, Ø))
2. Dokud úschovna není prázdná, opakujeme:
    1. Zvolíme vrchol z úschovny, jehož ohodnocení vzdálenosti je minimální (w(Ø) = 0) a odstraníme ho z úschovny.
    2. Přidáme hranu do tohoto vrcholu do kostry.
    3. Pokud z tohoto vrcholu vede kratší cesta do některého vrcholu v úschovně, nahradíme ji.

## Borůvkův algoritmus
Hledání minimální kostry grafu.

1. Každý vrchol představuje jednu komponentu souvislosti.
2. Dokud neexistuje pouze jedna komponenta souvislosti:
    1. Pro každou komponentu vybereme hranu s co nejmenším ohodnocením, která vede do jiné komponenty souvislosti (takže spojí tyto dvě komponenty).