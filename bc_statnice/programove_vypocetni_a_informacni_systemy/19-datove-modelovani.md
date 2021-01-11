# Datové modelování
- návrh datových struktur
- grafické vyjádření
- převod do relačního modelu
- ER diagram
    - entity
    - atributy
    - vztahy
- UML diagram tříd
- srovnání ER diagramu a diagramu tříd

## Návrh datových struktur
_datová struktura_ = způsob uložení informací; např.: halda, prioritní fronta, vyhledávací strom, hashovací tabulka, ...

V kontextu softwarového inženýrství se datové modelování zabývá modelováním:

- datových entit,
- vztahů,
- atributů.

## ERD - Entity relationship diagram

_entita_ = cokoli, o čem chceme ukádat data

Entity jsou:

- identifikovatelné,
- potřebné,
- popsatelné svými atributy, které sdíli s entitami stejného typu.

_vztah_ = vztah mezi dvěmi (případně více) entitami, které lze reprezentovat (většinou) slovesem

_atribut_ = fakt, aspekt, vlastnost nebo detail o typu entity nebo typu relace, nemá další podčásti

Pokud je doména atributu rozsáhlá, můžeme ji brát jako typ entity.

## ERD

![](19/IMG_4541.JPG)

## Kardinalita vztahu

1 : 1 one-to-one

1 : N one-to-many

M : N many-to-many

## Asociační entita

![](19/IMG_4542.JPG)

## Proces tvorty databáze

Modelování ERD je první krok k tvorbě databáze

1. Určení účelu databáze.
2. Nalezení a organizace potřebných informací
    - Vytvoření ERD. Převod entitních typů na tabulky, atributů na sloupce, entit na řádky.
    - Převedení asociačních entit a M : N vztahů.
3. Specifikace primárních klíčů.
4. Převod do normálních forem.
5. Vylepšení návrhu
    - testování
    - odstranění chyb

## UML : diagram tříd I.

Model statické struktury systému (třídy a vztahy mezi nimi).

### Tvorba diagramu tříd

1. Slovní analýza zadání, hledání tříd.
2. Tvorba _analytického diagramu tříd_ (stručný, bez implementačních detailů).
3. Tvorba _návrhového diagramu tříd_ (obsahuje implementační detaily, např. gettery a settery)

Agregace a kompozice:

![](19/IMG_4544.JPG)

_třída_ = vzor množiny objektů, které sdílejí stejné vlastnosti (atributy) a chování (metody)

_instance_ = konkrétní objekt vytvořený na základě třídy

_dědičnost_ = hierarchický vztah, kde potomek dědí od rodiče

_asociace_ = vztah mezi instancemi daných tříd

_navigovatelnost_ udává, která třída bude obsahovat atribut druhé třídy

![](19/IMG_4545.JPG)

## Srovnání ERdiagramu a UML diagramu tříd

| ERD | Diagram tříd |
| Zachycuje pouze strukturu systému (data). | Zachycuje strukturu i chování systému. |
| Jednoduché relace (případně generalizace). | Asociace, agregace, kompozice, závislost, generalizace. |
| Mapuje se na databázové tabulky a využívá klíče a normální formy. | Mapuje se na objekty reálného světa. |
| Nemusí obsahovat všechny "třídy", kvůli jejich persistentnosti. | Obsahuje i třídy, které nejsou persistentní. |

Je běžné, že se jedna entita mapuje na více tříd, nebo se jedna třída mapuje na více entit.

