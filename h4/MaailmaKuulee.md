# Tiivistelmä ensiaskelista virtuaalipalvelimella
Virtuaalipalvelimelle pääset secure shell yhteydellä komennolla. $ sudo ssh root@(IPv4-osoite) <br>
Vahva salasana on pakko, ei suositus <br>
Palomuuriin tehdään aukko portti 22 ja tcp liikenteelle ja otetaan se käyttöön. <br>
Komennoilla<br>
$ sudo ufw allow 22/tcp <br>
$ sudo ufw enable <br>
Luodaan uusi käyttäjä $ sudo adduser (nimi)<br>
Siirretään käyttäjä sudo ryhmään $ sudo adduser (nimi) sudo<br>
Testaa että sudo oikeudet toimivat.<br>
Lukitaan root käyttäjä. $ sudo usermod --lock root <br>
Päivitä paketinhallinta<br>
Asenna esim. apache2 ja tee sinne tarvittavat toimenpiteet (pistä nettisivusi toimimaan)<br>
Avaa palomuuriin portti 80/tcp.<br>
(Karvinen, First Steps on a New Virtual Private Server)
## a) Oma virtuaalipalvelin
Otan palvelun linodesta. <br>
Distribution - Debian 12<br>
Region - Frankfurt,DE (eu-central)<br>
Shared CPU - Nanode 1GB<br>
Root Password - tähän kohtaan vahva salasana<br>
Kaikki loput palvelut voidaan jättää ottamatta sillä ne ei tuota tässä tapauksessa yhtään lisäarvoa. <br>
Create Linode <br>
Menee hetken aikaa kun palvelu pistää koneen pyörimään ja kokeillaan ottaa ssh yhteys omalta virtuaalikoneelta. <br>
Liian hyvä salasana kun ei ekalla muistanut oikein. Sisällä ollaan <br>
<br>
kuva <br>
<br>
## b) Alkutoimenpiteet
Päivitetään paketinhallinta, palomuurille porttien avaukset, uusi käyttäjä ja käyttäjälle sudo oikeudet.<br>
Aloitetaan käyttäjästä. ($ sudo adduser jussi) ja terminaali kysyy tiedot ja kirjoittaa ne levylle. <br>
Kokeillaan toisella terminaalilla että käyttäjä on luotu ja että pääsen sillä sisään koneelle. <br>
Kokeilen sudo echo "Hello" että sudo oikeudet ovat voimassa. <br>
Sitten palomuurille toimenpiteet <br>
Jatkan työskentelyä jussi käyttäjällä kirjaudun rootilta ulos kun se kohta suljetaan kumminkin <br>
Koneella ei ollut asennettuna palomuuria joten $ sudo apt-get install ufw <br>
Millä selvitin asian? $ man ufw ja vastaus oli "No manual entry for ufw". Asentamisen jälkeen aukesi manuaalisivut :) <br>
Asennuksen jälkeen katsotaan mitä asentamisen jälkeinen tilanne on palomuurille. <br>
$ sudo systemctl status ufw <br>
<br>
<br>
Tehdääs palomuuriin aukot.<br>
$ sudo ufw allow 22/tcp <br>
Terminaali sanoo "rules updated" ja "rules updated (v6)" Säännöt päivitetty IPv4 ja v6 osotteille.<br>
$ sudo ufw enable <br>
En tee vielä aukkoa portti 80/tcp ennen kun olen tehnyt Apachella pyörivän sivun joka näytetään ulkomaailmaan. <br>
### c) Palvelin ja sivun vaihto
Apachen ja micro tekstieditorin lataus. <br>
$ sudo apt-get install apache2<br>
$ sudo apt-get install micro <br>
Kun molemmat ohjelmat on asentuneet. -> $ cd var/www/html <br>
$ ls ja katsotaan että index.html on kansiossa. Onhan se. <br>
$ micro index.html ja editorilla muokataan sisältö.<br>
Katsotaan miltä se näyttää terminaalissa. <br>
<br>
kuva <br>
<br>
Sitten avataan portti 80/tcp<br>
$sudo ufw allow 80/tcp ja rules updated ilmoitukset tulevat.<br>
Katsotaas sitten onko nettisivu internetissä <br>
<br>
<br>
