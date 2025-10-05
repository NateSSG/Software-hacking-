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

<img width="562" height="467" alt="task 4" src="https://github.com/user-attachments/assets/ae163947-1e06-405a-9037-375277771554" />

## Apufunktio 

<img width="808" height="368" alt="apufunktio" src="https://github.com/user-attachments/assets/32754e01-d7a6-415e-af75-fd3532db0b06" />

## Rivi-riviltä selitys: 

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




