# Softwarové inženýrství I.
- životní cyklus software a související aktivity
- specifikace požadavků a jejich typy
- strukturované metody analýzy a návrhu
- objektově orientované metody analýzy a návrhu

## Životní cyklus software
1. specifikace požadavků
2. analýza a návrh
3. implementace
4. validace a verifikace
5. evoluce

Iniciální vývoj -> Evoluce (nová funkcionalita) -> Udržování (nepřidáváme funkcionalitu, opravujeme chyby) -> Phase-out (neudržuje se, ale užívá se)

_refactoring_ = změna struktury kódu, která vede ke zlepšení čitelnosti, nemění se funkce

_reengeneering_ = změna funkcí nebo celé technologie

_prototypování_ = ukázkové ještě nefunkční řešení

## Specifikace požadavků a jejich typy
- Popis služeb a omezení, se kterými systém pracuje a podle kterých je vyvíjen.

_funkční požadavek_ - jak by se systém měl chovat v určitých situacích

_nefunkční požadavek_ - kvalita systému, splnění omezení

_Požadavky na specifikaci:_

- konzistentí
- kompletní
- přesné
- verifikovatelné
- reálné

_Způsob specifikace_:

- přirozený jazyk
- UML
- automaty

## Struturová analýza a design
- funkce + data; funkční dekompozice
- rozdělí projekt na probné aktivity a definuje jejich interakce
- využívá hierarchické grafické techniky
- cílí na vysokou kvalitu systému

### Metody
- DeMarco: Structured Analysis and System Specification (SASS)
- Gane Sorson : Logical Modelling (LM) (kontext, ERD, DFD)
- Yourdon: Modern Structured Analysis (YMSA)
- Structured System Analysis and Design Methods (SSADM)

## Strukturová analýza

![](17/IMG_4521.JPG)

## Objektově orientovaná analýza a design
- práce se skupinou integrujících objektů
- objekt je charakterizován třídou, stavem a chováním

### Metody
- Jim Rumbaugh: Object Modeling Technique (OMT)
- Kruechten et al: Rational Unified Process (RUP)
- Booch-Jacobson-Rumbaugh: Unified Process (UP)

### Unified process:
1. Požadavky
    - use case diagram - aktéři, hranice systému, požadavky
2. Analýza 
    - diagram tříd - vztahy, ddědičnost, polymorfismus
    - diagram přehledu interakcí, diagram aktivit - realizace případů užití
3. Design
    - diagram tříd, diagram komponent - třídy, rozhraní a komponenty
    - diagram přehledu interakcí, stavový diagram - detailní realizace případů užití

## Strukturovaný vs. objektově orientovaný přístup

| | Strukturovaná analýza | Objektově orientovaná analýza |
| Metody | systém = zanořené procesy přistupující k datům | systém = interagující objekty |
| hranice systému | kontextový diagram | diagram případů užití |
| funkcionalita | data flow diagram | diagramy aktivit a interakcí |
| data | ERD | diagram tříd a objektů |
| řízení | stavový diagram | stavový diagram |

