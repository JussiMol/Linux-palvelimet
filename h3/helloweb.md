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
Paketinhallinta tekee työnsä. Nyt voidaan kokeilla onko se päällä. <br>
