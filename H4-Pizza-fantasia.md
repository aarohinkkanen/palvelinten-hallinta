# Pizza fantasia

## x)

### 4.12.1 Size and Complexity of Some DSLs
- DSL:t voivat kasvaa erittäin suuriksi ja niistä voi tulla monimutkaisia. 
- Salt-niminen hallinta ohjelma sisältää state-funktioita ja dokumentaatio tälle on peräti yli 75 000 sanaa pitkä. 
- Salt generoi koodia Jinja2 hyödyntäen.
- Puppet on huomattavasti pienempi, koska se sisältää vain 113 funktiota. 
- Yleiset ohjelmointikielet esittävät toiston funktiona, mutta Puppetilla on oma menetelmä ja siinä toiston tilalla käytetään virtuaaliresursseja.
- Kysymys: Millaisissa ympäristöissä kumpikin on parempi?

### 4.12.2 Use of DSL Functions in Case Configuration
- CM-työkaluissa on satoja eri funktioita, mutta vain pientä osaa niistä käytetään.
- Yleisimpiä on case, file, package ja exec.
- Eli vaikka tarjolla on suuri määrä funktioita, niin silti pieni joukko funkioita riittää suurimman osan käytttö tarpeista.
- Kysymys: Millaisissa tilanteissa näitä muita funktioita käytetään.

### 4.12.3 Dependencies Between Main Functions
- Avain funktiot: package, file, servicem user, group, directory ja symlink.
- Kaksi tärkeintä perustoimintoa ovat exec ja file.
- Näiden kahden päälle rakentuvat muut funktiot
- Järjestelmä on impotentti eli tekee muutoksia vain jos tila ei ole jo sille oikea.
- Huomio: Mielenkiintoinen rakenne, jossa execin ja filen päälle rakentuu muut tärkeätkin funktiot, kuten package, service, user ja group.

## a)
Aloitin päivittämällä järjestelmäni komenolla sudo apt update.
<img width="1004" height="235" alt="image" src="https://github.com/user-attachments/assets/ebf8052e-23c4-4356-b1c6-3fcc11dbda8f" />

Sitten asensin Caddy nimisen verkkopalvelimen komennolla sudo apt install caddy.
<img width="1004" height="525" alt="image" src="https://github.com/user-attachments/assets/b0c33625-5b29-4f0f-9f0f-1cebd2ed7dab" />

Koska minulla oli apache2 päällä ja se kuunteli porttia 80, niin en pystynyt saamaan aluksi Caddy:a päällä, mutta lopetin apache2 palvelun komennolla sudo systemctl stop apache2. Tämän jälkeen kun ajoin komennon sudo systemctl start caddy ja sen perään sudo systemctl status caddy niin huomasin, että se toimii.
<img width="1004" height="403" alt="image" src="https://github.com/user-attachments/assets/5c112402-597c-49d8-9238-87ee79567149" />

Varmistin vielä tämän menemällä selaimeen ja ottamalla yhteyden omaan localhostiin eli http://localhost ja sain onnistuneen tuloksen.
<img width="1004" height="523" alt="image" src="https://github.com/user-attachments/assets/b5ea4727-204d-4936-9dab-999a3c0c479f" />

## b)
Loin kansiot Caddylle jokaiseen osioon (tasks, handlers, files).
- mkdir /roles/caddy/files/ -p
- mkdir /roles/caddy/handlers/ -p
- mkdir /roles/caddy/tasks/ -p
<img width="1004" height="104" alt="image" src="https://github.com/user-attachments/assets/23963816-f7a6-4f8b-8f79-e41b9676c7c4" />


