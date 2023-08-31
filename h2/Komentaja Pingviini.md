# Tärkeimmät komennot
$ pwd - print working directory. Missä hakemistossa ollaan/työskennellään tällä hetkellä. <br>
$ ls - list files. Listaa hakemiston tiedostot.<br>
$ cd (hakemisto) - change directory. Vaihda hakemistoa.<br>
$ cd .. - change directory up. Vaihda hakemistoa yhden ylös.<br>
$ mkdir (hakemiston nimi) - Make directory. Luo uuden hakemiston. <br>
$ mv (nimi) (kohde) - Move. Siirrä (tiedosto)(minne)<br>
$ cat (tiedosto) . Tulostaa komentokehotteeseen tiedoston sisällön.<br>
*** Poistokomennot tekee sitten työtä käskettyä ja ne eivät varmistuksia kysele. Tarkkana niiden käytössä. *** <br>
$ rm (tiedosto) . Remove. Poistaa tiedoston  <br>
$ rmdir (hakemisto) . Remove directory. Poistaa hakemiston<br>
$ man (komennon nimi) . Manual. Näyttää komennon ohjesivun.<br>
<br>
Lähde (Tero Karvinen, Command Line Basics Revisited) <br>
## Ennen kuin tehdään mitään muuta
Päivitetään pakettienhallinta niin saadaan varmasti uusimmat versiot.<br>
Kuvassa ei näy, mutta terminaali kysyy myös salasanan pääkäyttäjän oikeuksille.<br>
<br>
![Description](apt-upgrade.png)
## Micro tekstieditori
Ajetaan komento $ sudo apt install micro. <br>
Huom. Asensin jo oppitunnilla micron niin terminaalin tuloste saattaa näyttää sinulla erilaiselta. <br>
Myös ennen ohjelman asennusta terminaali kysyy. Do you want to continue [y/n] kirjoita Y ja enter. <br>
<br>
![Description](micro.png)
<br>
Kuvasta näkee ettei tässä tapauksessa tapahtunut mitään, ei asennusta, ei päivitystä.<br>
Homma valmis.<br>
## Järjestelmätiedot
Aluksi piti asentaa lshw (list hardware) työkalu. sudo apt install lshw. <br>
Komennolla $ sudo lshw - short -sanitize saadaan näkyville seuraavat tiedot.<br>
<br>
![Description](rauta.png)
<br>
Listasta ensimmäisenä etsin punaisella viivalla merkityt. <br>
Keskusmuisti 4 gigatavua. Aivan kuten asennuksessa määriteltiin.<br>
Prosessori on sama kuin host koneessa. <br>
Kovalevytila. Se on jostain syystä 21 gigatavua. Ei mitään hajua miksi. Asennuksessa määriteltiin 20GB.<br>
Ilmeisesti 20GB + käyttöjärjestelmän viemä tila? <br>
Display SVGA? Jotain Virtualboxin taikoja. Ymmärtäisin jos olisi HDMI. <br>
Mikäli perehtyisi Virtualboxin sielunelämään enemmän voisi ymmärtää mitä kaikkea se emuloi ja miten.<br>
Hiiri, näppäimistö ja kuulokkeet toimivat ok. Ne näyttävät listastakin löytyvän. <br>
## Kolme ohjelmaa
Ensimmäiseksi ohjelmaksi valikoitui VLC media player. <br>
$ sudo apt install vlc. Haluanko jatkaa? Yes.<br>
Ohjelma asennettu. Avautuu komennolla vlc tai vlc source mikäli on joku media mitä ajaa ohjelmassa.<br>
Ihan perus ohjelma videoiden katseluun.<br>
<br>
![Description](vlc.png)
<br>
Toinen ohjelma olisi sitten Wireshark Network Analyzer.<br>
Tällä voidaan analysoida verkkoliikennettä.<br>
$ sudo apt install wireshark <br>
Asentaessa kysyy voiko muutkin kuin pääkäyttäjät tallentaa verkkoliikennettä. Ei kyllä anneta siihen oikeuksia. <br>
<br>
![Description](wireshark.png)
<br>
Nopealla vilkaisulla näytti blue screeniltä, mutta eipä kaatunutkaan.<br>
<br>
![Description](wireshark1.png)
<br>
Testasin Googlaamatta komentoa millä lähtisi ohjelma päälle ja näköjään wireshark riitti siihen.<br>
<br>
Kolmas ohjelma terminaalissa toimiva speedtest.<br>
curl komennolla joudutaan hakemaan nettisivulta tiedot ohjelmasta.<br>
$ curl -s https://packagecloud.io/install/repositories/ookla/speedtest-cli/script.deb.sh | sudo bash <br>
$ sudo apt-get install speedtest <br>
Ohjelma asennettu tuttuun tapaan <br>
<br>
![Description](speedtest.png)
<br>
Valokuitu käy ja kukkuu. ( ͡° ͜ʖ ͡°) <br>
## Tärkeimmät hakemistot

