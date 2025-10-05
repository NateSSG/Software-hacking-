# h6 Sulaa hulluutta | Nathaniel Ssendagire 23.9.2025

## Ympäristö

OS: Debian GNU/Linux 12 Bookworm

Browser: Firefox 128.3.1esr (64-bit)

Hardware Model: VMWare Workstation Pro Memory: 4.0 GB

Processor: AMD Ryzen 3 7320U - 4 cores used

Disk: 35 GB

Network: NAT

## Lab 0 

Analysoidessani h1.jpg-tiedostoa käytin perusanalyysityökaluja, kuten strings-komentoa ja hekseditoria, saadakseni esiin luettavaa tekstiä ja metatietoja, jotka olivat upotettuina kuvaan. Suorittamalla strings h1.jpg, mutta sieltä ei tullut oikeastaan mitään esiin.

<img width="560" height="470" alt="jpg file strings" src="https://github.com/user-attachments/assets/acfbdb8f-b1c8-43b9-a590-b27ea14ae042" />

_________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________

Seuraavaksi kirjoitin file h1.jpg. Tuolla komennolla saadaan tietää mikä tiedosto tyyppi se on, mutta se jo tiedettiin koska sen pääte oli .jpg, mutta kuitenkin hyvä varmistaa koska sen nimi voi olla jpg, mutta oikeasti exe tyyppinen tiedosto.

<img width="1666" height="73" alt="file command on jpg image" src="https://github.com/user-attachments/assets/60a56b21-70a7-46be-b5d8-e30357e4f8c2" />

_________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________


Analysoidessani h1.jpg-tiedostoa käytin ExifToolia saadakseni kuvan metatietoja. Työkalu paljasti esimerkiksi tiedoston nimen, koon (838 kB), muokkaus- ja käyttöpäivämäärät, käyttöoikeudet, kuvan tyypin (JPEG) ja sen resoluution (1024x1024 pikseliä). Lisäksi löytyi tietoa värijärjestelmästä (YCbCr 4:2:0, sRGB) ja pakkausprosessista (Baseline DCT, Huffman-koodaus). Nämä tiedot antoivat yleiskuvan tiedoston rakenteesta ja ominaisuuksista, ja osoittivat, että tiedostossa ei näyttänyt olevan ylimääräisiä piilotettuja osioita suoraan metatietojen perusteella.


<img width="542" height="673" alt="exiftool the jpg file" src="https://github.com/user-attachments/assets/1460e514-37d0-4e3a-9ff0-8270a9ea561c" />

_________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________

<img width="571" height="455" alt="xxd scan of image file" src="https://github.com/user-attachments/assets/b691edd1-0a76-42a9-8f25-481cb74377bd" />

Käytin tässä xxd:tä, mutta tästä ei oikein saa mitään selvää.

_________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________


## Lab 1

<img width="1338" height="491" alt="binwalk jpg image" src="https://github.com/user-attachments/assets/3b7a11f5-7d7c-4b58-94ea-66405ef1d4bc" />

## 🔎 Mitä tietoja löytyi?

binwalk-analyysin perusteella h1.jpg sisältää normaalin JPEG-kuvatiedoston lisäksi upotettuja ZIP-arkistoja, joista paljastui useita DOCX-tiedostolle tyypillisiä osia:

- [Content_Types].xml

- word/document.xml (dokumentin sisältö)

- word/styles.xml, word/theme/theme1.xml (muotoilut ja tyylit)

- docProps/core.xml, docProps/app.xml (dokumentin metatiedot)

Tämä tarkoittaa, että kuvaan on piilotettu Word-dokumentti (steganografia tai liitetty data).


## 🛠 Mitä työkalua käyttäisit tiedostojen erottamiseen?

- binwalk -e h1.jpg → purkaa automaattisesti löydetyt arkistot ja tallentaa ne hakemistoon.

- unzip → koska sisältö on ZIP-muodossa, voit purkaa ne manuaalisesti:
    unzip extracted.zip -d output_folder
  
- 7z (p7zip) → toimii vaihtoehtoisena purkutyökaluna.

Näin saat talteen Word-dokumentin sisällön ja voit avata sen esimerkiksi LibreOffice:lla tai analysoida suoraan XML-tiedostoja.

## Eli mitä tästä nyt selvisi? 

Binwalkin avulla selvisi, että h1.jpg sisältää piilotettuna ZIP-arkiston, jossa on Microsoft Word -dokumentin rakenteeseen kuuluvia tiedostoja. Näiden erottamiseen ja tarkempaan tutkimiseen voisi käyttää esimerkiksi binwalk -e -komentoa tai unzip-työkalua. Näin voidaan palauttaa ja analysoida piilotetun dokumentin sisältö.


<img width="1266" height="462" alt="extracted binwalk jpg" src="https://github.com/user-attachments/assets/055675ec-8c4f-4537-9ad2-4a30fa644929" />

<img width="672" height="223" alt="495zip is a word document" src="https://github.com/user-attachments/assets/0e5df7b5-1bbd-4515-851d-028374685e0c" />

## Lab 2

## 🔗 Valittu APK

Lab 2:ssa valitsin analysoitavaksi MusicRecognizer-sovelluksen GitHubista:
👉 https://github.com/aleksey-saenko/MusicRecognizer

APK ladattiin ja analysoitiin kahdella työkalulla: JADX ja Bytecode-Viewer.


## 🔍 Käytetyt työkalut

JADX:

- Purkaa APK:n sisältämät classes.dex-tiedostot selkokieliseen Java-lähdekoodiin.

- Näyttää projektin rakenteen selkeästi puumaisessa näkymässä (paketit, luokat, resurssit).

- Hyvä koodin lukemiseen ja ohjelman logiikan hahmottamiseen.

Bytecode-Viewer:

<img width="1707" height="890" alt="Bytecode Viewer UI review" src="https://github.com/user-attachments/assets/7173a6d6-8158-4c8f-846d-f43f86639a45" />


- Näyttää APK:n luokat suoraan Java bytecode -muodossa sekä vaihtoehtoisesti dekompiloituna.

- Sisältää useita dekompilaattoreita (esim. Fernflower, CFR), mikä mahdollistaa koodin vertailun.

- Parempi, jos halutaan nähdä tarkasti mitä virtuaalikone ajaa (bytecode-taso).

Samankaltaisuudet: Molemmat purkavat APK:n ja antavat mahdollisuuden tarkastella koodia, resursseja ja sovelluksen rakennetta.
Erot: JADX keskittyy selkeään ja luettavaan Java-koodiin, kun taas Bytecode-Viewer mahdollistaa matalamman tason bytecode-analyysin ja dekompilaattorien vertailun.

## 📑 Mitä tietoa APK:sta löytyi

Analysoimalla APK:n sisältöä löysin seuraavia asioita:

- Data-mallit: Sovelluksen käyttämät tiedonrakenteet (esim. äänidatan käsittelyyn ja tallennukseen liittyvät mallit).

- Käyttöliittymän tiedot: Aktiviteetit ja layout-resurssit, jotka kuvaavat sovelluksen näkymät.

- Verkkokäyttö: Luokat ja metodit, joissa hyödynnetään verkkoa (API-yhteydet ja tiedonsiirto).

- Musiikin tunnistuslogiikka: Pääkoodi, joka toteuttaa äänentallennuksen ja sen tunnistuksen.

- Resurssikansio: Sisälsi mm. näyteäänitiedostoja, joita sovellus käyttää testaukseen tai esittelyyn.

- Toiminnallisuudet: Koodista löytyi viittauksia mm. tunnistuksen peruuttamiseen ja poistamiseen.

- Varmuuskopiot ja tietokanta: Sovellukseen liittyi myös tiedostoja ja luokkia, jotka hallitsevat käyttäjän tietoja ja varmuuskopiointia.

Vaikka suurin osa oli koodia, luokkien ja tiedostonimien perusteella oli mahdollista muodostaa kokonaiskuva siitä, mistä eri osista sovellus koostuu ja mitä toiminnallisuuksia siihen sisältyy.

## Yhteenveto 

JADX tarjosi paremmin luettavaa lähdekoodia, kun taas Bytecode-Viewer täydensi analyysia tarkemmalla näkymällä bytecodeen. Näiden avulla saatiin selville sovelluksen rakenne, käyttöliittymä, verkon käyttö, tunnistustoiminnallisuudet ja siihen liittyvät resurssit.

## Kuvat
<img width="312" height="282" alt="application database" src="https://github.com/user-attachments/assets/8798b8cb-e0c0-4ce9-87a9-75bc3bac71d0" />

<img width="1117" height="707" alt="backup files" src="https://github.com/user-attachments/assets/237873e1-c36d-4309-9e9e-f5fe9cb85537" />

<img width="1195" height="596" alt="music recorder_recognition" src="https://github.com/user-attachments/assets/b74efbaa-25f7-4152-95db-4fabbc44a81b" />

<img width="1196" height="632" alt="network usage" src="https://github.com/user-attachments/assets/35f4f246-a1b0-4f71-9f2b-fb951e25f0da" />

<img width="1715" height="901" alt="the heart of the android app aka the code" src="https://github.com/user-attachments/assets/3e1baf13-ef45-416e-aedc-6708079f789f" />

<img width="400" height="107" alt="resources folder test sample sound" src="https://github.com/user-attachments/assets/ce6dd0a9-11b5-45a9-b7bd-5fe52a7d20e1" />

<img width="371" height="243" alt="recognition cancelling and disabeling" src="https://github.com/user-attachments/assets/e7ffab9e-1175-4ad8-9b29-c3a94af582bd" />

<img width="367" height="531" alt="info about user interface" src="https://github.com/user-attachments/assets/e85ff95e-eb0d-49d5-b584-917bedd61c53" />

## Lähteet

<a href="https://github.com/aleksey-saenko/MusicRecognizer">MusicRecognizer</a>, <a href="https://hhmoodle.haaga-helia.fi/mod/folder/view.php?id=3329191">Larin tehtävä</a>, 
<a href="https://github.com/offa/android-foss">android-foss</a>, <a href="https://github.com/skylot/jadx">jadx</a>, <a href="https://github.com/Konloch/bytecode-viewer/">bytecode-viewer</a>, <a href="https://cryptopals.com/sets/1">Cryptopals</a>

