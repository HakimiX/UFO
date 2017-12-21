# Hvor sikker er din Webserver?

_Skrevet af Mustafa & Kevin_

## Introduktion

Din hjemmeside er dit brand og ofte den første kontakt med kunderne. Hvis hjemmesiden ikke er sikker, kan dine forretningsforbindelser bliver kompromitteret og have stor indflydelse på kundernes tillid. Truslerne kan komme i mange forskellige former og inficere din hjemmeside med malware for at sprede endnu mere malware til de besøgende på hjemmesiden. De kan stjæle de besøgendes kundeoplysninger, kreditkort, personlige oplysninger og endda forårsage nedbrud af hele din hjemmeside. En enkelt sikkerhedsbrud kan være altafgørende for en lille virksomhed. 

Jo mere en lille virksomhed kan gøre for at opbygge sikkerheden på deres hjemmeside, desto mere sandsynligt er det at kunderne besøger, køber, bliver og anbefaler. Det giver kunderne sikkerhed for at hjemmesiden er sikker, og at virksomheden er opmærksom på risiciene. Derfor er sikkerhed vigtigt!  

## Webserver Sikkerhed

Webserveren er en vigtig del a web-baserede applikationer og spiller en afgørende rolle i din hjemmesides sikkerhed. En sikker webserver er fundamentet for beskyttelse af dine webapplikationer, filer og data. Det ligegyldigt om du driver en stor virksomhed eller lille virksomhed – det er under alle omstændigheder vigtigt at du beskytter din webserver da hele netværket og virksomheden er afhængig af den. 

Webserveren og ethvert netværk der er forbundet til den er desværre udsat for alvorlige sikkerhedsrisici. Web serveren er et vindue mellem verden og dit netværk. Din indsats på servervedligeholdelse afgøre størrelsen på vinduet, men du kan aldrig lukke vinduet helt, da intet software system er fejlfrit. 

Nedenstående er top 8 netværks angreb efter typer, der er optaget fra april til juni 2017, og offentliggjort i en rapport fra McAfee Labs fra september 2017. [McAfee Labs](https://www.mcafee.com/us/mcafee-labs.aspx) er trusselforskningsafdelingen fra [McAfee](https://www.mcafee.com/uk/index.html), som er en af verdens førende kilder til trusselforskning og cybersecurity. Rapporten er baseret på data indsamlet fra millioner af sensorer, der forvaltes af McAfee. Sensorerne har til formål at levere real-time trussel intelligens. 

![Text](https://github.com/HakimiX/UFO/blob/master/Models/webattacks.jpg)

Ud fra den indsamlede data kan vi se at browserbaserede netværksangreb udgøre 20%. De ondsindede hacker forsøger at bryde en maskine gennem en webbrowser. Disse angreb starter ofte på sårbare hjemmesider med dårlig eller ingen sikkerhed. Hackerne får adgang til webserveren og inficere med malware, der spreder sig som influenza. 

Derudover kan vi se at Denial-of-Service (DDoS) angreb udgøre 15%. Denne form for angreb har til formål at nedbryde dit system ved at overvælde din webserver med trafik. Hvad er den mest skadelige konsekvens af DDoS-angreb på din virksomhed? Ifølge IT sikkerheds professionelle og netværksoperatører er det tab af kundernes tillid. En [undersøgelse](https://www.corero.com/company/newsroom/press-releases/loss-of-customer-trust-and-decreased-revenues-most-damaging-consequences-of-ddos-attacks-according-to-it-security-pros-and-network-operators/) fra Corero, som er en anerkendt DDoS sikkerheds udbyder, viser at næsten 45% af de IT sikkerhedsprofessionelle har sagt at den største konsekvens er tab af kunderens tillid og 34% har svaret tab af indtægter

En ud af tre virksomheder oplevede et DDoS angreb i 2017, ifølge en undersøgelse fra Kaspersky Labs. Kaspersky Labs er trusselforskningsafdelingen fra [Kaspersky](https://www.kaspersky.dk/), som har udviklet [prisvindene](https://www.kaspersky.com/about/awards) sikkerhedsteknologier. Ca. En tredjedel af respondenterne i Coreros [undersøgelse](https://www.corero.com/company/newsroom/press-releases/loss-of-customer-trust-and-decreased-revenues-most-damaging-consequences-of-ddos-attacks-according-to-it-security-pros-and-network-operators/) har svaret at DDoS-angreb på deres netværk forekommer ugentligt eller endda dagligt. DDoS vokser i hyppighed og kompleksitet, derfor er det vigtigt at din webserver er forbygget mod denne form for trussel. 

Coreros undersøgelse spurgte også om de nuværende metoder til at håndtering af DDoS-truslen, og her har en tredjedel (30%) svaret at de er afhængige af traditionelle sikkerhedsinfrastrukturprodukter såsom load balancer, IPS og firewalls. Men ifølge Dave Larson som er COO hos Corero, er traditionelle sikkerheds tiltag ikke tilstrækkelige mod DDoS angreb. 


> “Those companies are very vulnerable to DDoS attacks because it’s well-documented  that traditional security infrastructure products aren’t sufficient to mitigate DDoS attacks,” - Dave Larson


Malware udgøre 10% af alle angreb. Malware er ondsindet software designet til at spionere, stjæle eller skade dit system. Som sagt kan Malware bruges til at stjæle dine besøgendes kundeoplysninger, kreditkort og personlige oplysninger, hvilket resultere i tab af kunder. Coreros research og detekteringsteknologi viser, at cyberkriminelle bruger ”low-level” DDoS angreb som påvirker netværkets ydeevne og samtidig distrahere it-sikkerheds medarbejder så angrebet kan inficere med forskellige former for malware. 


> "Such attacks often act as a smokescreen for more malicious attacks. While the network security defenses are degraded, logging tools are overwhelmed and IT teams are distracted, the hackers may be exploiting other vulnerabilities and infecting the environment with various forms of malware." – Corero


## Hvor nemt et det egentlig at få adgang til følsomme oplysninger?

Når man vil angribe en webserver, ønsker man normalt at få adgang og kunne styre webserveren så man kan downloade fortrolige oplysninger og udnytte det yderligere ved at sprede Malware. Nedenstående demonstrere hvor nemt det faktisk er at få adgang til følsom data på vores Hackernews webserver. 

I denne gennemgang gøre vi brug af Kali Linux som gør hacking meget lettere. [Kali Linux](https://www.kali.org/) indeholder mere end 300 præinstallerede værktøjer til hacking og er en af de mest populære programmer til hacking og penetration testing. Personer uden programmerings baggrund kan nemt følge Kali Linux tutorials på internettet og få adgang til følsomme oplysninger. 

Vi starter med at ”Stealth Scan” Hackernews siden som ligger på følgende adresse: `165.227.136.184`. [Stealth Scanning](https://nmap.org/bennieston-tutorial/) er en velkendt måde til at opdage kommunikationskanaler og udnytte dem. Et virkeligt eksempel på Stealth Scanning kunne være, at gå op til en lejlighedsbygning og banke på hver dør for at se, hvem der er hjemme. Stealth Scanning stiller eksempelvis følgende spørgsmål til webserveren: hvilken webserver kørere du? Bruger du en mail server? Bruger du Telnet, FTP eller RCP? Webserveren afslører desværre mange af disse informationer og det tillader en uberettiget besøgende at få uautoriseret adgang til webserveren. Vi har gjort brug af værktøjet [NMAP](https://nmap.org/) til at få adgang til følsomme oplysninger. Vi kan se hvilken webserver der er brugt og hvilke TCP og HTTP porte der er åbne og tilgængelige. Kali Linux Terminal Kommando - `nmap -v 165.227.136.184`

![Text](https://github.com/HakimiX/UFO/blob/master/Models/StealthScanPorts.jpg)

Derudover kan vi få adgang til SSH-Host Key. Hver computer har en unik Host Key, som er en kryptografisk nøgle, der bruges til at godkende computere. Deling af SSH-Host Key er ikke anbefalet da det kan resultere i sårbarhed over for en ”Man-in-the-Middle” (MITM) angreb. [Man-in-the-middle]( https://www.ssh.com/attack/man-in-the-middle) er et angreb mod en kryptografisk protokol så hackeren kan forhandle forskellige kryptografiske parametre med webserveren og klienten. Kali Linux Terminal Kommando - `nmap –A 165.227.136.184`. 

![Text](https://github.com/HakimiX/UFO/blob/master/Models/StealthScanSSH.jpg)

Vi har også udført et DoS-angreb (Denial-of-service-attack) mod webserveren vha. værktøjerne Scatter og [Hping3](https://tools.kali.org/information-gathering/hping3). Formålet med et DoS angreb er at gøre webserveren utilgængelig for sine tilsigtede brugere ved at overbelaste den med trafik. DoS-angrebet medførte at Hackernews siden blev en del langsommere og reagerede ikke til nogle anmodninger. Kali Linux Terminal Kommando - `hping3 – S –V –flood –rand-source 165.227.136.184`.

![Text](https://github.com/HakimiX/UFO/blob/master/Models/hping3.jpg)
![Text](https://github.com/HakimiX/UFO/blob/master/Models/hpin3result.jpg)


Truslerne kan som sagt komme i mange forskellige former og ovenstående eksempler er blot en advarsel til dig, så du kan indse hvor nemt det er at få adgang til følsomme oplysninger. Så snart de ondsindede hackere har adgang til din webserver, er dine kunders oplysninger udsat, og det kan have store konsekvenser for dig og din virksomhed. Der er mange fordele ved at øge sikkerheden på din webserver, herunder at dine kunder har tillid til din hjemmeside og føler sig tryg når de eksempelvis handler online. Din webserver sikkerhed kan også have indflydelse på din hjemmesides søgeoptimering. Google har nemlig meldt ud at de vil rangere krypterede (HTTPS) sider højere i søgeresultater bl.a. for at eliminere nogle af de sikkerhedsrisici som ubeskyttede webservere udgøre. HTTPS benyttes på sider hvor der foretages udveksling af fortrolige oplysninger såsom kundeoplysninger,   transaktionsoplysninger og kreditkortsoplysninger. [HTTPS as a ranking signal](https://webmasters.googleblog.com/2014/08/https-as-ranking-signal.html). 


## OWASP ZAP Sikkerhedstest

En sikkerhedstest analysere din hjemmesides kode og hvordan den interagere med andre objekter for at identificere svagheder eller fejl, så vi kan forhindre at ondsindede hackere ikke får uautoriseret adgang til webserver eller andre netværk tilknyttet vores webserver. Vi har gjort brug af OWASP Zed Attack Proxy (ZAP) sikkerhedsværktøj til finde sikkerhedsfejl i vores Hackernews applikation. Nedenstående er en demonstration af OWASP ZAP Scan af vores system - `165.227.136.184`

![Text](https://github.com/HakimiX/UFO/blob/master/Models/OWASP2.jpg)

I OWASP’s brugergrænsefladen kan vi se at vores applikation er udsat for ”Clickjacking” angreb. Clickjacking angreb er når en hacker benytter gennemsigtige eller uigennemsigtige lag til at narre brugere til at klikke på et link eller en knap på en anden side, selvom brugerens hensigt var at klikke på øverste lag. 

> ”X-Frame-Options header is not included in the HTTP response to protect against Clickjacking attacks” - OWASP ZAP

![Text](https://github.com/HakimiX/UFO/blob/master/Models/OWASP1.jpg)

OWASP gør os opmærksom på at vores web browser XSS beskyttelse ikke er aktiveret. HTTP XXS beskyttelses response header er en funktion af Chrome og Safari, der har til formål at stoppe sider der indlæses med reflekterende XXS angreb (Cross-site scripting). Cross-site scripting er når en hacker påfører din hjemmeside ondsindede scripts. Via din hjemmeside kan en hacker påfører ondsindede scripts til dine kunders browser.  

> ”Web Browser XSS Protection is not enabled, or is disabled by the configuration of the X-XSS-Protection http response header on the web server” - OWASP ZAP



## Hvad kan du gøre?

Ifølge en undersøgelse fra [Netcraft](https://news.netcraft.com/archives/2017/01/12/january-2017-web-server-survey.html), som er en betroet udbyder af IT-sikkerhed og Anti-phishing, er Apache og Nginx blandt de mest populære webservere verden over. Undersøgelsen viser at Apache har fået næsten 820 millioner websteder (47%) og Nginx har fået 17 millioner websteder.  Derfor har vi opstillet nogle løsninger til hvordan du kan øge sikkerheden på din Apache- eller Nginx Server. 

### Apache Server
***

Apache HTTP Servers har et godt ry for sikkerhed, og et udviklerfælleskab som går en del op i sikkerhedsproblemer. Desværre er det uundgåeligt, at nogle problemer vil blive opdaget i softwaren efter at det er blevet frigivet.

Alle netværksservere kan være underlagt DDoS angreb (Denial of service attacks), som gør at serveren overbelastes i sådan en grad at reelle forespørgsler til serveren ikke kan besvares i tide. Det er næsten umuligt, at forhindre sådanne angreb, men der er visse ting man kan gøre for, at øge sikkerheden for DDoS angreb. 

Ofte er de mest effektive anti-DDoS værktøj en firewall. De fleste firewalls kan f.eks. konfigureres til at begrænse antallet af samtidige connections fra en hvilken som helst individuel IP-adresse eller netværk. Dette forhindrer en række simple angreb.

__Abonnere på Apache HTTP Server Announcements List__

Apache tilbyder en service som man kan abonnere på, der holder dig orienteret om nye udgivelser og sikkerhedsopdateringer. På denne måde kan du være sikker på at have de nyeste opdateringer hele tiden. [Reference](http://httpd.apache.org/lists.html#http-announce)

__Firewalls__

Firewalls er et godt værktøj til at forhindre simple angreb såsom DoS. DDoS (Distributed Denial of Service Attack) som derimod er næsten umulig at forhindre, da angrebet benyttes af tusindvis af computere og forbindelser.

__Log Files__

Det er altid en god ide, at holde øje med dine log files, så du har et overblik over hvad der rent faktisk sker mod din server. Det er dog ikke en måde, at forhindre angreb,men det er et godt værktøj til at finde ud af hvilke angreb der har været rettet mod din server.

Apache har også skrevet om konfigurationsindstillinger der kan hjælpe med at mildne diverse problemer, som kan findes på deres [side](https://httpd.apache.org/docs/2.4/misc/security_tips.html
)

### Nginx Server
***

Nginx er en web server med fokus på høj parallelitet, ydelse og lavt hukommelsesforbrug. Som standard er Nginx en meget pålidelig og sikker web-server. Der er dog mange måder at sikre Nginx yderligere. Nogle gode metoder til at øge sikkerheden kunne være følgende:

__Opdateringer__

Sørg for at have de nyeste opdateringer hele tiden, da næsten hver opdatering handler om sikkerhed.

__SSL Certificate__

Det er en god ide at have SSL implementeret så man kan få adgang til web applikationen med HTTPS og tilføje yderligere krypterings kommunikation.

__HTTP Methods__

I fleste tilfælde behøver man kun `GET`, `HEAD` & `POST` HTTP anmodninger i din webapplikation. Hvis man tillader `TRACE` eller `DELETE` kan det være risikabelt, fordi det kan tillade cross-site tracking angreb, hvilket kan gøre at hackere kan stjæle cookie oplysninger.

__IP Restriction__

Det kan være en god ide, slå IP restriction til via Nginx configuration, så du kun tillader betroede IP-adresser at have adgang til eksempelvis admin page. [Reference](https://www.digitalocean.com/community/tutorials/how-to-secure-nginx-with-let-s-encrypt-on-ubuntu-16-04)

__Begrænsning af Forbindelser__

Nginx er god til at håndtere mange samtidige forbindelser end backend-servere. Derfor kan man begrænse antallet af forbindelser til hver backend-server. For eksempel, kan man via configuration, begrænse forbindelser. Du kan selv bestemme hvor mange forbindelser hver backend-server i din website upstream skal etablere. [Reference](https://www.nginx.com/blog/mitigating-ddos-attacks-with-nginx-and-nginx-plus/)

__Begrænsning af Requests__

At begrænse indgående forespørgsler kan være en god ide. Dette kan man konfigurere i Nginx for at tillade en enkelt klients IP-adresse kan prøve at logge ind kun hvert 2 sekund, dette svarer til 30 requests per minut. [Reference](https://www.nginx.com/blog/mitigating-ddos-attacks-with-nginx-and-nginx-plus/)


## Konklusion

Efter at have læst denne artikel håber vi at du har fået et indblik i hvor afgørende en rolle sikkerheden i din webserver spiller for virksomhedens økonomi, troværdighed og overlevelse. Ethvert software system har sikkerhedshuller og svagheder, derfor er det vigtigt at du løbende øger sikkerheden ved at opdatere og konfigurere.  


