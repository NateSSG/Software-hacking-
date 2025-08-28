# Nathaniel Ssendagire | Hack' Fix 28.8.2025

## Ympäristö

OS: Debian GNU/Linux 12 Bookworm

Browser: Firefox 128.3.1esr (64-bit)

Hardware Model: VMWare Workstation Pro
Memory: 4.0 GiB

Processor: AMD Ryzen  3 7320U - 4 cores used

Disk: 35 GB

Network: NAT

## x) Lue/katso ja tiivistä. (Tässä x-alakohdassa ei tarvitse tehdä testejä tietokoneella, vain lukeminen ja tiivistelmä riittää. Tiivistämiseen riittää muutama ranskalainen viiva.)

Broken Access Control ja privilege escalation liittyvät tilanteisiin, joissa käyttäjä onnistuu ohittamaan käyttöoikeusrajoituksia ja saa pääsyn resursseihin tai toimintoihin, jotka eivät kuulu hänen oikeuksiinsa. Tällaiset ongelmat voivat johtaa vakaviin tietoturvaloukkauksiin.

Työkalu nimeltä ffuf soveltuu erinomaisesti verkkopalvelujen tutkimiseen. Sen avulla voidaan automaattisesti kartoittaa esimerkiksi piilotettuja hakemistoja ja tiedostoja, ja edistyneemmillä asetuksilla testata palvelimen käyttäytymistä eri HTTP-headerien avulla.

Tietoturvaraportointiin kuuluu tarkkoja vaatimuksia ja eettisiä sääntöjä. Kaiken dokumentoinnin on perustuttava todellisiin havaintoihin – tietojen keksiminen tai liioittelu heikentää raportin luotettavuutta ja voi johtaa vakaviin seurauksiin.

SQL-injektio on hyökkäystapa, jossa käyttäjä syöttää haitallista koodia esimerkiksi lomakekenttään. Jos syöte ei ole asianmukaisesti suojattu, hyökkääjä voi vaikuttaa taustalla olevaan tietokantaan, esimerkiksi lukea, muokata tai tuhota tietoja.

______________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________

Ensimmäisessä tehtävässä muutin input type kohdan tyhjäksi, jotta sinne voi laittaa ihan mitä vaan, eikä pelkästään numeroita. 

<img width="1025" height="407" alt="Input type" src="https://github.com/user-attachments/assets/c7ad8a6a-b5bc-44db-9535-75a78fd20daa" />

Testasin sen jälkeen ' OR 1=1-- teksti kenttään minkä opin edellisellä tunnilla. Vastaukseksi tuli "foo". Olin oikeilla jäljillä, jes! sitten lähdin lukemaan portswiggeristä ja youtubesta vähän tietoa SQL injectiosta. 



Lähteet: <a href="https://portswigger.net/web-security/sql-injection/union-attacks" target="_blank">Portswigger</a>


<img width="738" height="332" alt="Foo_password" src="https://github.com/user-attachments/assets/c9fd9c41-7443-4948-9e9f-dafbd2f67239" />

______________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________

Samalla kun luin huomasin vähän yhtäläisyyksiä kuvan kanssa, löysin lopulta vastauksen mikä on "UNION SELECT password FROM pins--

<img width="750" height="66" alt="image" src="https://github.com/user-attachments/assets/2aece036-ff6c-47a9-b1c7-9b044989422c" />
<img width="982" height="297" alt="SUPERADMIN_password" src="https://github.com/user-attachments/assets/f6698e4d-417d-45c6-a704-e2dc91f13564" />

## b) Korjaa 010-staff-only haavoittuvuus

<img width="627" height="486" alt="CodeFix 1" src="https://github.com/user-attachments/assets/99cc4117-41cd-4822-b16b-3d4fd096c665" />

Seuraavaksi keskityttiin koodin korjaamiseen, jotta sama SQL-injektiohaavoittuvuus ei voisi enää toistua. Tarkemmin tarkasteltuna havaitsin virheen, jossa käyttäjän syöte liitettiin suoraan osaksi SQL-kyselyä ilman asianmukaista käsittelyä. Tämä avasi mahdollisuuden haitallisen koodin suorittamiseen.

Ratkaisuna tähän luotiin erillinen muuttuja nimeltä pin2, johon käyttäjän syöte tallennetaan. Tämän jälkeen arvo siirretään turvallisesti execute()-funktiolle parametrisoituna syötteenä, mikä estää suoran SQL-koodin injektoinnin.

<img width="755" height="563" alt="Code_evidence" src="https://github.com/user-attachments/assets/fcfba397-9a6e-477f-b14a-86a774722c20" />

 ## Ratkaise dirfuzt-1 artikkelista Karvinen 2023: Find Hidden Web Directories - Fuzz URLs with ffuf. 

 Tämä oli aika yksinkertainen. Seurasin ffuf asennus ohjeita <a href="https://terokarvinen.com/2023/fuzz-urls-find-hidden-directories/" target="_blank">Terokarvinen</a>. Asennuksen jälkeen käynnistin ffufin. Huomasin että sieltä tuli PALJON requesteja. Niissä oli kyllä aika paljon samaa ja se oli että pituus / koko oli 154, joten tulin sellaiseen päätökseen, että suodatan kaikki joiden pituus on 154 pois ja sit BOOM sieltä napsahti oikeat sivu jee :D.
______________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________

<img width="1038" height="951" alt="FuzzEvidencee" src="https://github.com/user-attachments/assets/1475306c-fad0-424c-9eb8-458ac15efdd6" />
<img width="553" height="51" alt="Screenshot 2025-08-28 231056" src="https://github.com/user-attachments/assets/974c85e4-4bf2-4be8-beed-be52338ae8b6" />
<img width="906" height="472" alt="Fuzz2 1" src="https://github.com/user-attachments/assets/f50c39fb-52ef-45dd-90a8-d79505bd8c65" />
<img width="831" height="412" alt="Fuzz2 0" src="https://github.com/user-attachments/assets/1bca1c86-a39e-4718-bcef-994002323a8f" />

 ## Murtaudu 020-your-eyes-only
 Tein saman jutun kuin siinä ffuf tehtävässä. Suodatin 132 ja löysin sivun nimeltä admin-console. Pistin testiin ja kappas. Pääsin sisään 😁
 Eli mitä tossa nyt tapahtui oli että piti olla sisäänkirjautuneena ja sitten sieltä hakukoneesta muuttaa se sivu ja tadaa you're in.

 Lähteet mitä käytin: <a href="https://terokarvinen.com/hack-n-fix/" target="_blank">Hack'n Fix </a>, <a href="https://terokarvinen.com/2023/fuzz-urls-find-hidden-directories/" target="_blank">Terokarvinen</a>
 
<img width="857" height="817" alt="Screenshot 2025-08-28 234750" src="https://github.com/user-attachments/assets/a9f9a1be-e3d3-4d4a-8fed-f24533902d97" />



<img width="1173" height="356" alt="admin-console-page" src="https://github.com/user-attachments/assets/6c871b43-cd81-43d0-9f86-40d1313881df" />





