#h5 Se elää! | Nathaniel Ssendagire 16.9.2025
## Ympäristö

OS: Debian GNU/Linux 12 Bookworm

Browser: Firefox 128.3.1esr (64-bit)

Hardware Model: VMWare Workstation Pro Memory: 4.0 GB

Processor: AMD Ryzen 3 7320U - 4 cores used

Disk: 35 GB

Network: NAT
## Lab 0
Ensiksi suoritin koodin. Huomasin että koodissa lasku numero on 0 element 5 kohdalla. Tarkoittaa sitä että koodi epäonnistuu, koska silmukka menee yhden askeleen liian pitkälle ja yrittää lukea taulukon ulkopuolelta. Tämä johtaa virheelliseen tulostukseen tai ohjelman kaatumiseen.

<img width="595" height="393" alt="lab 0 ss" src="https://github.com/user-attachments/assets/5cc18382-f9e0-4f01-acbe-7719114622aa" />

<img width="671" height="358" alt="lab00 buggy_code" src="https://github.com/user-attachments/assets/603a9cb4-6256-4063-bd56-19a85436a9b9" />

## Korjattu koodi

<img width="442" height="328" alt="lab00 fixed_code" src="https://github.com/user-attachments/assets/ce83bea8-dba9-4309-9957-42c6b535611a" />


#include <stdio.h>
- Tuo mukaan standardikirjaston, joka sisältää printf-funktion. Sitä käytetään tulostamiseen.

void fixed_function(int *arr, int size) {
- Määrittelee funktion nimeltä fixed_function, joka ottaa vastaan kokonaislukutaulukon osoittimen (arr) ja taulukon koon (size).
- 
for (int i = 0; i < size; i++) {
- Aloittaa silmukan, joka käy läpi taulukon alkiot indeksistä 0 aina size - 1:een. Tämä estää virheellisen pääsyn taulukon ulkopuolelle.

printf("Element %d: %d\n", i, arr[i]);
-Tulostaa jokaisen taulukon alkion muodossa: "Elementti [indeksi]: [arvo]".

}
-Päättää silmukan ja funktion.

int main() {
- Ohjelman aloituspiste.
  
int numbers[] = {1, 2, 3, 4, 5};
- Luo taulukon nimeltä numbers, jossa on viisi kokonaislukua.
  
fixed_function(numbers, 5);
- Kutsuu fixed_function-funktiota ja antaa sille taulukon sekä sen koon (5).
  
return 0;
-Päättää ohjelman ja palauttaa arvon 0, mikä tarkoittaa onnistunutta suoritusta.
