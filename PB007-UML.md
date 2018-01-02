# Jazyk UML (Unified Modeling Language)
* 14 diagramů, každý zachycuje systém z jiné perspektivy
* **vnější pohled** -- interagce systému z okolím, vhodné pro komunikaci se zákazníkem a ujasnění požadavků
    * Diagram případů užití (Use case diagram)
* **strukturální pohled** -- vnitřní struktura systému
    * Diagram tříd (Class diagram)
    * Diagram objektů (Object diagram)
    * Diagram komponent (Component diagram)
    * Diagram balíků (Package diagram)
    * Diagram nasazení (Deployment diagram)
    * Composite structure diagram
    * (Profile diaagram)
* **interakční pohled** -- vnitřní chování systému, jak spolu komunikují jednotlivé částí
    * Sekvenční diagram (Sequence diagram)
    * Komunikační diagram (Communiacation diagram)
    * Diagram přehledu interakcí (Interaction overview diagram)
    * Diagram časování (Timing diagram)
* **perspektiva chování** -- posloupnost kroků chování
    * Diagram aktivit (Activity diagram)
    * Stavový diagram (State diagram)

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

## Diagram tříd (Class diagram)
### Analytický diagram tříd

### Návrhový diagram tříd
* obsahuje plno implementačních detailů (settery, gettery, datové typy, konstruktory,...)
* všechny vztahy musí mít šipky a násobnost na obou stranách

**agragace** -- celek a část, část může existovat bez celku, často 0..1* -> N (prázdný kosočtverec)

**kompozice** -- celek a jeho část, část nemůže existovat bez celku, často 1 -> 1 (plný kosočtverec)

**dědičnost** -- implementaci + rozhraní

**rozhraní** -- pouze rozhraní (veřejné atributy, operace a vztahy BEZ implementace)

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

## Sekvenční diagram (Sequence diagram)
* zobrazuje interakce uspořádané podle času, zdůrazňuje časovou posloupnost zasílaných zpráv

### Komponenty
* aktér
* čára života
* objekty
* fragmenty: opt [], alt
* cykly: loop, break
* paralelismus: par
* zprávy
    * synchronní -- čekám na odpověď (plná trojúehelníčková šipka)
    * asynchronní -- nečekám na odpověď (čárková šipka)
    * return -- nepovinná (čárkovaná šipka doleva)
* konstruktor <<create>>
* číslování

## Komunikační diagram (Communication diagram)
* zdůrazňuje strukturu vztahů mezi objekty
* zanořovaná čísla

## Interaction overview diagram
* modeluje mezi jednotlivými interakcemi
* má stejný syntax jako diagram aktivit, jednotlivé interakce jsou komunikační diagramy

## Časový diagram (Timing diagram)
* časové schéma
* obsahuje časovou osu