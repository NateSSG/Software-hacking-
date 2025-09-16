#h5 Se elää! | Nathaniel Ssendagire 16.9.2025
## Ympäristö

OS: Debian GNU/Linux 12 Bookworm

Browser: Firefox 128.3.1esr (64-bit)

Hardware Model: VMWare Workstation Pro Memory: 4.0 GB

Processor: AMD Ryzen 3 7320U - 4 cores used

Disk: 35 GB

Network: NAT
## Lab 0
Ensiksi suoritin koodin. Huomasin että koodissa lasku numero on 0 element 5 kohdalla. Pistin DBG:n tulille ja kirjoitin "start". Debuggeri pysähtyi ja ilmoitti ongelman mikä oli rivillä 10. Tarkoittaa sitä että koodi epäonnistuu, koska silmukka menee yhden askeleen liian pitkälle ja yrittää lukea taulukon ulkopuolelta. Tämä johtaa virheelliseen tulostukseen tai ohjelman kaatumiseen.

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

## Lab 1
Seuraavaksi tein saman jutun lab 1. Ajoin tiedoston ja sieltä tuli sitten tämmöinen viesti. Debugger on todella hyödyllinen tämmöisissä tilanteissa, jossa pitää selvittää mikä koodissa on vikana, kun se tulostaa jotain tuommoista.
<img width="467" height="100" alt="lab01 error_when_u_run_the_file" src="https://github.com/user-attachments/assets/286710a3-123c-46d1-8ae4-76b9453f486c" />

Ajettuani debuggerin, niin se näytti heti että mikä siinä koodissa oli oikein vikana:
<img width="588" height="363" alt="lab01 ss bug" src="https://github.com/user-attachments/assets/3b980650-4a90-44d5-8f7c-c9cece8e76d1" />

<img width="581" height="363" alt="lab01 ss_code" src="https://github.com/user-attachments/assets/10c90f40-b07a-4805-a279-919c52f9779c" />


Ongelma näyttää olevan rivillä 13. Tämä meinaa sitä, että koodi epäonnistuu, koska funktio yrittää käsitellä viestiä, joka on NULL, eli tyhjä osoitin. Ilman tarkistusta se johtaa virheeseen, koska ohjelma yrittää lukea muistista kohtaa, jota ei ole olemassa.

## Korjattu koodi Lab 1 

Seuraavaksi lähdetään korjaamaan koodia.

<img width="502" height="535" alt="lab01 fixed code" src="https://github.com/user-attachments/assets/6168ed75-933f-4711-96f7-9ef8cc10572d" />

Päivitetty koodi toimii oikein, koska se tarkistaa ensin, onko viesti NULL ennen kuin yrittää käsitellä sitä. Jos viesti on tyhjä, se tulostaa "[null message]" eikä yritä lukea muistista virheellistä osoitetta. Vanha koodi taas kaatui, koska se ei tehnyt tarkistusta ja yritti käyttää NULL-osoitinta, mikä johti virheeseen.

## Mitä koodissa tapahtuu rivi riviltä

#include <stdio.h>
- Tuo mukaan standardikirjaston, joka sisältää printf- ja putchar-funktiot tulostamista varten.
  
void print_scrambled(char *msg) {
-Määrittelee funktion, joka ottaa parametriksi merkkijonon osoittimen (msg). Tämä voi olla joko oikea viesti tai NULL.

if (msg == NULL) {
-Tarkistaa, onko viesti tyhjä (eli NULL). Jos on, ohjelma ei yritä käsitellä sitä.

printf("[null message]\n"); return;
-Tulostaa varoituksen "[null message]" ja lopettaa funktion ennen kuin yritetään käyttää virheellistä muistiosoitetta.

while (*msg) { putchar(*msg); msg++; }
- Jos viesti ei ole NULL, tämä silmukka käy läpi merkkijonon merkki kerrallaan ja tulostaa sen. putchar tulostaa yhden merkin, ja msg++ siirtyy seuraavaan merkkiin.
- 
printf("\n");
- Tulostaa rivinvaihdon lopuksi, jotta tulostus näyttää siistiltä.

int main() {
- Ohjelman aloituspiste.
  
char *bad_message = NULL;
- Määrittelee tyhjän viestin, joka ei osoita mihinkään muistipaikkaan.
  
char *good_message = "Hello, world.";
- Määrittelee oikean viestin, joka sisältää tekstin "Hello, world."
  
print_scrambled(good_message);
- Kutsuu funktion oikealla viestillä, joka tulostetaan merkki kerrallaan.
  
print_scrambled(bad_message);
- Kutsuu funktion tyhjällä viestillä. Koska msg == NULL, tulostetaan "[null message]" eikä ohjelma kaadu.

return 0;
-Ohjelma päättyy onnistuneesti.

## Lab 2
Seuraavaksi piti ryöstää lippu:

<img width="601" height="757" alt="lab02 disassembler" src="https://github.com/user-attachments/assets/81350fd3-b857-4899-ba63-0976bc5971cb" />


<img width="1672" height="675" alt="lab02 flag password thing" src="https://github.com/user-attachments/assets/4ec5cf00-b08c-408d-b575-8a435d58531a" />

## Mitä tein passtr2o-binäärin kanssa

purin passtr2o-ohjelma GDB:llä ja tutkin sen konekielistä rakennetta, vaikka siinä ei ollut debug-symbolisia. Disassemblaamalla main-funktion löysin kohdan, jossa ohjelma pyytää käyttäjältä salasanaa scanf-kutsun avulla. Heti sen jälkeen kutsuin funktiota nimeltä mAsdf3a, joka tarkisti, oliko syöte oikea.

## Miten löysin oikean kohdan pysäyttää ohjelman

Disassemblausta tutkimalla näin, että ohjelma käytti rekisteriä %eax tarkistukseen. Jos mAsdf3a palautti arvon 1, ohjelma siirtyi onnistumispolulle. Tämä tapahtui kohdassa:

0x0000000000001105: dec %eax
0x0000000000001107: jne ...

Tämä oli ratkaiseva haarautumiskohta. Asetin keskeytyksen juuri ennen tätä, jotta voin ohjata ohjelman kulkua.

## Miten huijasin ohjelmaa

Kun ohjelma pysähtyi, käytin komentoa: set $eax=1

Tämä sai ohjelman luulemaan, että salasana oli oikein.

Sen jälkeen tein: 
ni
ni
ni
Kolme kertaa ni (next instruction) askelsi ohjelman eteenpäin:

- lea 0xa(%rsp), %rdi

- dec %eax

- jne ... (joka ei enää hyppää, koska %eax == 0)

Näin päädyttiin onnistumispolulle, joka alkaa kohdasta main+137.

## Miten sain lipun esiin

Kun olin onnistumispolulla, tein: 

si         ; step into EaseEAs
finish     ; palataan takaisin pääohjelmaan
x/s $rbx   ; näytetään lippu muistista
continue   ; annetaan ohjelman tulostaa lippu

Lippu oli tallennettu muistipaikkaan rbx, joka osoitti puskuria rsp+0x30. Tämä oli se paikka, johon EaseEAs kirjoitti lopullisen lipun.

