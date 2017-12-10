# 4 simple måder at øge sikkerheden på din Nginx Server

## Hvad er Nginx

Nginx er en kraftfuld open source software til Web Serving, Load Balancing, Media Streaming, Caching og meget mere. Nginx startede som en web-server designet til maksimal stabilitet og ydeevne. Ud over sine HTTP-serverfunktioner kan Nginx også fungere som en proxyserver til e-mail (IMAP, POP3 og SMTP) og en Load Balancer og reverse proxy til HTTP- og TCP-servere. 

![Text](https://github.com/HakimiX/UFO/blob/master/Models/nginx.png)


Nginx blev oprindeligt udviklet til at være den hurtigste webserver, og dette formål er stadig et centralt mål for Nginx. Den slår Apache og andre server i benchmarks der måler web-serverens ydeevne. 


Web-server softwaren er indgangen til en server, derfor er web-serveren også det vigtigste mål for hackere, så de kan stjæle dine data og andre vigtige informationer. Som standard er Nginx en meget pålidelig og sikker web-server. Der er dog mange måder at sikre Nginx yderligere. 


Vi er godt klar over at det kan være svært at forbygge eller forhindre hacker angreb, derfor har vi opstillet 4 simple måder at øge sikkerheden på en Nginx web-server, ved at gøre brug af Nginx sikkerhedshærdningsprocess og sikkerhedsstandarder. Du vil lære hvordan man:
* Opdatere alt software 
* Forebygger informations lækage 
* Begrænser adgang via IP
* Udføre en sikkerhedsrevision

__Forudsætninger__
* Ubuntu 14.04 Server 
* Nginx web-server installeret og konfigureret 
* En domæne der peger på din server 

## Step 1 - Opdater alt software 

Ethvert software system fejler et eller andet – og det er bare et spørgsmål om tid, før nogen opdager dem. Hackere udnytter denne sårbarhed ved at skrive kode for at målrette mod et bestemt svagt punkt i dit software system. Store virksomheder har medarbejdere hvis eneste formål er at hacke ind i deres eget produkt, så de kan opdage og rette fejl, før ondsindede hackere kan drage fordel af dem. Derfor anbefaler vi at du opdatere til nyeste version for at sikre hele dit system og ikke kun Nginx. 


![Text](https://github.com/HakimiX/UFO/blob/master/Models/updates.png)

Før du opdatere dit software system er det vigtigt at du laver en backup af hele dit system. På denne måde kan du vende tilbage til din backup, hvis der opstår problemer efter opdateringen. 

For at opdatere hele dit software system og alle tilhørende packages og afhængigheder, skal du køre nedestående kommando: 

```
$ sudo apt-get update && sudo apt-get upgrade
```

## Step 2 - Forebyg informations lækage 

Der er 2 måder hvorpå information kan offentliggøres: Internt og eksternt. En intern offentliggørelse er eksempelvis, når en medarbejder gør privat information offentlig. Dette kunne ske som følge af manglende forståelse for informationernes følsomhed eller uforsigtighed. 

En ekstern offentliggørelse finder sted, når en person uden for organisationen får adgang til dit software system og offentliggøre information på websteder. Du skal være forberedt på begge typer trusler, men vi vil fokusere på ekstern offentliggørelse. 

For at forhindre at web-server informationer bliver offentliggjort, skal vi begynde med sikkerhedshærdningsprocessen. 

Når en web browser opstiller en forespørgsel til en side fra en web-server, svarere serveren med indholdet samt en HTTP Response Header. Nogle af disse HTTP Header indeholder metadata, såsom HTTP status koder, Request metoder og andre relevante informationer vedrørende vores operative system. Ved at skrive `curl –I http://localhost` kan du se et eksempel på dette. 

```
HTTP/1.1 200 OK

Server: nginx/1.3.6 (Ubuntu)
```

Ovenstående output viser navnet på vores operative system og versionen på vores Nginx web-server. Ondsindede hackere kan bruge denne information til at undersøge vores operative system og planlægge deres angreb. Derfor er det vigtigt at vi konfigurere vores Nginx, så disse oplysninger ikke offentliggøres

Start med at navigere hen til din Nginx konfiguration som ligger i følgende sti: `/etc/nginx/nginx.conf/`.Herefter kan du gøre brug af nedenstående kommando til at åbne Nano editor, så du kan skrive i filen. 

```
$ sudo nano /etc/nginx/nginx.conf
```

Find HTTP konfigurationen og tilføj følgende linje kode: `server_tokens off;`. Afslut med at gemme og forlade filen. HTTP konfigurationen bør se således ud: 

```
http {
    server_tokens off;
}
```

For at ændringerne træder i kraft, skal du genindlæse Nginx ved at skrive nedenstående kommando: 

```
$ sudo service nginx reload 
```

Vores HTTP Header viser ingen information vedrørende vores operative system efter at ændringerne er trådt i kraft. Skriv `curl –I http://localhost` for at få nedenstående output. 

```
HTTP/1.1 200 OK
Server: nginx
```

Ud over vores server HTTP Header er der en anden Header der også indeholder følsom information, fordi den viser version af PHP og andre informationer vedrørende Nginx. 


```
HTTP/1.1 200 OK
Server: nginx

X-Powered-By: PHP/7.1-1ubuntu4.14
```

Hackere kan drage fordel af denne information ved at undersøge allerede eksisterende sikkerhedshuller i de versioner vi har installeret på vores system. Det er vigtigt at skjule disse oplysninger, og dette gøres ved at skrive `expose_php off` i din `php.ini` fil. 

Næste vigtige ændringer er vores ”error pages”, såsom `401`, `403` og `404`. For at ændre disse skal du navigere til denne sti: `/etc/nginx/sites-enabled/defualt`. Herefter skal du tilføje følgende linje kode i server konfigurationen. 

```
server {
    error_page 401 403 404 /404.html;
}
```

For at ændringerne træder i kraft, skal du genindlæse Nginx ved at skrive nedenstående kommando: 

```
$ sudo service nginx reload 
```

### Step 3 - IP Begrænsning 

Sikkerhed handler ikke altid om, at have lange og komplicerede passwords. Man skal også prøve at holde de følsomme områder af sin webside væk fra ondsindede hackere. 

De sårbare områder såsom admin pages, CPanel og andre sider kan nemt tilgås og udnyttes af hackere for at få adgang til din webside. Hvis man har en svag adgangskode, kan adgangskoden nemt knækkes af hackere, som har en del værktøjer til at knække koder. Dette kunne være et brute force angreb, hvor hackerne prøver at knække adgangskoden, ved at der afprøves forskellige kode kombinationer indtil den rigtige kode er fundet. Der er en del værktøjer, som hackere gøre brug af for at udføre et brute force angreb, Hydra er det mest kendte og effektive værktøj. 

Udover at kunne oprette en lang og kompliceret kode som både indeholder tal, små-, store bogstaver, og tegn kan man også begrænse IP addresser for at få adgang til den specifikke side man vil beskytte.

Man kan angive de betroede IP addresser som eksempelvis din egen eller andre administratorer der skal kunne tilgå siden og have adgang. Her kan man så blokere alle andre IP’er fra at få adgang til siden. Dette medførere at din admin page kun kan tilgås fra de IP addresser du stoler på og kender.

Du kan tilføje og fjerne IP addresser ved at aktivere IP Restriction via Nginx configuration. Dette gøres ved at åbne Nginx configiration:

```
$ sudo nano /etc/nginx/sites-enabled/default
```

Herefter skal man kigge på server konfigurations delen:

```
server {

    location /wp-admin/ {
        allow 192.143.1.2/24;
        allow 10.2.0.1/24;
        deny all;
    }
}
```

Her har vi et eksempel på en location som er wp-admin siden. Her kan du så tilføje, redigere og fjerne alle de IP addresser der skal kunne tilgå siden. 

For at ændringerne træder i kraft, skal du genindlæse Nginx ved at skrive nedenstående kommando: 

```
$ sudo service nginx reload 
```

Når man nu prøver at tilgå admin page fra en IP addresse som ikke er iblandt IP Adresserne der skal have adgang, vil man få en `402 forbidden error`. 

## Step 4 - Sikkerhedsrevision

Vi anbefaler at du laver en sikkerhedsrevision, som er en systematisk evaluering af sikkerheden i dit software system, ved at måle hvor godt det er i overensstemmelse med et sæt af allerede etablerede kriterier. Det er ikke muligt at finde alle sikkerhedshuller og svagheder manuelt, derfor anbefaler vi tredjeparts værktøjer såsom Internal Audit software, Maltego, Metasploit osv. 

## Konklusion

Det er svært at forebygge og forhindre ondsindede hacker angreb, men efter at have læst denne artikel håber vi at du føler dig mere sikker når det kommer til sikkerheden i Nginx. Som sagt har ethvert software system sikkerhedshuller og svagheder, derfor er det vigtigt at du løbende øger sikkerheden ved at opdatere og konfigurere.  


## Kilder

https://www.digitalocean.com/community/tutorials/how-to-secure-nginx-on-ubuntu-14-04