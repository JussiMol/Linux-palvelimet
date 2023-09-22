# x) Tiivistelmä
### Uusi vakiosivu Apachelle
- Apachen asennusohjeet.
- Apachen default sivu on käytännössä virtual host.
- Saatavilla olevat sivut mutta ei välttämättä aktiiviset virtual hostit löytyvät /etc/apache2/sites-available/ hakemistosta. Tekstitiedoston sisältä.
- Uuden virtualhostin voi tehdä tekemällä uuden konfiguraatiotiedoston yllä mainittuun hakemistoon.
- Tiedostoon pitää laittaa käytetty portti, documentroot (tiedoston sijainti) ja oikeudet hakemiston käyttöön.
- $ sudo a2ensite (nimi).conf otetaan virtual host käyttöön ja komennolla $ sudo a2dissite 000-default.conf default sivu pois käytöstä.
- Näiden jälkeen uudelleen käynnistys apachelle.
- Uusi index.html sivu täytyy olla samassa sijainnissa minkä kirjoitit host tiedostoon.<br>
(Karvinen, New Default Website with Apache2 – Show your homepage at top of example.com, no tilde)<br>
### Virtuaalinen nimipalvelu (Karvinen)
- Palvelinympäristön asennus
- Uusi sivusto nimipalvelulla tehdään uusi konfiguraatiotiedosto /etc/apache2/sites-available/ hakemistoon.
- $ sudo a2ensite (tiedosto) ja uudelleenkäynnistys apache2.
- Luo kotihakemistoosi index.html tiedosto ja sille sisältö.
- Hosts tiedostolla voidaan manipuloida paikallisesti sivustojen nimiä.
- Normaalisti vuokraamme nimen nimipalvelusta.<br>
(Karvinen, Name Based Virtual Hosts on Apache – Multiple Websites to Single IP Address)<br>
### Virtuaalinen nimipalvelu (Apache)
- Asiakas ilmoittaa palvelimelle mitä sivua haetaan ja palvelin osaa palauttaa header tietojen perusteella oikean sivuston.
- Pyynnön saapuessa palvelin hakee parhaan/tarkimman parin virtualhost listasta ja palauttaa sen asiakkaalle.
- Jokainen sivu täytyy olla erillisessä <virtualhost> osiossa ja sen täytyy sisältää hakemistopolku html tiedostoon.<br>
(Apache, Name-based Virtual Host Support)<br>
### a) Nimen vuokraus












### Lähteet
Tero Karvinen <br>
New Default Website with Apache2 – Show your homepage at top of example.com, no tilde<br>
https://terokarvinen.com/2016/02/16/new-default-website-with-apache2-show-your-homepage-at-top-of-example-com-no-tilde/ <br>
Name Based Virtual Hosts on Apache – Multiple Websites to Single IP Address<br>
https://terokarvinen.com/2018/04/10/name-based-virtual-hosts-on-apache-multiple-websites-to-single-ip-address/<br>
