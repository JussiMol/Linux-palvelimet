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
Menee hetken aikaa kun palvelu pistää koneen pyörimään ja kokeillaan ottaa ssh yhteys omalta virtuaalikoneelta. $ ssh root@139.144.73.75 <br>
<br>
![Description](sshlogin.png) <br>
<br>
Liian hyvä salasana kun ei ekalla muistanut oikein. Sisällä ollaan. Etäyhteys toimii <br>
## b) Alkutoimenpiteet
Päivitetään paketinhallinta, palomuurille porttien avaukset, uusi käyttäjä ja käyttäjälle sudo oikeudet.<br>
Palomuurille toimenpiteet <br>
Koneella ei ollut asennettuna palomuuria joten $ sudo apt-get install ufw <br>
Millä selvitin asian? $ man ufw ja vastaus oli "No manual entry for ufw". Asentamisen jälkeen aukesi manuaalisivut :) <br>
Katsotaan minkälaisessa tilassa palomuuri on asennuksen jälkeen. <br>
$ sudo systemctl status ufw <br>
<br>
<br>
![Description](ufwstat.png)
<br>
<br>
Uncomplicated state luultavasti tarkoittaa että ei ole tehty ylimääräisiä määrityksiä ja inactive ettei se oli päällä.<br>
Tehdääs palomuuriin aukot.<br>
$ sudo ufw allow 22/tcp <br>
Terminaali sanoo "rules updated" ja "rules updated (v6)" Säännöt päivitetty IPv4 ja v6 osotteille.<br>
$ sudo ufw enable <br>
<br>
En tee vielä aukkoa portti 80/tcp ennen kun olen asentanut ohjelman ja tehnyt Apachella pyörivän sivun joka näytetään ulkomaailmaan. <br>
Lisätään käyttäjä. ($ sudo adduser jussi) ja terminaali kysyy tiedot ja kirjoittaa ne levylle. <br>
<br>
<br>
![Description](adduser.png)
<br>
<br>
Kokeillaan toisella terminaalilla että käyttäjä on luotu ja että pääsen sillä sisään koneelle. <br>
<br>
<br>
![Description](sisällä.png)
<br>
<br>
Kokeilen sudo echo "Hello" että sudo oikeudet ovat voimassa. <br>
<br>
<br>
![Description](hello.png)
<br>
<br>
Oikeudet voimassa jatketaan eteen päin. <br>
Jatkan työskentelyä omalla käyttäjällä eli kirjaudun root käyttäjältä pois komennolla $ exit
<br>
<br>
![Description](exit.png)
<br>
<br>
Seuraavaksi lukitsen root käyttäjän ja kokeilen pääseekö sille kirjautumaan. <br>
$ sudo usermod --lock root lukitsee root käyttäjän. Testataan pääseekö sille kirjautumaan. <br>
<br>
<br>
![Description](Rootlukossa.png)
<br>
<br>
Ennen kirjautumista mietin antaako terminaali ilmoitusta että onko käyttäjä lukossa. Antoi vasta oikean salasanan jälkeen. <br> 
### c) Palvelin ja sivun vaihto
Apachen ja micro tekstieditorin lataus. <br>
$ sudo apt-get install apache2<br>
$ sudo apt-get install micro <br>
Kun molemmat ohjelmat on asentuneet. -> $ cd var/www/html <br>
$ ls ja katsotaan että index.html on kansiossa. Onhan se. <br>
$ micro index.html ja editorilla muokataan sisältö.<br>
Katsotaan miltä se näyttää terminaalissa. <br>
<br>
![Description](cat.png) <br>
<br>
Sitten avataan portti 80/tcp<br>
$sudo ufw allow 80/tcp ja rules updated ilmoitukset tulevat.<br>
Katsotaas sitten onko nettisivu internetissä <br>
<br>
![Description](testisivu.png)
<br>
Nettisivut näkyvät internettiin. Kaverin vierailu löytyi logeista. Sen tunnistin Windows 11 käyttiksestä ja Opera selaimesta.<br>
## d) Murtautumisyrityksiä
Pistin virtuaalipalvelimen päälle 15.9 kello 15 aikoihin ja teen tämän kohdan 16.9 samoihin aikoihin.<br>
Kokeillaan journalctl -n 2000 ja tarkastellaan muutamat rivit päälle. <br>
Murtautumisyrityksiä on todella paljon. Sen näkee logeista heti. <br>
Esimerkkinä vaikkapa seuraava. <br>
<br>
![Description](yritys.png)
<br>
Väärällä salasanalla yritetty kirjautua käyttäjälle root käyttäen ssh2 yhteyttä portin 39296 kautta. <br>
Katsotaas mitä Google sanoo tuosta IPv4 osoitteesta.<br>
<br>
![Description](redsun.png)
<br>
Yllättyneet nostaa käden. <br>
## Lähteet
Tero Karvinen <br>
https://terokarvinen.com/2017/first-steps-on-a-new-virtual-private-server-an-example-on-digitalocean/
