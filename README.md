# SIS - Teorija MI2

# ISHOD 1.

1.  Objasniti što su tri aspekta sigurnosti (CIA)?

Povjerljivost → Osiguravanje tajnosti podataka (Bitno za slanje podataka mrežom, ali i za podatke u mirovanju, za zaštitu se koriste enkripcija i anonimizacija.); Integritet → Zaštita promjene informacije (može biti narušen na razne načine kao što su brisanje datoteke, mijenjanje datoteke. Za provjeru koristi se hash.); Dostupnost → Osiguravan dostupnost informacija odnosno sustava

2.  Što je sigurnosni rizik?

Rizik je mogućnost realizacije neželjenog događaja koji može štetno utjecati na povjerljivost, integritet i raspoloživost informacija

3.  Što su kontrole? Kakve kontrole prema načinu djelovanja postoje?

Sigurnosne kontrole umanjuju rizik, to su politke, procedure, prakse i organizacijske strukture

Postoje tehničke i upravljačke kontrole

4.  Opisati kvalitativni izračun rizika.

5.  Na koje sve načine je moguće tretirati rizik? Pojasnite.

- Rizik je moguće tretirati na tri načina
    - Umanjivanje → implemenatcij kontrola
    - Prenošenje → eksternilizacija i osiguranje
    - Izbjegavanje → modifikacija procesa odnsono procesni reinžinjering
- Rizik je potrebno periodički evaluirati i montinuirano nadzirati

6.  Što je ISO 27001 norma i čemu služi?

- Niz standarda IT Security-a koji pruža najbolje prakse i preporuke
    - Okvir za uspostavu, implementaciju, nadzor, reviziju i održavanje ISMS-a
    - Neovisan je o organizaciji (banka, slastičarna, faks itd.)
    - Mogućnost firmi da se certificiraju
- Implementacija
    - Potrebno osigurati sve resurse
    - Redovita procjena rizika

7.  Pojasnite CIS Top 20 kontrolni okvir? Zašto je učinkovit?
Jedan je od naj-respeced kontrolnih okvira, te je javno dostupan

- Foksuira se na aktivnosti koje mogu donijeti najveću korist
- Velik je broj uključenih
- Učinkovit je zato što je jednostavan za pratiti, te ga se lako implementira.

# ISHOD 4.

1. Koje su točke životnog ciklusa ranjivosti? Nacrtati životni ciklus.

Trenutak javne objave informacija o ranjivosti → Trenutak izdavanja sigurnosne zakrpe → instalacija sigurnosne zakrpe.

2. Što je exploit, što je ranjivost, što je 0-day ranjivost?
Exploit je specijalizirani program koji iskorištava ranjivost. Ranjivost je slabost u sustavu, sigurnosnim procedurama, dizajnu ili implementaciji resursa. 0-day ranjivost je sigurnosni propust u računalnj aplikaciji koji je otkriven i poznat je samo napadačima prije nego što za njega zna proizvođač i javnost.

3. Što je period kritične izloženosti?

To je vremensko razdovlje od trenutka kada je ranjivost otkrivena do trenutka kada je objavljena zakrpa.

4. Koje su tri tehnike koje možemo koristiti za otkrivanje i analizu ranjivosti?

Redovito skeniranje ranjivosti, definiranje prioriteza za uklanjanje ranjovisti, koristeći threat intelligence

5. Objasnite funkcionalnosti alata za procjenu ranjivosti (npr. Nessus)

Nessus je vulnerability scanning alat koji skenira računalo, te ako pronađe neki vulnerablity alerta korisnika o istom. Nessus NE sprječava napade, koristi se samo za skeniranje, Nessus nije antivirus.

6. Čemu služi alat Metasploit?

Metasploit je alat koji služi za iskorištavanje ranjivosti. Sadrži stotine exploit programa koji su spremi za korištenje.

7. Što su SIEM sustavi? Koje funkcionalnosti imaju?

SIEM sustavi su aplikacije koje omogućavaju centralno prikupljanje log zapisa, te analizu, korelaciju, pretraživanje i uzbunjivanje. Imaju dvije funkcionalnosti: SIM → log management i SEM → real-time monitoring i incident managing.

8.  Koja je prednost implementacije rješenja (u odnosu na SIEM) za naprednu detekciju na klijentima?

Nedostatak SIEM rješenja je implementacija, jer je vrlo kompleksna, skupa i zahtjevna prema resursima. XDR je “bolja verzija” SIEM-a te pokriva prva dva SIEM scenarija.

9. Zašto je važno što prije otkriti neovlašteni upad u informacijski sustav?

Nakon što hakeri upadnu u informacijski sustav, cilj im je proširiti se po cijelom sustavu (najčešće im je cilj doći do AD Controllera) važno ih je otkriti prije no što dođu do cilja, jer će s kontrolom AD sustava moći kontrolirati cijeli sustav.

10. Objasnite SQL Injection te mjere zaštite od istog?

Napadač, preko forme u aplikaciji može poslati SQL query kojeg će baza u pozadini pokrenuti i korisniku vratiti tražene infromacije. Braniti se može koristeći procedure u bazi, ne dohvaćati informacije preko običnih query-a.

11.  Objasnite Cross Site Scripting te mjere zaštite od istog?

Slično kao SQL Injection, XSS (Cross side scripting) je tehnika injectanja JavaScripta na webpage. Najčešće se napadaju forme, gdje na inputu možemo poslati neki JavaScript kod, npr. možemo ukrati cookies ili tako nešto. Zaštiti od XSS napada se možemo escpeanjem charactera. npr. haker naiđe na vulerable stranicu, te želi testirati da li je XSS moguć, prvo će formi poslati ovakav JS kod: <script>alert(1337)</script>. Programer može escapeati <> charactere, te ih server neće pročitati. Poruka će izgledati ovako: scriptalert(1337)/script.

12.  Što je OWASP Top 10?
OWASP top 10 je lista deset najčešćih prijetnji. To je web stranica kojoj je cilj povećati awerness o sigurnosti developerima.

1. Koja je razlika između penetracijskog testiranja i procjene ranjivosti putem alata?

Penetracijsko testiranje zapravo je procjena ranjivosti putem raznih alata, tako da nema razlike.

14.  Kratko objasnite Shodan
Shodan je search engine preko kojega se mogu pronaći svi uređaji koji su spojeni na internet koristeći service bannere (blok teksta koji opisuje servis koji se odvija).

15.  Objasnite koncept korelacije događaja. Zašto je korelacija temeljna na pravilima izazov?
Korelacija omogućava pronalazak povezanosti između dva ili više sigurnosnih događaja.

# ISHOD 5.

1.  Što su vatrozidi te što je nulto pravilo kod vatrozida? Što su vatrozidi nove generacije?

Vatrozid je hardware ili software namjenjen za filtriranje mrežnog prometa. Osnovna funkcija vatrozida je zaštita računala od napada na mrežnoj razini. Nulto pravilo vatrozida kaže: **odbaci sav mrežni promet.**

Vatrozidi nove generacije detaljno ispitivaju mrežni primet, te poboljšavaju kontrolu pristupa. Mogu se integrirati sa Threat intelligenceom, sadže black i white liste, detaljan logging sustav etc.

2.  Zašto Gartner smatra da tvrtke trebaju imati pristup informacijskoj sigurnosti kao da su u stanju kontinuirane kompromitacije?

Gratner to smatra zato što se firme previše oslanjaju na preventivne kontrole. Mnoge tvrtke previše vjeruju u prevenciju.

3.  Na koje dvije stvari, koje su ključne da poslovanje dostigne svoje ciljeve, se odnosi kontinuitet poslovanja?

Isporuka otpornog poslovanja i zaštita reputacije.

4.  Pojasnite analizu učinka na poslovanje (engl. Business Impact Analysis).

BIA je proces analize svih poslovnih aktivnosti, te kakav učinak će prekid jedne od poslovnih aktivnosti imati na cijelu organizaciju.

5.  Što je polimorfizam?

Polimorfizam je promjena tijela programa uz zadržavanje iste funkcionalnosti.

6.  Objasnite fileless maliciozne programe.

Fileless malware je skripta koja se zapiše u Registry windowsa, to omogućuje malwareu da se pokrene s pokretanjem računala. Filesless malware je zapravo ta skripta koja je sastoji od niza komandi.

7.  Objasnite termine „Indicators of compromise“ i „Indicators of attack“. Koja je razlika?

IOC = indikatori komprimizacije, tj. indikator je li haker ušao u mrežu.
IOA = indikatori koji se fokusiraju na detekciju namjera napadača, ponašanje napadača itd.

8.  Što je Threat Intelligence? Navedite s kojim dijelovima sigurnosne infrastrukture možemo integrirati threat intelligence.

Threat intelligence je prikupljanje, klasifikacija i iskorištavanje znanja o protivinicima. Threat intelligence se može integrirati sa SIEM sustavima, koriste ga SOC-ovi.

9.  Što su mreže malicioznih programa (engl. botneti)?

To je mreže zaraženih računala koje haker preko C&C centra može kontrolirati u neke svoje svrhe. Najčešće je to cryptocurrency mining, DDOS napadi ili spam kampanje.

10.  Što su mrežni IDS/IPS sustavi?

IDS/IPS sustavi detektiraji u sprječavaju neovlaštene aktivnosti.
IDS (Intrusion Detection System) analizira i nadgleda mrežni promet, te traži znakove napada. IDS uspoređava aktivnost na mreži s bazom podataka prijetnji kako bi uočio napade.
IPS (Intrusion Prevention System) odbija odabrani promet na mreži ako taj promet smatra malicioznim

11.  Pojasnite pojam APT. Koja je razlika u odnosu na tradicionalne napade? Zašto su APT napadi opasniji?

APT ili Advanced Presistent Threat je termin kojeg je razvila američka vojska koji bi koristili za klasifikaciju napada čije detalje nisu smjeli otkriti javnosti. APT napadi su posebni po tome što zahtjevaju izrazito velike ljudske i novčane resurse, te ga mogu izvesti samo vlade ili velike organizacije. APT napadi su opasniji zbog toga što praktički imaju neograničene resurse, te zbog toga mogu exploitati 0-day vulnerability-e.

12.  Čemu služe sigurnosne vježbe? Pojasnite.

Sigurnosne vježbe služe poboljašnju sigurnosti neke firme, uzmimo za primjer penetracijski test. Nekom testeru biti će zadatak da izvana proba doći do nekih osjetljviih podataka unutar firme. Ako napadač to uspješno izvrši, firma će dobiti detaljnu analizu kako je napadač to uspio, te će moći podnjeti mjere zaštite tako da takav napad neće moći izvršiti drugi napadači.

13.  Objasnite sustave za detekciju neovlaštenih aktivnosti na internoj mreži. Koja je korist takvih sustava? Kako se koristi strojno učenje?

14.  Objasnite ransomware. Zašto je fokus napadaca stavljen više na kompanije? Koje tehnike
napada se koriste u takvim napadima na kompanije? 

Ransomware je a type of malicious software designed to block access to a computer system until a sum of money is paid. Kompanije će platiti. Lateral movement, tj. širenje ransomwera interno.

14.  Što je Mitre ATT&CK?

Mitre Attack framework je popis svih taktika i tehnika napada izvučenih iz pravih primjera.
