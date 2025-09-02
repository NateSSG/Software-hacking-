# h3 No strings attached | Nathaniel Ssendagire 2.9.2025


## a) Strings. Lataa ezbin-challenges.zip Aja 'passtr'. Selvitä oikea salasana 'strings' avulla. Selvitä myös lippu. (Ensisijaisesti katsomatta sorsia, jos osaat.)

Kirjoitin komennon "Strings passtr" josta sitten näkyi salasana ja lippu. 

<img width="605" height="250" alt="command " src="https://github.com/user-attachments/assets/1131082c-58ee-4aea-8031-91aa27a5a20f" />
<img width="577" height="231" alt="password" src="https://github.com/user-attachments/assets/4c165bb0-2ddc-438e-b471-ab2456a5fe78" />

____________________________________________________________________________________________________________________________________________________________________________________________________________________
Ajoin sitten tuon passtr tiedoston, se kysyi salasanaa, kirjoitin sen salasanan minkä näin edellisessä strings listassa. Pääsin sitten sisään ja sain lipun.

<img width="467" height="66" alt="password_evidence" src="https://github.com/user-attachments/assets/ae7db977-514c-4099-b332-9f0e3c35f176" />

## b) Tee passtr.c -ohjelmasta uusi versio, jossa salasana ei näy suoraan sellaisenaan binääristä. Osoita testillä, että salasana ei näy. (Obfuskointi riittää.)

Tässä sitten käytin vähän tekoälyn apua koodin korjaamisessa, mutta mitä tää siis nyt tekee on että ohjelma kysyy käyttäjältä salasanaa ja tarkistaa sen oikellisuuden. Sen sijaan, että salasana ja lippu olisivat suoraan luettavissa ohjelman binääristä, ne on tallennettu koodissa obfuskointitekniikalla, tässä tapauksessa yksinkertaisella XOR-salauksella. Ohjelma purkaa / dekryptaa salatun salasanan ajon aikana ja vertaa  käyttäjän syöttämää salasanaa tähän salattuun versioon. Jos salasana on oikein, ohjelma purkaa ja näyttää piilotetun lipun. Tämä estää salasanojen ja lipun löytymistä helposti esim stringsillä

<img width="1147" height="846" alt="fellow AI" src="https://github.com/user-attachments/assets/40f05a46-90dc-4b11-85bb-f0268a568647" />
<img width="627" height="307" alt="fellow AI_2" src="https://github.com/user-attachments/assets/29f5fb0b-4ad9-4cc5-adac-acfaca555966" />

<img width="527" height="567" alt="evidence string" src="https://github.com/user-attachments/assets/76cf8720-6e98-4918-a152-8e571ddbb597" />

## c) Packd. Aja 'packd' paketista ezbin-challenges.zip. Mikä on salasana? Mikä on lippu?

Lähin testaamaan tätä tehtävää strings komennolla. Näin sen "salasanan", luulin että tehtävä oli sika helppo ja lähin aikamoisella itsevarmuudella kirjoittamaan salasanaa, mutta kappas vain...se ei toiminut :D. 

<img width="542" height="558" alt="piilosan" src="https://github.com/user-attachments/assets/45555f55-72cd-4b01-abae-19ef053421ee" />
<img width="560" height="110" alt="nope" src="https://github.com/user-attachments/assets/66653c82-2cd0-434e-8794-6a1eef84f100" />

Sitten seuraavaksi ajattelin että se salasana oli joku hämäys, että se oikea olikin joku muu tossa strings listassa. About 15 minuutin arvailun ja katsomisen jälkeen huomasin tämän erittäin tärkeän vihjeen!

<img width="623" height="42" alt="important tip" src="https://github.com/user-attachments/assets/da3131e6-08fc-4f69-927d-c06ae0741299" />

Lähdin saman tien etsimään netistä tietoa että mikä tämä oikein on <a href="https://linux.die.net/man/1/upx" target="_blank">Linux man page</a>, <a href="https://upx.github.io/" target="_blank">UPX selitys</a> 

Sain selville että UPX on työkalu, joka pakkaa suoritettavan ohjelman tiedoston pienempään kokoon. Tämä tarkoittaa sitä, että ohjelman koodi ja tiedot pakataan tiiviisti ja puretaan vasta ajon aikana. Tämän seurauksena ohjelman sisältö, kuten salasanat ja liput näkyivät vain puoliksi binäärissä tai "strings-" komennon tulosteessa. UPX auttaa suojaamaan ohjelmaa analysoinnilta.

Sitten ajoin tämän komennon "upx -d packd"

<img width="531" height="347" alt="upx" src="https://github.com/user-attachments/assets/253b8c52-03ba-4a42-baad-c0f087a0738b" />

Kuten huomaatte, tiedoston koko meni 5900 ---> 25263, eli nyt meillä on se tiedosto kokonaan purettu ja voidaan testata "strings" komentoa uudestaan.

<img width="1075" height="475" alt="test evidence" src="https://github.com/user-attachments/assets/6e2d8a43-6de0-459b-abb4-b6f0f84755db" />

<img width="553" height="61" alt="piilos-Ananas" src="https://github.com/user-attachments/assets/f91de935-473c-4b6f-aec1-f644116ecb13" />

Tadaa sieltä se oikea salasana napsahti ja saatiin se lippu!

