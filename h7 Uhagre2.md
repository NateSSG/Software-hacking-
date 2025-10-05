# h7 Uharge | Nathaniel Ssendagire 5.10.2025

Ympäristö

OS: Windows 11 Home

Browser: Firefox 128.3.1esr (64-bit)

GPU : AMD Radeon RX 9060 XT : 16.0 GB

MOBO : ASUS Prime B450-Plus 

RAM: 16 GB

Processor: AMD Ryzen 7 5700X 4 cores used

Disk: 90 GB

Network: NAT

## Convert hex to base64

Ongelmananto: Muunna heksadesimaalimerkkijono base64-muotoon noudattaen periaatetta "aina työskentele raakabyteillä".

<img width="600" height="161" alt="task 1" src="https://github.com/user-attachments/assets/b8c99c6b-ae88-4b4f-85d0-588696959cd0" />

## Miten se toimii:     

- Buffer.from(hexString, 'hex') muuntaa heksamerkit raakatavuisiksi

- .toString('base64') muuntaa tavut base64-muotoon

<img width="687" height="118" alt="terminal 1" src="https://github.com/user-attachments/assets/044ee00b-3820-409e-9bea-309db32e1be3" />

## Fixed XOR

Ongelmananto: Luo funktio, joka suorittaa XOR-operaation kahdelle samanpituiselle heksamerkkijonolle.

<img width="966" height="348" alt="task 2" src="https://github.com/user-attachments/assets/a93400f9-2fef-4d6f-8c05-928e5bf5051a" />


## Miten se toimii: 

- Muuntaa molemmat heksajonot tavutaulukoiksi

- Suorittaa XOR-operaation jokaiselle tavuparille

- Palauttaa tuloksen heksamuodossa

<img width="462" height="127" alt="terminal 2" src="https://github.com/user-attachments/assets/0a2d494d-8496-4e90-95e8-0bf9bfc18fc2" />

## Haaste 3 & 4: XOR-salauksen murtaminen

Ongelmananto: Etsi yhden merkin avain, jolla viesti on XOR-salattu, ja pura salaus.

<img width="707" height="592" alt="task 3" src="https://github.com/user-attachments/assets/4898ece1-40ad-4f92-b12f-cdd48ce11a16" />

## Koodi selitetty rivi-riviltä: 
- Muuntaa heksadesimaalimerkkijonon tavutaulukoksi (Buffer) Esim: "1b3737..." → [27, 55, 55, ...]
- Alustetaan muuttujat parhaan tuloksen seuraamiseen
- Kokeilee jokaista mahdollista 1-tavun avainta (0-255)
- Luo tulostustavutaulukon samalla koolla kuin salattu data
- Suorittaa XOR-operaation jokaiselle tavulle salatussa datassa
- XOR: salattu_tavu ⊕ avain = purettu_tavu
- Muuntaa puretut tavut tekstiksi
- Arvioi tekstin laatua englantilaisen tekstin taajuuksilla
- Jos tämä tulos on parempi kuin edellinen paras, tallennetaan se
- Palauttaa parhaan löydetyn tuloksen

## Haaste 4 koodi selitys

- Rivi 1: Funktio saa parametrina taulukon heksamerkkijonoja, joista yksi on salattu yhden merkin XOR:lla.

Rivi 3: Alustetaan muuttuja, joka pitää kirjaa parhaasta löydetystä tuloksesta:
- text: Parhaaksi arvioitu purettu teksti
- score: Parhaan tuloksen pistemäärä
- line: Rivinumero, jolla paras tulos löytyi

Rivi 6: Käydään läpi jokainen salattu merkkijono taulukossa:
- hexString: Yksi salattu heksamerkkijono
- lineNum: Nykyisen merkkijonon indeksi taulukossa (0, 1, 2, ...)

Rivi 8: Käytetään edellisen haasteen funktiota purkamaan tämä merkkijono:
- singleByteXORCipher kokeilee kaikkia 256 avainta
- Se palauttaa objektin: { key, text, score }
- result sisältää parhaan löydetyn tuloksen tälle merkkijonolle

Rivi 11: Verrataan tuloksen laatua parhaaseen tähän mennessä löydettyyn:
- Tarkistetaan onko tämän merkkijonon paras tulos parempi kuin globaali paras
- Vertailu tehdään pistemäärän perusteella

Rivit 12-18: Tallennetaan uusi paras tulos:
- text: Kopioidaan purettu teksti
- score: Kopioidaan pistemäärä
- line: lineNum + 1: Lasketaan oikea rivinumero (käyttäjälle ystävällisempi)
- key: Tallennetaan käytetty avain

- Rivi 19: forEach-silmukan loppu - toistetaan jokaiselle merkkijonolle taulukossa.

- Rivi 22: Palautetaan paras löydetty tulos koko taulukosta.

## Käytännön esimerkki:

Oletetaan että meillä on 3 salattua merkkijonoa:
const hexStrings = [
    "0e3647e8592d35514a081243582536ed3de67340",  // Rivi 1 - satunnaista dataa
    "1b37373331363f78151b7f2b783431333d783978",  // Rivi 2 - XOR-salattu teksti
    "334b041de124f73c18011a50e608097ac308ecee"   // Rivi 3 - satunnaista dataa
];

## Mitä funktio tekee vaiheittain:

Rivi 1: singleByteXORCipher palauttaa matalan pistemäärän (esim. 15.2)
- Ei parempi kuin alkuperäinen 0 → ei tallenneta
Rivi 2: singleByteXORCipher löytää tekstin "Cooking MC's like..." pistemäärällä 174.6
- Parempi kuin edellinen paras (0) → TALLENNETAAN
- bestOverall nyt: { text: "Cooking...", score: 174.6, line: 2, key: 88 }
Rivi 3: singleByteXORCipher palauttaa matalan pistemäärän (esim. 22.1)
- Ei parempi kuin 174.6 → ei tallenneta
Lopputulos: Funktio palauttaa objektin riville 2

## Miks tää toimii?

- Useimmat merkkijonot ovat satunnaista dataa → matalat pistemäärät
- Yksi merkkijono on oikeasti salattu teksti → korkea pistemäärä
- Korkein pistemäärä kertoo mikä merkkijono oli salattu

## Miten tää liittyy haasteeseen 4?
Haasteessa 4 annetaan satoja salattuja merkkijonoja, joista vain yksi on oikeasti XOR-salattu englanninkielinen teksti. Tämä funktio löytää sen automaattisesti!

Yksinkertaisesti sanottuna: Tämä funktio on "etsi neula heinäsuovasta" -työkalu salatuille viesteille!






<img width="562" height="467" alt="task 4" src="https://github.com/user-attachments/assets/ae163947-1e06-405a-9037-375277771554" />

## Apufunktio 

<img width="808" height="368" alt="apufunktio" src="https://github.com/user-attachments/assets/32754e01-d7a6-415e-af75-fd3532db0b06" />

## Koodi rivi-riviltä selitys: 

- Rivi 1: Funktio saa parametrina tekstin, jonka laatua halutaan arvioida.
Rivit 2-6: Luodaan taulukko, joka kertoo kunkin merkin esiintymistiheyden englannin kielisessä tekstissä prosentteina:
- ' ': 15 → Välilyönti esiintyy noin 15% ajasta

- 'e': 12.7 → Kirjain 'e' esiintyy noin 12.7% ajasta

- 't': 9.1 → Kirjain 't' esiintyy noin 9.1% ajasta

- ...ja niin edelleen

- Rivi 8: Alustetaan pistemäärä nollaksi.

Rivi 10: Käydään läpi jokainen merkki syötetekstissä:
  - text.toLowerCase() muuntaa kaikki kirjaimet pieniksi, jotta 'E' ja 'e' käsitellään samana

  - char sisältää yhden merkin kerrallaan

Rivi 12: Tämä on funktion ydinrivi:
- freq[char] hakee merkin taajuusarvon taulukosta
- || 0 tarkoittaa: "jos taulukossa ei ole arvoa tälle merkille, käytä nollaa"
- score += lisää löydetyn arvon kokonaispistemäärään

- Rivi 14: Palautetaan laskettu kokonaispistemäärä.

## Miks tää toimii salauksen murtamisessa? 

- Oikea salaus → Tekstiksi tulee "Cooking MC's like..." → Korkea pistemäärä

- Väärä salaus → Tekstiksi tulee "×°¶§¤@" → Matala pistemäärä

- Korkein pistemäärä = Todennäköisimmin oikea salaus

## Miten tää auttaa haasteessa 3?

Kun kokeilemme 256 eri avainta:

- 255 väärää avainta tuottavat satunnaista "roskaa" → matala pistemäärä
- 1 oikea avain tuottaa englanninkielistä tekstiä → korkea pistemäärä
- Valitsemme sen avaimen, joka antai korkeimman pistemäärän

Yksinkertaisesti sanottuna: Tämä funktio toimii "englannin kielen tunnistimena".





## Ratkaisustrategia:

- Brute force -lähestymistapa: Kokeile jokaista mahdollista 256 tavun avainta

- Tekstinlaadun arviointi: Käytä englantilaisen kielen kirjaintaajuuksia

- Pistemääräjärjestelmä: Valitse korkeimman pistemäärän saanut tulos

Löydetyt tulokset:

- Avain: 0x58 (merkki 'X')

- Purettu viesti: "Cooking MC's like a pound of bacon"

<img width="447" height="113" alt="terminal 3" src="https://github.com/user-attachments/assets/6ddf2f13-8be3-4f88-be43-37612e326812" />

<img width="487" height="106" alt="terminal 4" src="https://github.com/user-attachments/assets/278bbc77-834c-40ab-b12c-ddc8a579bbf0" />




