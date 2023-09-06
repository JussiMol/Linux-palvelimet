# Hello Web<br>
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
## a) Apachen asennus
Apache löytyy suoraan paketinhallintajärjestelmästä eli suoritetaan komento.<br>
$ sudo apt-get install apache2 <br>
Paketinhallinta tekee työnsä. Nyt voidaan kokeilla onko palvelin päällä. <br>
Palvelimen tilan voi tarkastaa joko terminaalilla tai verkkoselaimella.
http://localhost url-palkkiin <br>
Terminaalilla $ sudo systemctl status apache2 <br>
<br>
![Description](apache.png)
<br>
Palvelin on päällä. <br>
Jos palvelin ei olisi päällä. Selain sanoisi Unable to connect. <br>
Ja terminaalissa $ sudo systemctl status apache2 näyttäisi seuraavaa. <br>
<br>
![Description](apache2.png)
<br>
