# Databáze II.
- funkční závislosti
- normální formy
    - 1. NF
    - 2. NF
    - 3. NF
    - Boyce-Codddova NF
- vztahy mezi normálními formami
- dekompozice relačních schémat
- normalizace schématu

## Funkční závislosti
= hodnota určité množiny atributů jednoznačně určuje hodnotu jiné množiny atributů

R...relační schéma, \alpha \subset R, \beta \subset R : \alpha -> \beta je funkční závislost pokud t_1[\alpha] = t_2[\alpha] \implies t_1[\beta] = \t_2[\beta]

_triviální funkční závislost_ : X \subset Y, Y -> X

_superklíč_ relace R je K, pokud K -> R

_kandidátní klíč_ relace R je K, pokud platí K -> R a \alpha \properSubset K, \alpha -> R

Funkční závislosti využíváme k testování relace nebo specifikace omezení.

_úplná funkční závislost_ : X -> Y, kde Y není závislé na jiné podmnožině X (částečně závislý)

## Armstrongovy axiomy
- reflexivita
    - \beta \subset \alpha -> \alpha -> \beta
- rozšíření
    - \alpha -> \beta \implies \alpha, \gamma -> \beta, \gamma
- tranzitivita
    - \alpha -> \beta a \beta -> \gamma \implies \alpha -> \gamma

## 1. normální forma
- všechny atributy jsou atomické

![](10/IMG_4442.JPG)

## 2. normální forma
- splňuje 1. normální formu
- pro každý atribut platí buď:
    - atribut je součástí kandidátního klíče
    - není částečně závily na kandidátním klíči

![](10/IMG_4443.JPG)

## 3. normální forma
- splňuje 1. a 2. normální formu
- pro každý atribut platí jedno z následujících:
    - atribut je součástí kandidátního klíče
    - atribut není tranzitivně závisly na superklíči

![](10/IMG_4444.JPG)

## Boyce-Coddova normální forma
- splňuje 1., 2. a 3. normální formu
- pro každou závislost \alpha -> \beta, \alpha \subset R, \beta \subset R platí alespoň jedno z následujících:
    - \alpha -> \beta je triviální závislost (\beta \subset \alpha)
    - \alpha je superklíč

![](10/IMG_4445.JPG)

## Vztahy mezi normálními formami

BCNF \properSuperset 3NF \properSuperset 2NF \properSuperset 1NF

třída relací X je vlastní podmnožinou třídy relací Y (X \properSuperset Y . X \neq Y)

BCNF nemusí na rozdíl od ostatních zachovávat funkční závislosti.

Vždy existuje pevod do 3NF takový, že je bezztrátový a zachová funkční závislosti (který využívá dekompozici).

## Dekompozice relačních schémat
= rozklad na více relačních schémat

### Bezztrátová dekompozice
- všechny atributy původních schématu se objeví i v rozkladu.
- R = R_1 \cup R_2, \Phi_A,B(r) \motylek \Phi_B,C(r)

### Dekompozice zachovávající funkční závislosti
- sjednocení všech funkčních závislostí z dekomponovaných schémat dá původní funkční závislosti originálního schématu
- pokud ne, musíme relace při každé modifikaci spojit \motylek a ověriž platnost závislostí

## Normalizace
- proces dekompozice a reorganizace relačního schématu tak, aaby se s ním lépe pracovalo
    - omezení redundance
    - zlepšení konzistence
- nevede k navýšení výkonu databáze
- neexistuje jen jedno správné řešení

### Normální formy
- 1. NF - atributy jsou atomické
- 2. NF - neklíčové atributy jsou závislé (plně) na každém klíči
- 3. NF - neklíčové atributy jsou vzájemně nezávislé
- BCNF - atributy primárního klíče jsou vzájemně nezávislé