# H3 Demoni

## x)
### Karvinen 2026
-	Apache2 on verkkopalvelin
-	Apache2 voidaan myös asentaa ja konfiguroida ansiblen avulla
-	Kaikki konfiguraatiohin tehdyt muutokset tulee voimaan vasta, kun käynnistää palvelun uudelleen
-	Roolin hakemistorakenne muodostuu seuraavasti: tasks/, handlers/, files/

### Ansible Community Documentation: Handlers: running operations on change
Handlers – Johdanto
-	Handlerit ovat tehtävä, joka suoritetaan vain jos jokin muu tehtävä ilmoittaa muutoksesta
-	Halutaan suorittaa palvelun uudelleenkäynnistys konfiguraatiotiedoston muuttuessa

Notifying handlers
-	Tällä ”avainsanalla” tehtävä voi kutsua yhden tai useita handlereita
-	Voi olla lista useista handlereista tai yksi merkkijono
-	Handleri suoritetaan vain jos tehtävä muuttuu
  
Ansible-doc service
-	Tarkoitus on hallita palveluiden tilaa
-	Enabled määrittää käynnistyykö palvelu automaattisesti bootin yhteydessä eli se ei vaikuta sen hetkiseen tilaan.
-	Name määrittää palvelun nimen esim. apache2
-	State määrittää palvelun tilan esim, started, stopped, restarted, reloaded
  
EXAMPLE
````
-	Service:
    name: apache2
    state: started
    enabled: yes
````

## a)
Aloitin Apache2 asentamisen samalla tavalla, kuin minkän muun asentamisen eli päivitän järjestelmän "sudo apt-get update" komennolla. Sen jälkeen asensin Apache2 verkkopalvelun komennolla "sudo apt-get install apache2". Loin Apache2 varten kotihakemistooni kansion publicsite ja sinne tein index.html nimisen tiedoston. Index.html tiedostoon kirjoitin yksinkertaisen html koodin ````<h1> Testisivut </h1>````. 

Seuraavaksi loin uuden konfiguraatiotiedoston Apache2 varten. Tänne lisäsin mallin mukaisen konfiguraation, johon tein muutokset, jotka ovat välttämättömiä, jotta se löytää minun hakemistopolkuni.
<img width="1004" height="473" alt="image" src="https://github.com/user-attachments/assets/16acaea7-2ed2-48d9-83c8-8b4991dd2f65" />

Sitten loin linkin "sites-available/example.com.conf" ja "sites-enabled/example.com.conf" välillä, jotta se ottaa sivuston käyttöön. Linkin loin komennolla ````ln -s /etc/apache2/sites-available/example.com.conf /etc/apache2/sites-enabled/example.com.conf````.

Lopuksi vielä ennenkuin testasin sivuni toimivuutta määritin ohjeiden mukaiset oikeudet sivuston kansioille. 
````
- chmod ugo+x /home/aaro/
- chmod ugo+x /home/aaro/publicsite/
- chmod ugo+r /home/aaro/publicsite/index.html
````

Testasin Apache2 configuraation toimivuutta komennolla ````sudo apache2ctl configtest````.
<img width="1004" height="112" alt="image" src="https://github.com/user-attachments/assets/3c2bf31c-6cc9-4bdd-95da-58c5c8b115e4" />

Kun syntaksi oli OK, testasin sivua nettiselaimessa ja se toimi.
<img width="1004" height="398" alt="image" src="https://github.com/user-attachments/assets/b33e3de6-a633-48ad-be8c-fa722b117f32" />


## b)
Tein tismalleen saman alun, kuin Apache2 kanssa eli ajoin päivitykset ja asensin Nginx:n. 


