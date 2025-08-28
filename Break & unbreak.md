# Nathaniel Ssendagire | Hack' Fix 28.8.2025

## Ympäristö

OS: Debian GNU/Linux 12 Bookworm

Browser: Firefox 128.3.1esr (64-bit)

Hardware Model: VMWare Workstation Pro
Memory: 4.0 GiB

Processor: AMD Ryzen  3 7320U - 4 cores used

Disk: 35 GB

Network: NAT

x) Lue/katso ja tiivistä. (Tässä x-alakohdassa ei tarvitse tehdä testejä tietokoneella, vain lukeminen ja tiivistelmä riittää. Tiivistämiseen riittää muutama ranskalainen viiva.)

Broken Access Control ja privilege escalation liittyvät tilanteisiin, joissa käyttäjä onnistuu ohittamaan käyttöoikeusrajoituksia ja saa pääsyn resursseihin tai toimintoihin, jotka eivät kuulu hänen oikeuksiinsa. Tällaiset ongelmat voivat johtaa vakaviin tietoturvaloukkauksiin.

Työkalu nimeltä ffuf soveltuu erinomaisesti verkkopalvelujen tutkimiseen. Sen avulla voidaan automaattisesti kartoittaa esimerkiksi piilotettuja hakemistoja ja tiedostoja, ja edistyneemmillä asetuksilla testata palvelimen käyttäytymistä eri HTTP-headerien avulla.

Tietoturvaraportointiin kuuluu tarkkoja vaatimuksia ja eettisiä sääntöjä. Kaiken dokumentoinnin on perustuttava todellisiin havaintoihin – tietojen keksiminen tai liioittelu heikentää raportin luotettavuutta ja voi johtaa vakaviin seurauksiin.

SQL-injektio on hyökkäystapa, jossa käyttäjä syöttää haitallista koodia esimerkiksi lomakekenttään. Jos syöte ei ole asianmukaisesti suojattu, hyökkääjä voi vaikuttaa taustalla olevaan tietokantaan, esimerkiksi lukea, muokata tai tuhota tietoja.

______________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________

Ensimmäisessä tehtävässä muutin input type kohdan tyhjäksi, jotta sinne voi laittaa ihan mitä vaan, eikä pelkästään numeroita. 

<img width="1025" height="407" alt="Input type" src="https://github.com/user-attachments/assets/c7ad8a6a-b5bc-44db-9535-75a78fd20daa" />

Testasin sen jälkeen ' OR 1=1-- teksti kenttään minkä opin edellisellä tunnilla. Vastaukseksi tuli "foo". Olin oikeilla jäljillä, jes! sitten lähdin lukemaan portswiggeristä ja youtubesta vähän tietoa SQL injectiosta. 
Samalla kun luin huomasin tämän 



<a href="https://portswigger.net/web-security/sql-injection/union-attacks" target="_blank">Portswigger</a>


<img width="738" height="332" alt="Foo_password" src="https://github.com/user-attachments/assets/c9fd9c41-7443-4948-9e9f-dafbd2f67239" />

______________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________

Samalla kun luin huomasin vähän yhtäläisyyksiä kuvan kanssa, löysin lopulta vastauksen mikä on "UNION SELECT password FROM pins--

<img width="750" height="66" alt="image" src="https://github.com/user-attachments/assets/2aece036-ff6c-47a9-b1c7-9b044989422c" />
<img width="982" height="297" alt="SUPERADMIN_password" src="https://github.com/user-attachments/assets/f6698e4d-417d-45c6-a704-e2dc91f13564" />
