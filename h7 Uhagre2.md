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

<img width="562" height="467" alt="task 4" src="https://github.com/user-attachments/assets/ae163947-1e06-405a-9037-375277771554" />


## Ratkaisustrategia:

- Brute force -lähestymistapa: Kokeile jokaista mahdollista 256 tavun avainta

- Tekstinlaadun arviointi: Käytä englantilaisen kielen kirjaintaajuuksia

- Pistemääräjärjestelmä: Valitse korkeimman pistemäärän saanut tulos

Löydetyt tulokset:

- Avain: 0x58 (merkki 'X')

- Purettu viesti: "Cooking MC's like a pound of bacon"



