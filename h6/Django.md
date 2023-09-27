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
### a) Djangon asennus
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
Ei mennä liian syvälle, löytyy hakemistoja ja suoritettavia tiedostoja. <br>
$ source bin/activate riittää koska olen jo /env hakemistossa. Aloitetaan käyttämään env ympäristöä.
/home/jussi/env/bin/pip
Luodaan /home/jussi/env hakemistoon requirements.txt sisältö "django" 
<br>
![Description](pip.png) <br>
<br>




### Lähteet
Tero Karvinen <br>
Python Web - Idea to Production - 2023<br>
https://terokarvinen.com/2023/python-web-idea-to-production/#osaamistavoitteet<br>
Django 4 Instant Customer Database Tutorial<br>
https://terokarvinen.com/2022/django-instant-crm-tutorial/<br>
Deploy Django 4 - Production Install<br>
https://terokarvinen.com/2022/deploy-django/<br>
