## Elementární teorie čísel

- dělitelnost
- Euklidův algoritmus
- modulární operace
- prvočíselnost a její testování
- Aplikace teorie čísel
    - RSA
    - DSA
    - Lineární kódy
    - polynomiání kódy

# Dělitelnost
Celé číslo a dělí celé číslo b, právě když existuje celé číslo c takové, že platí a ∙ c = b

n | 0 („en dělí nulu“), 0 | 0, n | n

pokud a | b a zároveň b | c, pak také a | c

_největší společný dělitel_ čísel n_1, ..., n_k je číslo, které dělí všechna tato čísla a je z takových čísel největší

_nejmenší společný násobek_ čísel n_1, ..., n_k je číslo, které je násobkem každého z těchto čísel a je z takových čísel nejmenší

_nesoudělná čísla_ mají pouze jednoho společného dělitele (1)

## Pravidla dělitelnosti

dvěma: poslední číslice je dělitelná 2

třemi: ciferný součet je dělitelný 3

čtyři: poslední dvojčíslí je dělitelné 4

pěti: poslední číslice je 0 nebo 5

šesti: je dělitelné 2 a 3

sedmi: využijeme faktu, že 100 ≡ 2 (mod 7)

osmi: poslední trojčíslí je dělitelné 8

devíti: ciferný součet je dělitelný 9

deseti: poslední cifra je 0

jedenácti: součet jednotlivých dvojčíslí je dělitelný 11 / rozdíl součtu číslic na sudých a lichých pozicích je dělitelný 11

## Euklidův algoritmus
Slouží pro výpočet největšího společného dělitele (GCD).

1. větší z čísel podělíme tím menším se zbytkem
2. pokud je zbytek 0, menší z čísel je největší společný dělitel
3. jinak hledáme největšího společného dělitele menšího čísla a zbytku

Příklad: Největší společný dělitel čísel 133 a 15?

133 = 8 ∙ 15 + 13

15 = 1 ∙ 13 + 2

13 = 6 ∙ 2 + 1

2 = 2 ∙ 1 + 0

Největší společný dělitel je 1.

## Bezoutova věta
Pro libovolná celá čísla a_1, a_2 existuje jejich největší společný dělitel (a_1, a_2), přitom existují celá čísla k_1, k_2 taková, že

(a_1, a_2) = k_1 ∙ a_1 + k_2 ∙ a_2

### Výpočet Bezoutových koeficientů
Vycházím z Euklidova algoritmu.

1. vyjádřím GCD ho pomocí předpoledního řádku z Euklidova algoritmu
2. vyberu menší z obou čísel a zase ho vyjádřím pomocí koeficientů z „řádku nadtím“
3. upravím do jednoduššího tvaru a opakuji, dokud se nedostanu k původním číslům (těm, jejichž GCD jsme hledali), koeficienty u nich jsou hledané koeficienty

Příklad: Bezoutovy koeficienty pro GCD 133 a 15?

1 = 13 - 6 ∙ 2

  = 13 - 6 ∙ (15 - 1 ∙ 13)

  = 7 ∙ 13 - 6 ∙ 15

  = 7 ∙ (133 - 8 ∙ 15) - 6 ∙ 15

  = 7 ∙ 133 - 62 ∙ 15


## Kongruence

x ≡ y mod m právě tehdy, když x - y = r ∙ m, r ∈ ℕ

Dvě čísla jsou kongruentní, pokud dávají po dělení stejným číslem m týž zbytek.

- K libovolné straně kongruence můžeme přičíst násobek modula.
- K oběma stranám kongruence lze přičíst/odečíst/vynásobit/umocnit stejným přirozeným číslem.
- Obě streny kongruence můžeme podělit číslem nesoudělným s modulem.
- Jestliže kongruence platí podle mod m, platí i podle mod (m/a), kde a je dělitelem m

## Eulerova funkce φ(n)
Počet čísel mezi 1 a n nesoudělných s n.

φ(n) = n - 1 ... n je prvočíslo

n = p_1^a1 ∙ p_2^a2 ∙ ... ∙ p_k^ak ... p_i je prvočíslo

φ(n) = p_1^(a1 - 1) ∙ (p_1 - 1) ∙ ... ∙ p_k^(ak - 1) ∙ (p_k - 1)

Příklad:

6 = 2^1 ∙ 3^1

φ(6) = 2^0 ∙ (2 - 1) ∙ 3^0 ∙ (3 - 1) = 2

## Modulární umocňování x ≡ a^b (mod m)

a) Eulerova věta

Pokud (a, n) = 1, pak a^φ(m) ≡ 1 (mod m)

b) Rozklad modula na dvě nesoudělná čísla

m = m_1 ∙ m_2 a zároveň (m_1, m_2) = 1, pak kongruenci rozdělíme na dvě: x ≡ a^b (mod m_1) a x ≡ a^b (mod m_2)

c) Využití řádu

Umocňujeme základ, dokud není kongruentní s 1. Toto potom využijeme k redukci mocniny.

d) Postupné umocňování

Umocňujeme základ a redukujeme mocninu pomocí modula

! Pokud je základ větší než modul, základ modulem zmodulíme.

## Prvočíselnost
_prvočíslo_= číslo p ∈ ℕ, p > 2, že pouze 1|p a p|p

Prvočísel je nekonečně mnoho.

_složené číslo_ = číslo, které není prvočíslem.

2, 3, 5, 7, 11, 13, 17, 19, 23, 29, 31, 37, 41, 43, ...

### Testování prvočíselnosti

- postupné dělení (stačí ověřit jen čísla do √n)
- Eratosthenovo síto
- Fermanův test: pro každé prvočílo p platí, že a^(p - 1) ≡ 1 (mod p) pro každé a takové, že 0 < a < p, existují ale i neprvočísla, pro které vztah platí
- Wilsonova věta: číslo p je prvočíslo, právě když platí (p - 1)! ≡ -1 (mod p)¨

## RSA (Rivest, Shamir Adleman)
Asymetrická šifra (soukromý i veřejný klíč), která se používá pro šifrování i podepisování dokumentů.

p, q ... prvočísla; n = p ∙ q; φ(n) = (p - 1)(q - 1)

e ... veřejný klíč

d ... soukromý klíč; e ∙ d ≡ 1 (mod φ(n))

M ... zpráva

C .. šifrovaná zpráva

C = M^e (mod n)

M = C^d (mod n)

### RSA – prolomení
1. Rozložím n na součin dvou prvočísel (lze rychle jen pro malá čísla)
2. Spočítám φ(n) = (p - 1)(q - 1)
3. Řeším rovnici e ∙ d ≡ 1 (mod φ(n))
    1. Spočtu GCD(φ(n), e)
    2. Určím Bezoutovy koeficienty
    3. Vynásobím původní kongruenci koeficientem u e
    4. Na levé straně kongruence zůstane jen d
4. d dosadím do rovnice M = C^d (mod n)

## DSA (Digital Signature Algorithm)
1. Alice podepíše zprávu svým soukromým klíčem a zveřejní svůj veřený klíč.
2. Bob ověří podpis Aliciným veřejným klíčem.
    - ✓ zprávu poslala Alice.
    - ✓ zpráva nebyla změněna.

Oficiální podpisy je nutné ověřit u certifikační autority (například Česká pošta).

## (n, k)-kódy
Při přenosu informace dochází k její deformaci. Přidáme n-k bitů (n > k), abychom mohli chyby

- rozpoznávat
- opravovat

původní slovo ... 2^k možností

kódová slova ... 2^n možností

chybová slova ... 2^n - 2^k možností

_kód kontrolující paritu_ ... přidáním prvního bitu zaručíme sudý (nebo lichý, dle domluvy) počet jedniček v kódovém slově

_Hammingova vzdálenost_ dvou slov je rovna počtu bitů, ve kterých se liší.

Zpráva je polynom:

p(x) = c_0 + c_1 ∙ x^1 + c_2 ∙ x^2 + ...

101001 -> x^5 + x^3 + 1

## Lineární kódy
= Injektivní lineární zobrazení g: (ℤ_2)^k -> (ℤ_2)^n

Matice G typu n|k reprezentující zobrazení v standardních bázích se nazývá _matice kódu_.

Pro každé slovo u je v = G ∙ u příslušné kódové slovo.

Každý polynomiální (n,k)-kód je lineární kód.

_matice kontroly parity_ H

_syndrom slova u je hodnota H∙u, podle syndromu zjistím, kolik chyb nastalo.

## Polynomiální kódy
Nechť p(x) = a_0 + ... + a_(n-k) ∙ x^(n-k) ∈ ℤ_2[x] je polynom s a_0 = 1, a_(n-k) = 1. Polynomiální kód generovaný polynomem p(x) je (n, k)-kód, jehož slova jseu polynomy stupně menšího než n dělitelné p(x).

Zpráva m(x) je zakódována jako v(x) = r(x) + x^(n-k) m(x), kde r(x) je zbytek po dělení polynomu x^(n-k)m(x) polynomem p(x).

_Chybový polynom_ reprezentuje vektor chyby přenosu.

_Ireducibilní polynom_ p(n) ∈ ℤ_2[x] stupně m se nazývá _primitivní_, jestliže p(x) dělí polynom (1 + x^k) pro k = 2^n - 1, ale nedělí jej pro žádné menší k.