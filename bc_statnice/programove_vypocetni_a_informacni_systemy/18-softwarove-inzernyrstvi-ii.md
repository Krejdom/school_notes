# Softwarové inženýrství II.
- testování
- verifikace
- validace
- provoz, údržba a další vývoj systému
- role jezyka UML v podpoře analýzy a návrhu software

## Testování
- Cílem je ověřit, jestli program dělá to, co má a jestli to dělá správně.
- Umí potvrdit přítomnost chyb, nikoli dokázat jejich absenci.
- Testování se snažíme automatizovat kvůli ceně.

### Testování nefuknčních vlastností
- Testování výkonu
    - testuje výkon a spolehlivost
    - postupně zvyšuje reálnou zátěž, dokud je systém použitelný
    - stress testing - dokud se systém nezhroutí
- Testování spolehlivosti
    - simuluje předopkládané užívání systému
- Testování bezpečnosti
    - testování proti známým útokům, hledání slabých míst, analýza systému (password checkery), formální verifikace

### Testovací strategie
- částečné testování = testujeme pouze několik reprezentativních vzorků
- testování podle guidelines - testujeme podle pokynů, které byly určeny na základě předchozích zkušeností
    - vygenerování všech chybových hlášek
    - přetížit systém (přetečení bufferu)
    - spuštění testů se stejným vstupem několikrát
    - vynucení nevalidních výstupů
    - vynucení příliš malých/velkých výstupů

### Test-driven development (TDD)
= agilní metodika, při které nejdřív píšu testy a až potom kód

Pozitiva:
- stoprocentní pokrytí testy
- regression testing - zmna v kódu něco nepokazí
- zjednodušené debuggování
- testy jsou jistým způsobem dokumentace

### Fáze testování
1. development testing - v průběhu vývoje
    - unit testing - testování individuálních částí
    - component testing - testování, jestli funkcionalita odpovídá rozhraní
    - system testing - testování systému jako celku
2. release testing - před zveřejěním (výkonost)
3. user testing - testování potenciálními uživateli
    - alfa testování - uživetelé spolupracují s vývojáři
    - beta testování - sw je zveřejněn, uživatelé hlásí chyby
    - A/B testování - nasadí se dvě odlišné verze produktu
    - acceptance testing - zákazních schválí produkt při převzetí

## Verifikace
= ověření, že vytváříme produkt správně

_statická verifikace_ - hledáme chyby v kódu, aniž bychom ho spustili

_dynamická verifikace_ - spouštíme systém a díváme se, jestli nedělá něco, co nemá

_formální verifikace_ - systém mám reprezentovaný formálně (např. pomocí automatů), technika je např. model checking, symbolická exekuce a další

_statická analýza_ = analýzou kódu, který nemusí být kompletní a nmusíme ho spouštět, můžeme ji využít k verifikace, optimalizaci, ...
    - chyby typické pro daný jazyk
    - chyby definované uživatelem
    - asserty

## Validace
= ověření, jestli vytváříme správný produkt

_testování validace_ - jestli sw splňuje požadavky (alespoň jeden test pro každý požadavek)

Systém musí splňovat požadavky na:

- bezpečnost
- spolehlivost
- výkonnost

## Fáze vývoje software
Specifikace požadavků -> analýza -> návrh

1. Iniciální vývoj = produkt není hotový, vyvíjíme ho; následuje validace, verifikace, testování
2. Evoluce = Přidání nových funkcí, oprava chyb.
3. Údržba = Pouze oprava chyb.
4. Phase-out = Systém je využíván, ale nepřidáváme nové funkce ani neopravujeme chyby.

## Údržba software
= úprav software poté, co byl zveřejněn

- využívá se především u software na zakázku, běžný software využívá nové verze (releases).
- většinou nezahrnuje větší zásahy do architektury
- modifikujeme existující komponenty a přidáváme nové

_Typy údržby:_

- oprava chyb
- přizpůsobení jinému/novému systému
- vývoj - přidání nových funkcionalit

_refaktovorání_ - zlepšení struktury, složitosti, čitelnosti (nepřidává novou funkcionalitu)

_reengineering_ = změna funkcionality nebo technologie

Náklady na údržbu bývají až dvacetkrát výšší, než náklady na vývoj.

## Role jazyka UML v podpoře analýzy a návrhu software
- UML je nástroj pro _modelování systému._
- Pomocí _grafické notace_ vytváříme _abstraktní model systému_, který reprezentuje _různé pohledy_ na systém.
- Pomáhá _porozumět funkcionalitě_ a při _komunikaci se zákazníkem._

### Perspektivy UML:
- Vnější pohled: diagram případů užití
- Strukturální pohled: diagram tříd, diagram balíků, diagram objektů, diagram komponent, diagram nasazení, compozite structure diagram, (profile diagram)
- Interakční pohled: sekvenční diagram, komunikační diagram, diagram přehledu interakcí, diagram časování
- Perspektiva chování: diagram aktivit, stavový diagram

### Diagram případů užití (use case diagram)
- grafické znázornění požadavků na systém
- definuje pohled na systém zvenku
- interakce uživatele se systémem

![](18/IMG_4534.JPG)

### Diagram tříd (class diagram)
- třídy objektů a asociace mezi nimi
- analytický (stručný) a návrhový (včetně implementačních detailů)

![](18/IMG_4535.JPG)

### Sekvenční diagram (sequence diagram)
- interakce mezi akteéry a systémem a mezi systémovými komponentami

![](18/IMG_4536.JPG)

### Diagram aktivit
- zachycuje procesy v systému jako posloupnosti událostí

![](18/IMG_4537.JPG)

