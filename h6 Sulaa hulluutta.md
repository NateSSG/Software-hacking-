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

Seuraavaksi kirjoitin file h1.jpg. Tuolla komennolla saadaan tietää mikä tiedosto tyyppi se on, mutta se jo tiedettiin koska sen pääte oli .jpg, mutta kuitenkin hyvä varmistaa koska sen nimi voi olla jpg, mutta oikeasti exe tyyppinen tiedosto.

<img width="1666" height="73" alt="file command on jpg image" src="https://github.com/user-attachments/assets/60a56b21-70a7-46be-b5d8-e30357e4f8c2" />



<img width="542" height="673" alt="exiftool the jpg file" src="https://github.com/user-attachments/assets/1460e514-37d0-4e3a-9ff0-8270a9ea561c" />

Analysoidessani h1.jpg-tiedostoa käytin ExifToolia saadakseni kuvan metatietoja. Työkalu paljasti esimerkiksi tiedoston nimen, koon (838 kB), muokkaus- ja käyttöpäivämäärät, käyttöoikeudet, kuvan tyypin (JPEG) ja sen resoluution (1024x1024 pikseliä). Lisäksi löytyi tietoa värijärjestelmästä (YCbCr 4:2:0, sRGB) ja pakkausprosessista (Baseline DCT, Huffman-koodaus). Nämä tiedot antoivat yleiskuvan tiedoston rakenteesta ja ominaisuuksista, ja osoittivat, että tiedostossa ei näyttänyt olevan ylimääräisiä piilotettuja osioita suoraan metatietojen perusteella.

<img width="571" height="455" alt="xxd scan of image file" src="https://github.com/user-attachments/assets/b691edd1-0a76-42a9-8f25-481cb74377bd" />
