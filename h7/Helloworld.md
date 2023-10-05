## x) Linkit
H0 https://github.com/JussiMol/Linux-palvelimet/blob/a11ecad2897b3cf47c072e2f74b66e6e4de91e6f/h0.md <br>
H1 https://github.com/JussiMol/Linux-palvelimet/blob/8c93c8786d0d7789193efcf162f43529db86f58b/h1.md <br>
H2 https://github.com/JussiMol/Linux-palvelimet/blob/8c93c8786d0d7789193efcf162f43529db86f58b/h2/Komentaja%20Pingviini.md <br>
H3 https://github.com/JussiMol/Linux-palvelimet/blob/8c93c8786d0d7789193efcf162f43529db86f58b/h3/HelloWeb.md <br>
H4 https://github.com/JussiMol/Linux-palvelimet/blob/8c93c8786d0d7789193efcf162f43529db86f58b/h4/MaailmaKuulee.md <br>
H5 https://github.com/JussiMol/Linux-palvelimet/blob/8c93c8786d0d7789193efcf162f43529db86f58b/h5/Nimitt%C3%A4in.md <br>
H6 https://github.com/JussiMol/Linux-palvelimet/blob/8c93c8786d0d7789193efcf162f43529db86f58b/h6/Django.md <br>
## y) Tiivistelmä
Itselle <a href="https://terokarvinen.com/2018/hello-python3-bash-c-c-go-lua-ruby-java-programming-languages-on-ubuntu-18-04/"> artikkelin</a> kielistä ainoa kunnolla tuttu on python.<br>
Hello world monella eri kielellä.<br>
## a) Hei maailmat
Tehdään yksinkertaiset hello world ohjelmat Tero Karvisen<a href="https://terokarvinen.com/2018/hello-python3-bash-c-c-go-lua-ruby-java-programming-languages-on-ubuntu-18-04/"> artikkelin</a> ohjeita seuraten Javalla ja C:llä. Pythonilla voi vähän kikkailla kun se on itselle entuudestaan tuttu kieli.<br>
#### Python
Python oli ladattuna virtuaalikoneelle jo jollain aiemmalla oppitunnilla.<br>
Käytin tulostuksessa f-merkkijonoa. Se tulostaa lainausmerkkien sisällön ja {} sulkeissa voidaan käyttää muuttujia ja ohjelma tulostaa seuraavasti. <br>
<br>
![Description](python.png)
#### Java
Javan kanssa seurasin suoraan ohjeita, muutin vaan koodia vähän. <br>
<br>
![Description](java.png)
#### C
C:n kanssa myös ohjeiden mukaan. <br>
<br>
![Description](C.png)
#### Ekstra kieli Rust
Asennan paketinhallinnasta Rust kielen. Ensin piti etsiä mitä asennetaan. <br>
$ sudo apt search rust <br>
Hetken selailin listaa ja päätin että ladataan koko ohjelmointikieli. <br>
$ sudo apt-get install rust-all <br>
<br>
![Description](rust.png)
<br>
Microlla tein hello_world.rs tiedoston ja käännettiin rustrc (tiedostonimi) komennolla <br> 
#### Python laskimena
Laskuoperaattorit <br>
** = potenssi<br>
% = jakojäännös<br>
// = jakolasku (kokonaisluku)<br>
/ = jakolasku (liukuluku)<br>
<br>
![Description](laskin.png)
<br>
#### Shell skripti ja uusi komento
Teen microlla tiedoston helloworld.sh ja sisältö selviää kuvasta. <br>
<br>
![Description](bash.png)
<br>
Komennosta haluttiin kaikille suoritettava, täytyy muokata käyttöoikeuksia <br>
<br>
![Description](bash2.png)
<br>
Chmodilla annetaan eXecute/suoritus oikeudet tiedostoon kaikille käyttäjille. <br>
Testin perusteella se toimii halutusti. <br>
