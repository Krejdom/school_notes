# Síťové aplikace a bezpečnost I.
- základní aplikační protokoly
    - doručování pošty
    - přenos souborů
    - web
    - jmenná služba
- principy popisu a zajištění kvality služby
- použití pro multimédia

## Doručování pošty

### SMTP (simple message transfer protocol)
- standardní mechanismus pro posílání elektronické pošty
- struktura SMTP emulované zprávy:
    - obálka - adresa odesílatele, adresa příjemce, ...
    - zpráva
        - hlavička - odesílatel, příjemce, předmět
        - tělo zprávy - vlastní přenášená zpráva

_emailová adresa:_ lokalni-cast@domenova.cast

![](15/IMG_4494.JPG)

## Přenos souborů

### FTP (file transfer protocol)
- standardní mechanismus Internetu pro přenos souborů mezi uzly
- ustanovuje dvě samostatná TCP spojení:
    - _řídké spojení_ - port 21, udržováno permanentně
    - _datové spojení_ - port 20, otevíráno pro každý soubor

![](15/IMG_4495.JPG)

- dnes nastupuje HTTP/2
- HTTP = textový protokol
- HTTPS : port 443, TLS, certifikáty

## WEB

### HTTP (hyper text transfer protocol)
- textový protokol pro přísup k datům na www
- klient pošle požadavek a www server vrátí odpověď, komunikují TCP protokolem na portu 80
- přenášená data mohou být text, hypertext, audio
- dnes nastupuje HTTP/2
- HTTPS : port 443, TLS, certifikáty

### URL (uniform resource locator)
- definuje zdroj, který chce klient získat
- protocol://user:passwd@server/file#location

### Kategorie www dokumentů
- statické - pevný obsah na serveru (HTML)
- dynamické - vytvořený webovým serverem dle požadavků klienta (CGI)
- aktivní - serversem poskytnuté programy spuštěné u klienta (JavaScript)

## Jmenná služba

### DNS (domain name system)
- služba pro překlad doménových jmen na IP adresy a zpět
- dva způsoby pojmenování předmětných entit
    - plochý jmenný prostor (MujRouterDomaVBrne)
        - bez vnitřní struktury
        - riziko duplicit
    - hierarchický jmenný prostor (mujRouter.DomaVBrne.cz)
        - s vnitřní strukturou
        - možnost decentralizované správy
- Domain Name Space - hierarchický strom
- každý uzel má jmenovku (label) a doménové jméno (domain name), které končí tečkou a je zřetězením jmenovek od uzlu až do kořene
- národní domény (cz, sk, uk, ...) & základní domény (com, edu, gov, net, ...)

### DNS server types
- root servers
- TCP authoritative servers
- recursive resolver
- cachce server
- name server (for your domain)

- DNSSEC: podepisování DNS záznamů, PEM

## Kvalita služby QoS
- standardně jsou toky v TCP/IP obsluhovány se stejnou prioritou
- některé přenosy vyžadují přednostní zpracování (např. realtime procesy)

### Parametry síťových toků:
- spolehlivost
- zpoždění (latence)
- rozptyl zpoždění (jitter)
- přenosová kapacita

### Mechanismy zajištění kvality služby:
- plánování
- formování i omezování toků
- prevence zahlcení

## Plánování (scheduling)
- souvisí s obsluhou vstupních/výstupních front na odesílateli, příjemci a vnitřních síťových prvcích

### FIFO (first in, first out) - fronta
- zvýhodnění agresivních proudů, bez podpory priority
- FCFS (first come, first serve)

### Prioritní fronta
- pakety jsou rozřazeny do prioritních tříd, které mají vlastní frontu
- pakety s nižší třídou mohou vyhladovět

### Vážená prioritní fronta
- podobné prioritní frontě, každá fronta má váhu
- podle váhy je z fronty uvolněn příslušný počet paketů (round robin)

## Formování / omezování toků (traffic shaping)
- mechanismus pro řízení množství a rychlosti odesílaných paketů

_average rate_ = počet paketů, které lze zpracovat za určitý čas

_peak rate_ = max.počet paketů, které lze poslat během dočasného zvýšení posílaných paketů

_burst size_ = max. počet paketů, které lze poslat během extrémně krátkého časového intervalu

### Leaky Bucket
- vyhlazení přenosu
- princip děravého kyblíčku
- pokud je kyblíček plný, nově příchozí pakety jsou zahozeny

### Token Bucket
- umožnění krátkodobých špiček

## Prevence zahlcení (congestion avoidance)
- pokud je fronta plná, nově příchozí pakety se zahazují
- může dojít k vlnám zahlcení napříč uzly

### RED (random early detection)
- při určitém aplnění fronty začne zahazova náhodné pakety -> zpomalení
- odstraňuje problém globální synchronizace

### WRED (weighted random early detection)
- stejné jako RED, ale zholedňuje prioritu paketů

## Kvalita služby internetu

### Integrované služby
- ověřování zdrojů - zamítnutí nebo vyhovění
- rezervace zdrojů (protkoly. RSVP, YESSIR)
- přenos dat
- nevýhoda: problém škálovatelnosti (musíme udržovat vnitřní stav sítě)

### Rozlišované služby
- označení priority paketů
- pole v hlavičce Type of Service (IPv4), TrafficClass (IPv6)
- výhody: škálovatelnost, jednoduchost, bez zpoždění způsobeného rezervací

## QoS při přenosu multimédií
- některé služby vyžadují určitou minimální úroveň šiřky pásma a zpoždění

Například:

- IP telefonie
- videokonferenční hovory
- online hry
- řízení strojů v reálném čase
- operace na dálku
- IPTV - televize přes internetový protokol
- obsluha jaderného reaktoru

