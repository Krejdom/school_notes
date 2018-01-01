# Jazyk UML
* 14 diagramů, každý zachycuje systém z jiné perspektivy
* **vnější pohled** -- interagce systému z okolím, vhodné pro komunikaci se zákazníkem a ujasnění požadavků
    * diagram případu užití
* **strukturální pohled** -- vnitřní struktura systému
    * diagram tříd
    * diagram objektů
    * diagram komponent
    * diagram balíků
    * diagram nasazení
    * Composite structure diagram
* **interakční pohled** -- vnitřní chování systému, jak spolu komunikují jednotlivé částí
    * sekvenční diagram
    * komunikační diagram
    * interakční diagram
    * timing diagram
* **perspektiva chování** -- posloupnost kroků chování
    * diagram aktivit
    * stavový diagram

## Diagram případu užití (Use case diagram)
Diagram případu užítí zachycuje hranice systému.

* Nerozkreslujeme ho příliš do detailů.
* Diagram by měl být srozumitelný.
* Před tvorbou diagramu specifikujeme funkční požadavky.

**funkční požadavek**

### Komponenty
* **hranice systému** -- odděluje vnitřní a vnější prostředí systému,
* **případ užit** (use case) -- funkcionalita systému; pojmenováme je slovensnou vazbou,
* **akter** -- uživatelé, vnější zařízení, čas; jeden aktér může reprezentovat více fyzických osob, jedna osoba se může mapovat na více aktérů, více aktérů může mít stejné jméno (pokud to zvýší přehlednost), rozlišujeme dva druhy aktérů (ale v diagramu rozlišeni nejsou):
    * *primární aktér* -- spouští případ užití (např. student se přihlásí do kurzu),
    * *sekundární aktér* -- interaguje s případem užití (např. systém notifikuje učitele o naplnění kurzu)
* **textový scénář případu užití** -- obsahuje rozepsané informace o případu užití
    * jméno,
    * id,
    * popis,
    * aktéři,
    * precodnition,
    * postup,
    * alternativní scénář -- narušení scénáře nenadálou situací,
    * postcondition.

* Komunikace probíhá pouze uvnitř systému nebo mezi aktérem a vnitřkem systému, nikoli vně systému.

### Speciální vztahy

**include** -- funcionalita, která je obsažena ve více případech užití (neduplikujeme ji); A → B = "A obsahuje B"

**extend** -- funcionalita, která je v případu užití volitelná (+ podmínka, kdy může nastat ono rozšíření); A ← B = "A je rozšířeno B"

**generalizace mezi aktéry** -- dědičnost mezi aktéry

**generalizace mezi případy užití**

## Diagram aktivit (Activity diagram)
* zachycuje procesy v systému jako posloupnost událostí
* z/do aktivit vede pouze jedna šipka
* hodí se i pro upřesnění naprogramování funkce (do aktivit můžu vpisovat i pseudokód apod.)

### Komponenty
* **začátek** -- plné kolečko
* **aktivita** (akce) -- obdélník se zakulacenými rohy
* **kontrolní body** -- kosočtverec znázorňuje podmínku; tlusté vodorovné čáry znázorňují paralelní běh
* **control flow** -- čáry
* **plavecká dráha** (swim line) -- rozdělení na různé logické oblasti (např. podle toho, kdo onu část zpracovává)
* **konec** -- dvojté plné kolečko

... 3. přednáška ...

## Diagram tříd (Class diagram)
...

## Stavový diagram (State diagram)
* zachycuje chování určitého objektu (elementu) v systému (jeho životní etapy)
* např. žárovka: vypnutá, zapnutá, vyhořelá
* dva typy:
    * behavoriální -- chování objektu
    * protokolové -- protokol, v jakém pořadí volat např. nějaké metody

### Komponenty
* **stav** -- zaoblený obdélník, uvnitř stavu mohu provádět různé akce (vstupní, výstupní, vnitřní přechody, interní aktivita)
    * iniciální stav -- vyplněné kolečko
    * koncový stav -- dvojté vyplněné kolečko
    * složený stav -- např. kniha může být vypůjčená nebo nevypůjčená a zároveň rezervovaná nebo nerezervovaná
* **přechod** -- událost [podmínka] / akce
* **událost**
    * volání (call event)
    * signál (signal event)
    * změna (change event)
    * čas (time event)
* případně je možné použít i větvení podobně jako v diagramu aktivit
