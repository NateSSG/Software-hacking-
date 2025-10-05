# Standardit

## A) 3.2 (Hyökkäys / Attack)
Hyökkäys tarkoittaa tahallista toimintaa, jonka tavoitteena on vahingoittaa, muokata, varastaa tai käyttää tietoja ja resursseja luvatta. Se voi kohdistua järjestelmiin, verkkoihin tai käyttäjiin, ja sen tarkoituksena on usein saada taloudellista hyötyä, aiheuttaa haittaa tai paljastaa arkaluonteista tietoa.

Omasta mielestäni hyökkäys ei ole pelkästään tekninen teko, kuten haittaohjelman levittäminen, vaan se voi olla myös sosiaalinen, esimerkiksi tietojenkalastelua tai huijausviestejä, jotka hyödyntävät ihmisten luottamusta. Siksi organisaatioiden on tärkeää panostaa sekä tekniseen suojaukseen että henkilöstön koulutukseen, koska suurin osa hyökkäyksistä onnistuu inhimillisen virheen kautta.

## 3.31 (Tietoturvatapahtuma / Information Security Incident)
Tietoturvatapahtuma tarkoittaa yhtä tai useampaa odottamatonta tapahtumaa, joka liittyy tietoturvaan ja voi vaarantaa organisaation tietojen luottamuksellisuuden, eheyden tai saatavuuden. Se voi olla esimerkiksi palvelunestohyökkäys, tietovuoto, haittaohjelmatartunta tai luvaton pääsy järjestelmään.

Omasta näkökulmastani tietoturvatapahtuman merkittävin piirre on sen vaikutus, joskus pieneltäkin vaikuttava tapaus voi laukaista ketjureaktion, joka lamauttaa kriittisiä toimintoja. Siksi on olennaista, että organisaatiolla on selkeä toimintasuunnitelma (incident response plan), jolla tapahtumat tunnistetaan, analysoidaan ja korjataan nopeasti.

## 3.56 (Vaatimus / Requirement)
Vaatimus tarkoittaa tarvetta, odotusta tai ehtoa, joka tulee täyttää, jotta jokin järjestelmä, prosessi tai palvelu vastaisi asetettuja tavoitteita. Vaatimukset voivat olla lainsäädännöllisiä, sopimuksellisia tai organisaation itse määrittelemiä.

Omasta mielestäni vaatimusten ymmärtäminen ja dokumentointi on yksi tietoturvan peruspilareista, ilman niitä ei voida arvioida, täyttääkö organisaatio turvallisuuden, yksityisyyden tai laadun odotukset. Hyvin määritelty vaatimus toimii myös mittarina, jonka avulla voidaan tarkistaa, onko tietoturvatoimia toteutettu tehokkaasti ja johdonmukaisesti.

## 3.58 (Tarkistus / Review)
Tarkistus on prosessi, jossa arvioidaan, kuinka hyvin tietoturvaan liittyvät käytännöt, toimenpiteet ja järjestelmät vastaavat asetettuja tavoitteita ja vaatimuksia. Tarkistuksen tarkoitus on tunnistaa puutteita, parantaa toimintaa ja varmistaa jatkuva kehitys.

Omasta näkemyksestäni tarkistukset ovat erittäin tärkeitä, koska tietoturva ei ole koskaan valmis tila. Teknologia, uhkat ja liiketoiminnan tarpeet muuttuvat jatkuvasti, joten säännölliset tarkistukset auttavat pitämään järjestelmät ajan tasalla ja minimoimaan riskit. Ne myös osoittavat organisaation sitoutumisen tietoturvaan, mikä lisää luottamusta asiakkaiden ja yhteistyökumppaneiden silmissä.

## 3.77 (Heikkous / Vulnerability)
Heikkous tarkoittaa tietoturvan näkökulmasta omaisuuden tai järjestelmän kohtaa, jota uhka voi hyödyntää. Se voi olla ohjelmiston virhe, huono salasanasuojaus, väärin asetettu palvelin tai jopa kouluttamaton työntekijä.

Omasta mielestäni haavoittuvuuksien tunnistaminen on yksi tärkeimmistä vaiheista tietoturvassa. Yksikin paikkaamaton heikkous voi avata hyökkääjälle oven koko järjestelmään. Siksi organisaatioiden tulisi suorittaa säännöllisiä haavoittuvuusskannauksia ja kouluttaa henkilöstöä tunnistamaan riskit. Tietoturva on loppujen lopuksi yhtä vahva kuin sen heikoin lenkki.

## ISO 27034-1 – 5 (Sovellusturvallisuuden hallinta) 
ISO 27034 -standardi käsittelee sovellusturvallisuuden hallintaa, eli sitä, miten organisaatiot voivat kehittää ja ylläpitää turvallisia sovelluksia koko niiden elinkaaren ajan. Se tarjoaa kehyksen ja ohjeita, joiden avulla tietoturva voidaan sisällyttää suunnittelusta käyttöönottoon ja ylläpitoon.

Standardi ei määrää yksittäisiä teknisiä ratkaisuja, vaan antaa periaatteet ja käytännöt, jotka voidaan sovittaa organisaation tarpeisiin. Tämä auttaa ehkäisemään haavoittuvuuksia, kuten puutteellista syötteiden tarkistusta tai heikkoa salauskäytäntöä, ja tukee turvallisuuskulttuurin luomista sovelluskehitykseen.

## Podcast 
Laatulöpinät-podcastin 30. jaksossa käsitellään tietoturvaa erityisesti ohjelmistokehityksen näkökulmasta. Jakso pohtii muun muassa sitä, miten hallinnollinen ja tekninen tietoturva voidaan yhdistää, millä keinoilla käyttäjiä voidaan ohjata toimimaan tietoturvallisesti, sekä mihin tietoturvajargonia tarvitaan. Podcastin väittämät korostavat, että täydellistä tietoturvaa ei ole olemassa ja että hallinnollinen tietoturva on ratkaisevan tärkeää teknisen tietoturvan onnistumiselle.

## Riskienhallintasuunnitelma
Käytän virtuaalikoneympäristöä, joka on eristetty pääverkosta ja jolla on rajatut resurssit, jotta mahdolliset haittaohjelmat eivät pääse leviämään. Sisään- ja ulos menevä liikenne on suodatettu palomuurilla, ja intrusion detection -järjestelmä havaitsee epäilyttävän toiminnan. Lokit keräävät kaikki tapahtumat jäljitettävyyden varmistamiseksi. Jos epäilen haittaohjelmaa, käytän kill switch -toimintoa katkaistakseni verkkoyhteydet ja siirrän tiedostot karanteeniin, estäen leviämisen ympäristöön.
