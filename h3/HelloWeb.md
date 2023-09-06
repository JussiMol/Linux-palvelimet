e# Hello Web<br>
## x) Install Apache Web Server on Ubuntu
Komento asennukselle $ sudo apt-get install apache2. Löytyy suoraan paketinhallinnasta.<br>
Voit kokeilla onko sivu päällä automaattisesti verkkoselaimella. Osoite http://localhost <br>
Voit muokata kotisivuja lisäämällä public_html kotihakemistoosi. <br>
Oikeudet kotisivujen luomiseen pitää antaa komennolla. $ sudo a2enmod userdir <br>
Tämä komento muokkaa Apachen konfiguraatiotiedostoja.<br>
Muutosten voimaantulo vaatii Apachen uudelleenkäynnistyksen. Komento $ sudo systemctl restart apache2. <br>
#### Kotisivujen testaus
$ cd komennolla kotihakemistoon. <br>
$ mkdir public_html tehdään kansio mihin laitetaan nettisivun vaatimat tiedostot. <br>
$ whoami komennolla voit selvittää käyttäjänimesi. <br>
http://localhost/~(nimi)/ <br>
Jos näät kotisivun olet asentanut onnistuneesti palvelimen kotisivuille. <br>
<br>
(Karvinen, Install Apache Web Server on Ubuntu)<br>
## a) Apachen asennus
Apache löytyy suoraan paketinhallintajärjestelmästä eli suoritetaan komento.<br>
$ sudo apt-get install apache2 <br>
Paketinhallinta tekee työnsä. Nyt voidaan kokeilla onko palvelin päällä. <br>
Palvelimen tilan voi tarkastaa joko terminaalilla tai verkkoselaimella.
http://localhost url-palkkiin <br>
Terminaalilla $ sudo systemctl status apache2 <br>
<br>
![Description](apache.png) <br>

Palvelin on päällä. <br>
Jos palvelin ei olisi päällä. Selain sanoisi Unable to connect. <br>
Ja terminaalissa $ sudo systemctl status apache2 näyttäisi seuraavaa. <br>

![Description](apache2.png)<br>
### b) Lokitiedot
![Description](logi.png)<br>
Analysoidaan alin rivi eli uusin kotisivua koskeva pyyntö.<br>
127.0.0.1 - IP-osoite on koneen mistä pyyntö hakea nettisivu on tullut. Kyseessä on isäntäkone, eli sama kone millä palvelin pyörii.<br>
<br>
Tarkistin koneen ip-osoitteen komennolla $ ip addr ja se täsmää 127.0.0.1 kanssa. <br>
<br>
"- -" kohdassa olisi käyttäjätunnus ja/tai käyttäjäryhmä. Tiedon puuttuessa se on korvattu viivalla. Luultavasti LAN-verkossa nimet olisi näkyvillä? <br>
<br>
Päivämäärä, aika ja aikavyöhyke. <br>
<br>
GET = HTTP-metodi verkkosivujen hakemiseen.<br>
<br>
HTTP/1.1 on pyynnössä käytetty protokollan versio.<br>
<br>
Seuraava tieto on arvokas. Luku 200 on vastauskoodi. Se tarkoittaa, että pyyntö onnistui ja palvelin lähetti pyydetyt tiedot takaisin.<br>
<br>
3380 = Palautettujen tavujen määrä kyselyn tekijälle.<br>
<br>
Rivistä loput kertoo kyselyn tekijän verkkoselaimen ja käyttöjärjestelmän tietoja/versioita.<br>
<br>
Kuvassa voidaan myös huomata esim toiseksi ylimmällä rivillä epäonnistunut yritys pyytää verkkosivu.<br>
<br>
Vastauskoodi 404. Epäonnistunut yritys ja palautettujen tavujen määrä paljon pienempi.<br>
<br>
(Apache Software Foundation, Log Files)
<br>

## c) Default sivun vaihtaminen
Tähän toimenpiteeseen löytyy ohje suoraan Apachen esimerkkisivulta.<br>
![Description](ohje.png)<br>
Mennään terminaalissa $ cd /var/www/html <br>
$ micro index.html
Korvataan sisältö omalla ja tallennetaan. <br>
Sivu näyttää nyt tältä. <br>
![Description](index.png)<br>
<br>

## d) Käyttäjien kotisivut
Komennolla $ sudo a2enmod userdir. Muokataan Apachen konfiguraatiota ja annetaan käyttäjille oikeudet luoda kotisivuja.<br>
Tehdään kotihakemistoon /home/jussi kansio public_html komennolla $ mkdir public_html <br>
Tein html tiedoston microlla ja sisältö näyttää seuraavalta. <br>
<br>
![Description](oma.png) <br>
Katsotaan miltä se näyttää selaimessa. <br>
<br>
![Description](deny.png) <br>
Eipä toiminut.  <br>
Pitää ajaa komento joka muuttaa tiedostojen ja hakemistojen käyttöoikeuksia.<br>
$ sudo chmod ugo+x $HOME $HOME/public_html/ <br>
Käytännössä tämä komento antaa käyttäjille, ryhmille ja muille suoritusoikeuden kotihakemistoosi /home/jussi ja sen alahakemistoon public_html.<br>
<br>
![Description](omasivu.png)<br>
<br>
Näyttäisi toimivan. <br>
## f) Curl komennot
Pelkkä curl komento hakee annetun url-osoitteeseen liittyvän sivun sisällön ja tulostaa sen komentoriville.<br>
<br>
![Description](curl.png)<br>
<br>
curl -I komento tekee sivustolle head pyynnön joka tulostaa otsikkotiedot, mutta ei itse sivun sisältöä.  <br>
<br>
![Description](curl1.png)<br>
<br>


https://httpd.apache.org/docs/2.4/logs.html
