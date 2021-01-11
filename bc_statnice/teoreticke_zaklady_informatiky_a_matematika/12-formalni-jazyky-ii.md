# Formální jazyky II.

- bezkontextové jazyky a jejich reprezentace
- varianty zásobníkových automatů
    - metody akceptování
    - determinismus a nedeterminismus
    - rozšířené zásobníkové automaty
- nedeterministická syntaktická analýza
- uzávěrové vlastnosti bezkontextových jazyků

## Bezkontextová gramatika

G = (N, Σ, P, S)

N ... neprázdná konečná množina _neterminálů_

Σ ... konečná množina _terminálů_; N ∩ Σ = Ø, V = N ∪ Σ

S ∈ N ... _počáteční neterminál_

P ⊂ N × V* ... konečná množina _pravidel_

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

## Bezkontextová gramatika bez ϵ-pravidel
Množina pravidel neobsahuje žádné ϵ-pravidlo, nebo obsahuje právě pravidlo S -> ϵ a S se nevyskytuje na pravé straně žádného pravidla.

### Algoritmus pro odstranění ϵ-pravidel

1. Vytvořím množinu neterminálů, které se po určitém počtu kroků přepíšou na ϵ : N_ϵ = {A ∈ N | A =>* ϵ}.
2. Upravím všechna pravidla tak, aby pokud jejich pravá strana neobsahuje N_x ∈ N_ϵ, tak zůstala stejná; pokud obsahuje, tak se pravidlo rozdělí na dvě: jedno původní, jedno bez N_X (případně pro všechny možné kombinace).
3. Pokud S ∈ N_ϵ, přidám nový iniciální neterminál a dvě pravidla: S' -> S | ϵ

## Bezkontextová gramatika bez jednoduchých pravidel
_jednoduché pravidlo_ : A -> B, kde A, B ∈ N

### Algoritmus na odstranění jednoduchých pravidel
1. Pro každý neterminál A ∈ N si napočítám množinu neterminálů, do kterých se dostanu pomocí jednoduchcých pravidel, tato množina vždy obsahuje neterminál A, pro který ji zrovna počítám. Jako první počítám pro iniciální neterminál.
2. Pravidla přepíšeme tak, že jednoduchá pravidla nahradíme dosazením.

## Vlastní bezkontextová gramatika

_necyklická gramatika_ neexistuje neterminál A ∈ N takový, že by se po určitém nenulovém počtu kroků přepsal sám na sebe A =>^+ A

_vlastní gramatika_ je:

- bez nepoužitelných symbolů
- bez ϵ-pravidel
- necyklická

Ke každém neprázdnému bezkontextovému jazyku existuje vlastní bezkontexová gramatika, která jej generuje.

## Chomského normální forma
- bez ϵ-pravidel
- každé pravidlo ve tvaru
    - A -> BC, kde B,C ∈ N
    - A -> a, kde a ∈ Σ
    - S -> ϵ

### Algoritmus převodu do Chomského normální formy
1. Gramatiku převedeme na vlastní.
2. Odstraníme jednoduchá pravidla.
3. Pravidla nežádoucího tvaru upravíme tak, že delší pravidla skrátíme vytvořením nového neterminálu představujícího řetězec původních neterminálů a přidání pravidel pro nový neterminál.

## Gramatika bez levé rekruze
Neterminál A je _levorekurzivní_, pokud existuje derivace A =>^+ Aβ

### Algoritmus pro odstranění přímé levé rekurze
1. Ke každému neterminálu a jeho pravidlům s leverou rekurzí:

    A -> Aα_1 | ... | Aα_m | β_1 | ... | β_n

    Vytvoříme nová pravidla

    A -> β_1 | ... | β_n | β_1A' | ... | β_nA'
    A' -> α_1 | ... | α_m | α_1A' | α_mA'

### Algoritmus pro odstranění přímé levé rekurze
1. Zvolíme uspořádání neterminálů a aplikujeme substituci a odstranění přímé levé rekurze v pořadí „shora dolů“ na zpětné hrany

## Greibachové normální forma
- bez ϵ-pravidel (s výjimkou S -> ϵ)
- každé pravidlo tvaru:
    - A -> aα, kde a ∈ Σ a α ∈ N*
    - S -> ϵ

## Zásobníkový automat

M = (Q, Σ, Γ, δ, q_0, Z_0, F)

Q ... konečná množina _stavů_

Σ ... konečná _vstupní abeceda_

Γ ... konečná _zásobníková abeceda_

δ : Q × (Σ ∪ {ϵ}) × Γ -> P_Fin(Q × Γ*) ... parciální _přechodová funkce_

q_0 ∈ Q ... počáteční stav

Z_0 ∈ Γ ... počáteční symbol na zásobníku

F ⊂ Q ... množina koncových stavů

## Výpočet zásobníkového automatu

_konfigurace_ = libovolný prvek (p, ω, α) ∈ Q × Σ* × Γ*

_krok výpočtu_ ⊢_M = binární relace: (p, aω, Zα) ⊢_M (q, ω, γα) ≡ ∃ (q, γ) ∈ δ(p, a, Z) pro a ∈ Σ ∪ {ϵ}

⊢^* je tranzitivní uzávěr nad ⊢

Jazyk akceptovaný _koncovým stavem_:

L(M) = {w ∈ Σ* | (q_0, w, Z_0) ⊢^* (q_f, ϵ, α), kde q_f ∈ F, α ∈ Γ*}

Jazyk akceptovaný _prázdným zásobníkem_:

L_e(M) = {w ∈ Σ* | (q_0, w, Z_0) ⊢^* (q, ϵ, ϵ), kde q ∈ Q}

Při neformální grafické reprezentaci zásobníkového automatu reprezentují uzly jednotlivé konfigurace.

## Deterministický zásobníkový automat

M = (Q, Σ, Γ, δ, q_0, Z_0, F)

M je deterministický, pokud:

- pro všechna q ∈ Q a Z ∈ Γ platí: kdykoliv δ(q, ϵ, Z) ≠ Ø, pak δ(q, a, Z) = Ø pro všechna a ∈ Σ (když je přechod pod ϵ, pak není žádný přechod pod a)
- pro žádné q ∈ Q, Z ∈ Γ a a ∈ Σ ∪ {ϵ} neobsahuje δ(q, a, Z) více než jeden prvek.

Jazyk je deterministický bezkontextový, pokud existuje deterministický zásobníkový automat, který ho akceptuje koncovým stavem.

## Rozšířený zásobníkový automat

R = (Q, Σ, Γ, δ, q_0, Z_0, F)

od zásobníkového automatu se liší pouze definice δ.

δ : Q × (Σ ∪ {ϵ}) × Γ* -> P_Fin(Q × Γ*)

krok výpočtu ⊢_R

(p, aw, γ_2α) ⊢_R (q, w, γ_2α) ≡ ∃ (q, γ_2) ∈ δ(p, a, γ_1) pro a ∈ Σ ∪ {ϵ}

Ke každému rozšířenému PDA existuje ekvivalentní PDA.

## Nedeterministická statická analýza
- Generuje bezkontextová gramatika dané slova?
- Budujeme derivační strom pro slovo, rozvýjíme vždy nejlevější neterminál.

### Shora dolů
1. Vytvoříme dvojici (slovo, iniciální neterminál) a iniciální neterminál postupně přepipsujeme podle pravidel.
2. Pokud oba prvky dvojice začínají stejným terminálem, odstraníme ho u obou (aba, aSA) ⊢^a (ba, SA)
3. Pokud nám zůstane dvojice (ϵ, ϵ), tak je slovo generováno příslušnou gramatikou.

### Zdola nahoru
1. Vytvořím trojici (stav, slovo, ⊥)
2. Postupně načítám písmena zleva ze slova a přidávám je zprava do zásobníku (za ⊥)
3. Když můžu, přepíšu symboly vpravo od ⊥ na nějaký neterminál (v takovém případě čty ϵ)
4. Snažím se vyprázdnit zásobník (dostat se do akceptujícího stavu a načíst celé slovo).

CYK (Cock-Younger-Kasami) je deterministický algoritmus sloužící k rozhodnutí, zda gramatika slovo w generuje, který má složitost O(|w|^3)

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