# h4 Kääntopaikka | Nathaniel Ssendagire 9.9.2025

## Ympäristö
OS: Debian GNU/Linux 12 Bookworm

Browser: Firefox 128.3.1esr (64-bit)

Hardware Model: VMWare Workstation Pro Memory: 4.0 GB

Processor: AMD Ryzen 3 7320U - 4 cores used

Disk: 35 GB

Network: NAT

## a) Asenna Ghidra.

- Asensin Ghidran tällä komennolla "sudo apt-get install ghidra. Käytän kali linuxia niin se lataus toimi sillä.

## x) Lue/katso/kuuntele ja tiivistä. (Tässä x-alakohdassa ei tarvitse tehdä testejä tietokoneella, vain lukeminen tai kuunteleminen ja tiivistelmä riittää. Tiivistämiseen riittää muutama ranskalainen viiva.)

- Tekijä selittää asiat rennosti ja vaihe vaiheelta, mikä tekee videosta helposti seurattavan, vaikka kaikki työkalut eivät olisi entuudestaan tuttuja.

- Oli mielenkiintoista nähdä, miten ensin kokeiltiin yksinkertaisia komentoja ja sitten siirryttiin raskaampaan työkaluun (Ghidra), kun se oli tarpeen.

- Huomasin, että reverse engineeringissä tärkeintä ei ole heti tietää kaikkea, vaan uskaltaa kokeilla ja opetella yrityksen ja erehdyksen kautta.

- Videosta jää fiilis, että vaikka Ghidra näyttää monimutkaiselta, sen kanssa oppii parhaiten vain käyttämällä sitä rohkeasti käytännössä.

## b) rever-C. Käänteismallinna packd-binääri C-kielelle Ghidralla. Etsi pääohjelma. Anna muuttujielle kuvaavat nimet. Selitä ohjelman toiminta. Ratkaise tehtävä binääristä, ilman alkuperäistä lähdekoodia
<img width="480" height="567" alt="Packdrever" src="https://github.com/user-attachments/assets/f5c35f43-9cbd-4ff6-a2a6-50d5a0c5eba2" />

Tässä oli alkuperäinen purettu koodi ghidralla, kuten huomaat kuvassa on vähän erikoisia muuttujia, selkensin koodia nimeämällä jännän näköiset muuttujat yksinkertaisimmiksi.

<img width="447" height="431" alt="packdrever_fix" src="https://github.com/user-attachments/assets/70fe7ba5-af21-4b4d-8871-1f8d4dca9f32" />

## Yleinen Yhteenveto koodin toiminnallisuudesta

Tämä on yksinkertainen salasanan tarkistusohjelma. Se kysyy käyttäjältä salasanaa, vertaa sitä kovakoodattuun oikeaan salasanaan ("pillos-AnAnAs") ja tulostaa "lipun" (onnistumisviestin), jos se täsmää, tai epäonnistumisviestin, jos se ei täsmää.

## Rivi Riviltä Selitys

Rivi 2: int main(void)
Tämä on main-funktion alku, C-ohjelman pääsyökohta. int tarkoittaa, että se palauttaa kokonaisluvun (yleensä 0 onnistumisen merkiksi), ja (void) tarkoittaa, että se ei ota argumentteja.

Rivi 4: {
Aaltosulje merkitsee main-funktion koodilohkon alkua.

Rivi 5: int salasana_tarkistus;
Deklarointi: Tämä esittelee kokonaislukumuuttujan nimeltä salasana_tarkistus.
Tarkoitus: Tätä muuttujaa käytetään myöhemmin käyttäjän syötteen ja oikean salasanan vertailun tuloksen tallentamiseen.

Rivi 6: char password [32];
Deklarointi: Tämä esittelee merkkitaulukon nimeltä password, jonka pituus on 32 alkiota.
Tarkoitus: Tämä on puskuri (varattu muistilohko), johon ohjelma tallentaa käyttäjän kirjoittaman salasanan.

Rivi 8: puts("What\'s the password?");
Funktiokutsu: puts-funktio (lyhenne sanoista "put string") tulostaa lainausmerkkien sisällä olevan tekstin standarditulosteeseen (yleensä konsoliin/terminaaliin).
Tuloste: Tämä rivi tulostaa kehotteen: What's the password? kysyäkseen käyttäjältä syötettä.

Rivi 9: __isoc99_scanf(&DAT_001020ld,password);
Funktiokutsu: Tämä on kutsu scanf-funktiolle (sen variantti C99-standardia varten), joka lukee syötettä standardisyötteestä (yleensä näppäimistö).

Rivi 10: salasana_tarkistus = strcmp(password,"pillos-AnAnAs");
Funktiokutsu & Sijoitus: strcmp-funktio (string compare) vertaa kahta merkkijonoa.
Argumentit: Se vertaa käyttäjän syöttämää merkkijonoa (password) kovakoodattuun merkkijonoon "pillos-AnAnAs".
Paluuarvo:
Palauttaa 0, jos merkkijonot ovat identtiset.
Palauttaa arvon pienemmän kuin 0, jos ensimmäinen merkkijono on toista "pienempi" (aakkosjärjestyksen perusteella).
Palauttaa arvon suuremman kuin 0, jos ensimmäinen merkkijono on toista "suurempi".
Tarkoitus: Tämän vertailun tulos tallennetaan salasana_tarkistus-muuttujaan.

Rivi 11: if (salasana_tarkistus == 0) {
Ehtotarkistus: Tämä if-lauseke tarkistaa salasana_tarkistus-muuttujan arvon.
Logiikka: Ehto == 0 on totta vain, jos strcmp:n vertaamat kaksi merkkijonoa olivat täsmälleen samat. Tämä on haara oikealle salasanalle.

Rivi 12: puts("Yes! That\'s the password. FLAG(fero-0e3bed0a89)");
Funktiokutsu: Tämä puts-kutsu suoritetaan vain, jos yllä olevan if-lausekkeen ehto oli totta (eli salasana oli oikein).
Tuloste: Se tulostaa onnistumisviestin: Yes! That's the password. FLAG(fero-0e3bed0a89).

Rivi 13: }
Sulkee if-lausekkeen koodilohkon.

Rivi 14: else {
else-haara. Tämä merkitsee koodilohkon alkua, joka suoritetaan vain, jos edellisen if-lausekkeen ehto oli epätosi (eli salasana oli väärin).

Rivi 15: puts("Sorry, no bonus.");
Funktiokutsu: Tämä puts-kutsu suoritetaan vain, jos salasana oli väärin.
Tuloste: Se tulostaa epäonnistumisviestin: Sorry, no bonus..

Rivi 16: }
Sulkee else-haaran koodilohkon.

Rivi 17: return 0;
Paluuarvon Asetus: Tämä komento lopettaa main-funktion suorituksen ja palauttaa arvon 0 käyttöjärjestelmälle.
Tarkoitus: Arvo 0 konventiona merkitsee, että ohjelma suoritettiin onnistuneesti ilman virheitä.

Rivi 18: }
Loppuaaltosulje merkitsee main-funktion koodilohkon loppua.

## c) Jos väärinpäin. Muokkaa passtr-ohjelman binääriä (ilman alkuperäistä lähdekoodia) niin, että se hyväksyy kaikki salasanat paitsi oikean. Osoita testein, että ohjelma toimii

Kun suoritin tiedostoa niin se pyysi salasanaa ja tietenkin jos laittaa väärän niin se vastaa "Sorry no bonus" 

<img width="190" height="128" alt="passtr_file_og" src="https://github.com/user-attachments/assets/0f44f336-f8eb-43fb-8ea1-7c098c1805f1" />

Se, miten sain ohjelman hyväksymään minkä tahansa salasanan (kunhan se ei ollut juuri se oikea salasana). Ratkaisu oli aika yksinkertainen: koodissa / Decompile:main -kohdassa klikkasin sitä if-funktiota, jolloin pääsin suoraan siihen osaan, jossa salasanaa tarkistetaan. Siellä muokkasin ehtoa poistamalla käskystä "JNZ"-komennon kirjaimen N pois. Tämän muutoksen jälkeen ohjelma alkoi hyväksyä salasanan.

## Selitys

Syy miksi se toimi on koska alkuperäinen JNZ tarkoittaa “jump if not zero”, eli hyppää toiseen kohtaan vain jos edellisen operaation tulos ei ole nolla. Salasanan tarkistuksessa tämä tarkoittaa, että ohjelma hyppää väärään kohtaan, kun salasana on oikea. Kun poistetaan N ja käytetään JZ (“jump if zero”), hyppy tapahtuu vain, jos tulos on nolla, eli vertailu onnistuu, ja ohjelma hyväksyy salasanan. Käytännössä logiikka kääntyi oikeaksi.

<img width="1402" height="656" alt="passtr_ghidra" src="https://github.com/user-attachments/assets/0b94d67b-820d-4857-bf5a-5cf57320ab4d" />

<img width="650" height="471" alt="passtr_file (1)" src="https://github.com/user-attachments/assets/e2fe472b-cf00-45b3-9b43-c586b9e29be4" />

## e) Nora crackme01. Ratkaise binääri.

<img width="532" height="487" alt="crackme01_explanation" src="https://github.com/user-attachments/assets/4d9f9949-7a5f-4760-8f6d-a2a82c9a0382" />


## Mitä ohjelma tekee? 
Tämä ohjelma on salasanantarkistin, joka suoritetaan komentoriviltä. Sen tarkoitus on, että se hylkää salasanan, jos se alkaa sanalla "password", ja hyväksyy sen takia minkä tahansa muun salasanan.

## Selitys Riviltä

if (param_1 == 2) {
- Tarkistaa, että ohjelmalle on annettu tasan yksi komentoriviparametri (esim. ./ohjelma salasana). param_1 on argumenttien määrä (argc).

__n = strlen("password!");
- Laskee merkkijonon "password!" pituuden. Tulos on 9 (kirjaimet p-a-s-s-w-o-r-d-!).

iVar1 = strncmp(..., "password1", __n);
- Tämä on tärkein rivi. Se vertaa käyttäjän antamaa salasanaa (param_2 + 8 on argv[1]) oikeaan salasanaan "password1".

- MUTTA: Vertailu tehdään vain ensimmäisten 9 merkin osalta (__n on 9).

- Tämä tarkoittaa: Ohjelma ei vertaile koko salasanaa, vaan vain sen 9 ensimmäistä merkkiä. Se vertaa siis käyttäjän syötettä merkkijonoon "password" (9 ensimmäistä merkkiä sanasta "password1").

if (iVar1 == 0) {
- Jos vertailun tulos on 0, eli käyttäjän syötteen 9 ensimmäistä merkkiä olivat "password", ohjelma suorittaa VÄÄRÄN salasanan haaran.
- Tämä on ohjelman "juoni"! Oikea salasana on password1, mutta ohjelma torjuu sen, koska se alkaa merkeillä password.

Haarat:
- if-haara (vertailu == 0): Tulostaa "No, %s is not correct." Käyttäjä antoi salasanan, joka alkaa merkeillä password. Tämä on väärä vastaus.
- else-haara (vertailu != 0): Tulostaa "Yes, %s is correct!" Käyttäjä antoi salasanan, joka ei ala merkeillä password. Tämä on oikea vastaus.

Yhteenveto / Vastaus

Ohjelma haluaa, että salasana ei ole "password1", vaan jokin toinen salasana, joka ei ala kirjaimilla "password".

Oikea vastaus on siis mikä tahansa salasana, joka ei ole password-alkuinen. Esimerkiksi:

- oikeasalasana

- 123

- abc
## e) Nora crackme01e. Ratkaise binääri
<img width="583" height="497" alt="crackme01e_explanation" src="https://github.com/user-attachments/assets/4cef264c-30e1-43ad-8d8a-d95bf04abd81" />

## Mitä ohjelma tekee?
Tämä ohjelma on salasanantarkistin, joka vaatii salasanan komentoriviparametrina. Toisin kuin edellinen, se hyväksyy salasanan vain, jos se alkaa merkeillä "slm!paas.k". Ohjelma vertailee syötettä vain tämän merkkijonon pituuden verran, joten oikea salasana on slm!paas.k (tai jokin pidempi merkkijono, joka alkaa näillä merkeillä).

## Selitys Riviltä

if (param_1 == 2) {
- Tarkistaa, että ohjelmalle on annettu tasan yksi komentoriviparametri (esim. ./ohjelma salasana). param_1 on argumenttien määrä (argc).

_n = strlen("slm!paas.k");

- Laskee merkkijonon "slm!paas.k" pituuden. Tulos on 10 (merkit s-l-m-!-p-a-a-s-.k).

iVar1 = strncmp(..., "slm!paas.k", _n);

- Vertaa käyttäjän antamaa salasanaa (param_2 + 8 on argv[1]) oikeaan salasanaan "slm!paas.k".

- Vertailu tehdään vain ensimmäisten 10 merkin osalta (_n on 10).

if (iVar1 == 0) {

- Jos vertailun tulos on 0, eli käyttäjän syötteen 10 ensimmäistä merkkiä olivat "slm!paas.k", ohjelma suorittaa OIKEAN salasanan haaran.

- Tämä on suora vastakohta edelliselle ohjelmalle. Tässä ohjelmassa strncmp-vertailun onnistuminen tarkoittaa hyväksymistä.

Haarat:

- if-haara (vertailu == 0): Tulostaa "Yes, %s is correct!\n". Tämä on oikea vastaus.

- else-haara (vertailu != 0): Tulostaa "No, %s is not correct.\n". Tämä on väärä vastaus.

## Yhteenveto / Vastaus

Ohjelma haluaa, että salasana alkaa merkeillä "slm!paas.k".

Ainoa oikea vastaus on siis salasana:
slm!paas.k

Ohjelma vertailee vain 10 ensimmäistä merkkiä, joten salasana voi olla myös pidempi (esim. slm!paas.k123), mutta lyhyehkö slm!paas.k riittää.

Aja ohjelma komennolla: ./crackme01e slm!paas.k

Ohjelma vastaa: Yes, slm!paas.k is correct!

## f) Nora crackme02. Nimeä pääohjelman muuttujat käänteismallinnetusta binääristä ja selitä ohjelman toiminta. Ratkaise binääri.

<img width="728" height="478" alt="crackme02_OG" src="https://github.com/user-attachments/assets/dd63cade-4298-4899-8e35-a191a21f4612">

## Korjattu koodi

<img width="741" height="562" alt="crackme02_fixed_code" src="https://github.com/user-attachments/assets/60a437ff-9c8d-444f-9354-36dc207876da" />

Tässä käänsin koodin ymmärrettävämpään muotoon. Tässä on lista niistä muuttujista mitkä vaihdoin ja syy nimeämiselle.

param_1 → num_args → "Komentoriviparametrien määrä"
- Tämä kertoo, kuinka monta argumenttia ohjelmalle annettiin.
- Sama kuin argc normaalissa C-koodissa.

param_2 → args_ptr → "Osoitin argumenttitaulukkoon (argv)"
- Tämä on osoitin taulukkoon, jossa kaikki argumentit ovat.
- Sama kuin argv normaalissa C-koodissa. Esim. argv[1] on käyttäjän antama salasana.

uVar1 → exit_code → "Ohjelman paluuarvo"
- Tähän tallennetaan ohjelman lopullinen palautusarvo.
- Jos se on 0, ohjelma päättyy onnistuneesti. Jos 1 tai -1, se kertoo virheestä.

local_c → char_index → "Merkkien indeksi silmukassa"
- Tätä käytetään laskurina for-silmukassa, kun vertaillaan annettua salasanaa ja kovakoodattua merkkijonoa merkki kerrallaan.

Ylemmässä kuvassa ennen omia muutoksiani molemmissa print tulostuksissa on "undefined8".  Undefined8 Ghidrassa ei ole muuttuja, vaan tyyppimerkintä. Se tarkoittaa 8 tavun kokoista arvoa (64 bittiä), jonka tarkkaa tyyppiä Ghidra ei osaa päätellä. Siksi sitä käytetään esimerkiksi silloin, kun ohjelma käsittelee joko 64-bittisiä lukuja tai osoittimia (kuten char *). char olisi vain yhden tavun kokoinen, joten se ei käy osoittimille. Kun Ghidra näyttää esimerkiksi printf(char * __format, undefined8), se ei tiedä että toinen argumentti on merkkijono-osoitin (char *), joten mun piti tehdä override-signature ja vaihtaa se oikeaksi.

<img width="877" height="177" alt="char_override" src="https://github.com/user-attachments/assets/8d4c35fc-d6d5-41eb-a667-6eac3582bc4a" />

## Mitä ohjelma tekee?

Ohjelma tarkistaa komentoriviparametrina annetun salasanan. Se vertaa sitä kirjain kirjaimelta vääntämällä oikeaa salasanaa "password1".

## Rivi Riviltä -selitys

Rivi 8: if (num_args == 2) {
- Tarkistaa, onko annettu tasan yksi komentoriviparametri (ohjelman nimi on ensimmäinen).

Rivit 9-12: for-silmukka

- Käy läpi jokainen kirjain käyttäjän syötteessä ja vertailussa käytettävässä merkkijonossa "password1" (esim. 'p', 'a', 's', ...), kunnes törmää merkkijonon loppuun.

Rivi 13: if ("password1"[char_index] + -1 != ... ) {

- Tämän ohjelman ydin: Se vertaa käyttäjän kirjainta kohdassa char_index merkkijonon "password1" vastaavaan kirjaimeen, josta on vähennetty 1 ASCII-arvoltaan.

- Esimerkki: Ensimmäinen kirjain 'p' (ASCII 112) muuttuu arvoksi 'o' (111). Käyttäjän syötteen ensimmäisen kirjaimen täytyy siis olla 'o'.

Rivit 14-17: Virhehaara

- Jos jokin käyttäjän kirjaimista ei täsmää edellisessä vaiheessa laskettuun odotettuun kirjaimeen, ohjelma tulostaa virheviestin ja päättyy välittömästi.

Rivit 19-20: Onnistumishaara

- Jos kaikki kirjaimet täsmäävät sääntöön (käyttäjän kirjain = "password1"[sama paikka] - 1), tulostetaan onnistumisviesti.

## Yhteenveto / Oikea salasana

Ohjelma vaatii, että salasana on muodostettu vähentämällä jokaisesta merkkijonon "password1" kirjaimesta yksi ASCII-arvo.

## Lähteet
 <a href="https://terokarvinen.com/sovellusten-hakkerointi/#h4-kaantopaikka-tero" target="_blank">Tero Karvinen</a>, <a href="https://github.com/NoraCodes/crackmes/tree/master" target="_blank">Nora Codes </a>, <a href="https://stackoverflow.com/questions/67933602/what-is-undefined-function-when-i-use-ghidra-to-dissemble-a-so-file" target="_blank">Stack Overflow</a>, <a href="https://www.youtube.com/watch?v=oTD_ki86c9I" target="_blank">GHIDRA for Reverse Engineering</a>
