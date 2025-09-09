# h4 Kääntopaikka | Nathaniel Ssendagire 9.9.2025

## Ympäristö
OS: Debian GNU/Linux 12 Bookworm

Browser: Firefox 128.3.1esr (64-bit)

Hardware Model: VMWare Workstation Pro Memory: 4.0 GB

Processor: AMD Ryzen 3 7320U - 4 cores used

Disk: 35 GB

Network: NAT

## a) Asenna Ghidra.

Asensin Ghidran tällä komennolla "sudo apt-get install ghidra. Käytän kali linuxia niin se lataus toimi sillä.

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

Seuraavaksi miten sain sen sanomaan että salasana on oikein kunhan kirjoittaa mitä vain mikä ei ole se itse oikea salasana oli aika yksinkertaista, klikkaa koodissa / Decompile:mainissa sitä if functiota, niin se vie sut suoraan siihen kohtaan missä sen tarkistuksen voi muokata.  poistin "JNZ" N kirjaimen pois ja sitten se alko toimimaan. 

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

