# Formální jazyky II.

- bezkontextové jazyky a jejich reprezentace
- varianty zásobníkových automatů
    - metody akceptování
    - determinismus a nedeterminismus
    - rozšířené zásobníkové automaty
- nedeterministická syntaktická analýza
- uzávěrové vlastnosti bezkontextových jazyků

## Bezkontextová gramatika

G = (N, \Sigma, P, S)

N ... neprázdná konečná množina _neterminálů_

\Sigma ... konečná množina _terminálů_; N \cap \Sigma = \emptyset, V = N \cup \Sigma

S \in N ... _počáteční neterminál_

P \subset N \times V* ... konečná množina _pravidel_

Jazyk je _bezkontextový_, pokud je generovaný nějakou bezkontextovou gramatikou.

## Redukovaná bezkontextová gramatika

- neobsahuje _nepoužitelné symboly_:
    - _nenormované symboly_ = nelze z nich vytvořit žádné slovo
    - _nedosažitelné symboly_ = nelze se do nich dostat

### Nalezení nenormovaných symbolů

1. Vytvoříme množinu neterminálů, které je možné přímo přepsat na řetězec terminálů.
2. Tuto množinu rozšiřujeme o neterminály, které se přepísí na terminály nebo neterminály, které už jsou v množině.
3. Zbylé neterminály jsou nenormované.

### Nalezení nedosažitelných symbolů (terminálů i neterminálů)

1. Vytvoříme množinu obsahující iniciální neterminál.
2. Postupně rozšiřujeme tuto množinu o neterminály dosažitelné z této množiny.
3. Zbylé terminály / neterminály jsou nedosažitelné.

## Bezkontextová gramatika bez \eps-pravidel
Množina pravidel neobsahuje žádné \eps-pravidlo, nebo obsahuje právě pravidlo S -> \eps a S se nevyskytuje na pravé straně žádného pravidla.

### Algoritmus pro odstranění \eps-pravidel

1. Vytvořím množinu neterminálů, které se po určitém počtu kroků přepíšou na \eps : N_\eps = {A \in N | A =>* \eps}.
2. Upravím všechna pravidla tak, aby pokud jejich pravá strana neobsahuje N_x \in N_\eps, tak zůstala stejná; pokud obsahuje, tak se pravidlo rozdělí na dvě: jedno původní, jedno bez N_X (případně pro všechny možné kombinace).
3. Pokud S \in N_\eps, přidám nový iniciální neterminál a dvě pravidla: S' -> S | \eps

## Bezkontextová gramatika bez jednoduchých pravidel
_jednoduché pravidlo_ : A -> B, kde A, B \in N

### Algoritmus na odstranění jednoduchých pravidel
1. Pro každý neterminál A \in N si napočítám množinu neterminálů, do kterých se dostanu pomocí jednoduchcých pravidel, tato množina vždy obsahuje neterminál A, pro který ji zrovna počítám. Jako první počítám pro iniciální neterminál.
2. Pravidla přepíšeme tak, že jednoduchá pravidla nahradíme dosazením.

## Vlastní bezkontextová gramatika

_necyklická gramatika_ neexistuje neterminál A \in N takový, že by se po určitém nenulovém počtu kroků přepsal sám na sebe A =>^+ A

_vlastní gramatika_ je:

- bez nepoužitelných symbolů
- bez \eps-pravidel
- necyklická

Ke každém neprázdnému bezkontextovému jazyku existuje vlastní bezkontexová gramatika, která jej generuje.

## Chomského normální forma
- bez \eps-pravidel
- každé pravidlo ve tvaru
    - A -> BC, kde B,C \in N
    - A -> a, kde a \in \Sigma
    - S -> \eps

### Algoritmus převodu do Chomského normální formy
1. Gramatiku převedeme na vlastní.
2. Odstraníme jednoduchá pravidla.
3. Pravidla nežádoucího tvaru upravíme tak, že delší pravidla skrátíme vytvořením nového neterminálu představujícího řetězec původních neterminálů a přidání pravidel pro nový neterminál.

## Gramatika bez levé rekruze
Neterminál A je _levorekurzivní_, pokud existuje derivace A =>^+ A\beta

### Algoritmus pro odstranění přímé levé rekurze
1. Ke každému neterminálu a jeho pravidlům s leverou rekurzí:

    A -> A\alpha_1 | ... | A\alpha_m | \beta_1 | ... | \beta_n

    Vytvoříme nová pravidla

    A -> \beta_1 | ... | \beta_n | \beta_1A' | ... | \beta_nA'
    A' -> \alpha_1 | ... | \alpha_m | \alpha_1A' | \alpha_mA'

### Algoritmus pro odstranění přímé levé rekurze
1. Zvolíme uspořádání neterminálů a aplikujeme substituci a odstranění přímé levé rekurze v pořadí „shora dolů“ na zpětné hrany

## Greibachové normální forma
- bez \eps-pravidel (s výjimkou S -> \eps)
- každé pravidlo tvaru:
    - A -> a\alpha, kde a \in \Sigma a \alpha \in N*
    - S -> \eps

## Zásobníkový automat

M = (Q, \Sigma, \Gamma, \delta, q_0, Z_0, F)

Q ... konečná množina _stavů_

\Sigma ... konečná _vstupní abeceda_

\Gamma ... konečná _zásobníková abeceda_

\delta : Q \times (\Sigma \cup {\eps}) \times \Gamma -> P_Fin(Q \times \Gamma*) ... parciální _přechodová funkce_

q_0 \in Q ... počáteční stav

Z_0 \in \Gamma ... počáteční symbol na zásobníku

F \subset Q ... množina koncových stavů

## Výpočet zásobníkového automatu

_konfigurace_ = libovolný prvek (p, \omega, \alpha) \in Q \times \Sigma* \times \Gamma*

_krok výpočtu_ \leftt_M = binární relace: (p, a\omega, Z\alpha) \leftt_M (q, \omega, \gamma\alpha) \equiv \exists (q, \gamma) \in \delta(p, a, Z) pro a \in \Sigma \cup {\eps}

\leftt^* je tranzitivní uzávěr nad \leftt

Jazyk akceptovaný _koncovým stavem_:

L(M) = {w \in \Sigma* | (q_0, w, Z_0) \leftt^* (q_f, \eps, \alpha), kde q_f \in F, \alpha \in \Gamma*}

Jazyk akceptovaný _prázdným zásobníkem_:

L_e(M) = {w \in \Sigma* | (q_0, w, Z_0) \leftt^* (q, \eps, \eps), kde q \in Q}

Při neformální grafické reprezentaci zásobníkového automatu reprezentují uzly jednotlivé konfigurace.

## Deterministický zásobníkový automat

M = (Q, \Sigma, \Gamma, \delta, q_0, Z_0, F)

M je deterministický, pokud:

- pro všechna q \in Q a Z \in \Gamma platí: kdykoliv \delta(q, \eps, Z) \neq \emptyset, pak \delta(q, a, Z) = \emptyset pro všechna a \in \Sigma (když je přechod pod \eps, pak není žádný přechod pod a)
- pro žádné q \in Q, Z \in \Gamma a a \in \Sigma \cup {\eps} neobsahuje \delta(q, a, Z) více než jeden prvek.

Jazyk je deterministický bezkontextový, pokud existuje deterministický zásobníkový automat, který ho akceptuje koncovým stavem.

## Rozšířený zásobníkový automat

R = (Q, \Sigma, \Gamma, \delta, q_0, Z_0, F)

od zásobníkového automatu se liší pouze definice \delta.

\delta : Q \times (\Sigma \cup {\eps}) \times \Gamma* -> P_Fin(Q \times \Gamma*)

krok výpočtu \leftt_R

(p, aw, \gamma_2\alpha) \leftt_R (q, w, \gamma_2\alpha) \equiv \exists (q, \gamma_2) \in \delta(p, a, \gamma_1) pro a \in \Sigma \cup {\eps}

Ke každému rozšířenému PDA existuje ekvivalentní PDA.

## Nedeterministická statická analýza
- Generuje bezkontextová gramatika dané slova?
- Budujeme derivační strom pro slovo, rozvýjíme vždy nejlevější neterminál.

### Shora dolů
1. Vytvoříme dvojici (slovo, iniciální neterminál) a iniciální neterminál postupně přepipsujeme podle pravidel.
2. Pokud oba prvky dvojice začínají stejným terminálem, odstraníme ho u obou (aba, aSA) \leftt^a (ba, SA)
3. Pokud nám zůstane dvojice (\eps, \eps), tak je slovo generováno příslušnou gramatikou.

### Zdola nahoru
1. Vytvořím trojici (stav, slovo, \bot)
2. Postupně načítám písmena zleva ze slova a přidávám je zprava do zásobníku (za \bot)
3. Když můžu, přepíšu symboly vpravo od \bot na nějaký neterminál (v takovém případě čty \eps)
4. Snažím se vyprázdnit zásobník (dostat se do akceptujícího stavu a načíst celé slovo).

CYK (Cock-Younger-Kasami) je deterministický algoritmus sloužící k rozhodnutí, zda gramatika slovo w generuje, který má složitost \O(|w|^3)

## Uzávěrové vlastnosti bezkontextových jazyků

CFL jsou uzavřené na:
- sjednocení
- průnik s regulárním jazykem
- zřetězení
- iterace (i pozitivní)

CFL nejsou uzavřené na:
- průnik
- doplněk

DCFL jsou uzavřené na:
- doplněk
- průnik s regulárním jazykem

DCFL nejsou uzavřené na:
- průnik
- sjednocení