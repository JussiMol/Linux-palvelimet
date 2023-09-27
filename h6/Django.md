# x) Tiivistelmät
### Python Web Idea
Opit tekniikoita, joka
- Palvelee asiakkaita kaikilla alustoilla
- Kerää tietoa miten palvelua käytetään. (lokit)
- Antaa monien käyttäjien muokata tietoa yhtä aikaa
- Toimii asentamatta mitään
- Käyttää uusinta ohjelmaversiota<br>
(Karvinen, Python Web - Idea to Production - 2023)<br>
### Django tietokanta tutoriaali
Edellytyksinä, linux asennettuna ja Linux komentokehotteen käyttö.<br>
Kehitysympäristön asennus ohjeet ja virtualenv (kehitysympäristö) ensiaskeleet.<br>
Kun työskennellään virtualenvissä, komentokehotteessa kuuluu lukea (env) komentorivin alussa.<br>
Pakettien asennuksessa pitää käyttää harkintaa ja suorittaa niitä vain (env) tilassa. Älä käytä sudoa.<br>
Kehityspalvelinta ei parane näyttää internettiin.<br>
Ohjeet adminin ja käyttäjien luontiin.<br>
Tietokannan luomisen ohjeet ja käyttäjien lisääminen tietokantaan.<br>
(Karvinen, Django 4 Instant Customer Database Tutorial)
### Django tuotantoasennus
Esivaatimukset, Linux komentokehotteen käyttö, virtuaalipalvelin ja testiympäristö (virtuaalikone).<br>
Projektia varten tarvitset Apache2 web-palvelimen, virtuaalihostin ja web-sivun jossa on sisältöä.<br>
Django projektin joka tehdään virtualenv ympäristöä käyttäen.<br>
Djangon ja Apachen yhdistämisessä tarvitaan 3 hakemistopolkua. Django projektin mistä löytyy manage.py tiedosto, Polku wsgi.py tiedostoon ja Virtualenv site-packages hakemisto.<br>
Copy-pastea tiedostopolkuja ja vältä kirjoitusvirheet = debug tarve vähenee.<br>
/etc/apache2/sites-available/ konfiguraatiotiedosto vaatii nyt enemmän kuin pelkän virtualhostin<br>
Debug moodi kannattaa poistaa käytöstä, ettei paljasta ylimääräistä tietoa hakkereille tms.<br>
## a) Djangon asennus
Aloitetaan seuraamalla<a href="https://terokarvinen.com/2022/django-instant-crm-tutorial/"> Karvisen ohjeita</a> Djangon asennukseen ja siitä tietokannan rakentamiseen. <br>
Teen tehtävän omalla paikallisella virtuaalikoneelle.<br>
$ sudo apt-get update ja upgrade perään. Paketinhallinta päivitetty. <br>
$ sudo apt-get -y install virtualenv - asennetaan virtualenv ympäristö. -y on automaattinen "yes" vastaus yes/no kyselyihin.<br>
$ virtualenv --system-site-packages -p python3 env/ Tällä komennolla luodaan virtuaaliympäristö joka pääsee käsiksi järjestelmän paketteihin ja luo env/ hakemiston.<br>
Katsotaan tekikö komento hakemiston.<br>
<br>
![Description](env.png) <br>
<br>
hakemisto löytyy otetaan nopea vilkaisu sisältöön. <br>
<br>
![Description](sis.png) <br>
<br>
Ei mennä liian syvälle, löytyy sym-link tiedostoja (cyan) ja suoritettavia tiedostoja (vihreä). <br>
$ source bin/activate riittää koska olen jo /env hakemistossa. Aloitetaan käyttämään env ympäristöä.<br>
/home/jussi/env/bin/pip<br>
Luodaan /home/jussi/env hakemistoon requirements.txt sisältö "django" <br>
$ pip install -r requirements.txt - Asennetaan pythonin paketinhallinnalla tiedoston sisällä määritellyt paketit.<br>
<br>
![Description](pip.png) <br>
<br>
Lopputulos django 4.2.5 versio<br>
<br>
![Description](django.png) <br>
<br>
Django framework on nyt onnistuneesti asennettu.<br>
### b) Projekti tietokannalla
Aloitetaan django projekti.<br>
$ django-admin startproject testikanta <br>
Tarkistetaan mihin hakemisto luotiin <br>
<br>
![Description](testikanta.png) <br>
<br>
Helpottaa tilannekuvan hahmottamista suorittaa näitä tarkistuksia.<br>
Kokeillaas sitten toimiiko kehityspalvelin<br>
$ cd testikanta<br>
$ ./manage.py runserver<br>
<br>
![Description](toimpro.png) <br>
<br>
Starting development server at http://127.0.0.1:8000/ -> Firefox ja url http://127.0.0.1:8000/<br>
<br>
![Description](toim.png) <br>
<br>
Palvelin toimii onnistuneesti. <br>
### Admin interface
Kirjautumissivut ovat olemassa mutta ei käytössä<br>
Päivitetään tietokanta.<br>
$ ./manage.py makemigrations<br>
$ ./manage.py migrate<br>
Tuloste on seuraava <br>
<br>
![Description](migrate.png) <br>
<br>
Ensimmäinen komento ei tehnyt mitään muutoksia mutta migrate komento ilmeisesti otti käyttöön joitain tietokantarakenteita.<br>
Lisätään käyttäjä. <br>
$ ./manage.py createsuperuser<br>
<br>
![Description](csu.png) <br>
<br>
Kysyy tiedot, syötetään ne. Palvelin päälle $ ./manage.py runserver <br>
URL - http://127.0.0.1:8000/admin/<br>
<br>
![Description](kir.png) <br>
<br>
Kirjaudun laittamillani tiedoilla.<br>
<br>
![Description](adm.png) <br>
<br>
Sisällä ollaan, kirjautuminen toimii.<br>
Tehdään uusi käyttäjä Users kohdasta vihreästä plus merkistä<br>
Annetaan käyttäjänimeksi esmes ja hyvä salasana <br>
esmessille staff ja superuser ryhmät että voi muokata tietoa. <br>
Permissions kohdasta laitetaan staff ja superuser laatikoihin täpät ja sivun alaosasta save <br>
Kokeillaan kirjautua<br>
<br>
![Description](esmes.png) <br>
<br>
esmes on sisällä, käyttäjän lisäys onnistui. <br>
### CRM tietokanta
Uusi hakemisto crm sovellukselle<br>
$ ./manage.py startapp crm<br>
<br>
![Description](crm.png) <br>
<br>
Lisätään crm testikanta/settings.py tiedostoon INSTALLED_APPS osioon.<br>
$ micro testikanta/settings.py<br>
<br>
![Description](set.png) <br>
<br>
Sitten muokataan crm hakemiston sisältöjä. <br>
$ micro crm/models.py<br>
<br>
![Description](models.png) <br>
<br>
Tällä saadaan luotua "customer" taulu tietokantaan "name" sarakkeella<br>
Tuodaan uudet tietokannan rakenteet. <br>
$ ./manage.py makemigrations<br>
$ ./manage.py migrate<br>
<br>
![Description](migrate2.png) <br>
<br>
Tällä kertaa makemigrations haki tietokantarakenteen. Joka olettaen tekee tietokantaan tuon customer taulun <br>
Ja migrate komento otti sen käyttöön. <br>
Jotta muutokset nähtäisiin ne täytyy rekisteröidä <br>
$ micro crm/admin.py<br>
<br>
![Description](admin.png) <br>
<br>
Palvelin päälle ja katsotaan mitä on tehty. <br>
$ ./manage.py runserver<br>
<br>
![Description](crm2.png) <br>
<br>
CRM ja pari asiakasta lisätty onnistuneesti. <br>
Asiakkaille nimet lisäämällä models.py tiedostoon metodi joka palauttaa customer olion nimen.<br>
<br>
![Description](models2.png) <br>
<br>
Palvelin päälle ja katsotaan muuttuiko nimet. <br>
<br>
![Description](asiakkaat.png) <br>
<br>
Asiakkaiden nimet näkyy normaalisti, tehtävä suoritettu <br>
### c)Tuotantotyyppinen asennus
Seurataan <a href="https://terokarvinen.com/2022/deploy-django/"> Karvisen ohjeita</a> djangon tuotantoasennukseen<br>
Listataan alkunu mitä kaikkea omalla virtuaalikoneella on jo valmiina<br>
- Apache2
- micro
- /var/www/html/index.html apachen vakiosivu vaihdettuna
- /home/jussi/public_html löytyy index.html
- Djangolla tehty projekti<br>
Aloitetaan siis luomalla virtualhost.<br>
$ sudoedit /etc/apache2/sites-available/testikanta.conf <br>
<br>
![Description](asiakkaat.png) <br>
<br>
### Lähteet
Tero Karvinen <br>
Python Web - Idea to Production - 2023<br>
https://terokarvinen.com/2023/python-web-idea-to-production/#osaamistavoitteet<br>
Django 4 Instant Customer Database Tutorial<br>
https://terokarvinen.com/2022/django-instant-crm-tutorial/<br>
Deploy Django 4 - Production Install<br>
https://terokarvinen.com/2022/deploy-django/<br>
