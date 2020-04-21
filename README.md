## Johdanto

Tämä dokumentti pitää sisällään minun osuuteni Lintukoto-sovelluksen kehittämisestä kevään 2020 Ticorporate Demo Lab-opintojaksolla. 

Dokumentista käy ilmi odotukseni opintojkasolle ja niiden myötä asetetut oppimistavoitteeni. Vertaan niitä siihen mitä lopulta oikeasti opin kevätlukukauden aikana ja missä olisi voinut tehdä toisin. Esittelen myös käytännössä tekemiäni osioita sovelluksesta ja kerron sivutoimistani tuotteenomistajana.

### Asetetut oppimistavoitteet

Vielä kurssin alkaessa olin hyvin epävarma omasta roolistani tiimissä. Puntaroin todella pitkään valitsenko roolin, jossa olen jo kehittynyt (liiketoiminta) vai roolin, jota tuntui etten hahmottanut yhtään (tekniikka). Ohjaajat kuitenkin painottivat, että valitkaa aihe jossa haluatte ensisijaisesti kehittyä. Siksi päätin valita teknisen roolin.

Olin kyllä käynyt web-sovelluskehitys-kurssia koko syksyn aktiivisesti, mutta se maailma ei ollut vielä yhtään avautunut minulle. Tiedän, että opin parhaiten tekemällä, mutta tekemistä helpottaisi jos hahmottaisi isossa kuvassa asioiden merkityksen.
>**Päätin asettaa ensisijaiseksi tavoitteekseni, että sovelluskehityksen maailma alkaisi avautua minulle.**

Näin ymmärtäisin eri asioiden merkityksen ja roolin paremmin. Nollatasolta suunta on kuitenkin vain ylöspäin.

Koska haluan oppia ohjelmoimaan ja mahdollisesti työllistyö sen pariin, oli luonnollista tietysti pyrkiä kehittämään myös niitä kykyjä.
>**Toinen tavoitteeni olikin kehittää ohjelmointitaitoja ihan konkreettisesti, etenkin front-endin osalta.** 

Selkeitä konkreettisia maaleja oli haastava asettaa, koska kokonaiskuvankin hahmottaminen oli vaikeaa. Mutta koska olin päässyt edes tekemään jotain angularilla viime syksynä, uskoin, että siitä minun olisi fiksuinta lähteä syventämään osaamistani. Back-end oli minulle suuri mysteeri, joten sen kohdalla rima oli alempana.

>**Kolmas tavoitteeni oli oppia scrum käytännössä.**

Se on kuitenkin jokin konkreettinen asian jota voi suoraan soveltaa tulevaisuudessa työelämässä. Siksi otin tuoteomistajan roolin mielelläni vastaan. Siitä saa eturivin paikat seurata prosessin pyörittämistä ja olla siihen osallisena. Scrum masterina toimiminen olisi ollut myös vaihtoehto, mutta olin soveltuvin PO-rooliin, joten otin sen siksi ennemmin vastaan.


### Toteutunut oppiminen


## Tekniset toteutukset
Roolini sovelluksen teknisessä toteutuksessa oli front-endin kehittäjänä. Siksi myös konkreettiset tuotokset ovat kaikki käyttöliittymän kehittämisestä.

### Asetukset sivu

TÄHÄN TULEE VIDEO TAI KUVA

Nimensä mukaan, asetukset sivun tarkoitus on antaa käyttäjälle mahdollisuus lisätä omia henkilökohtaisia toiveita sovelluksen osalta. Kaikille asetukset sivun kohdille oli mietitty vaikutukset sovelluksessa, mutta kaikkia ei ehditty toteuttaa kevään aikana. Asetuksien lomakkeessa on kuitenkin kohdat valmiina, vaikka kaikkien osien takana ei olekaan toiminnallisuuksia.

#### Toteutus

```javascript
TÄHÄN TULEE KOODIA
```

#### Haasteet

#### Oppiminen

***

### Henkipöllön pesäsivu

TÄHÄN TULEE VIDEO TAI KUVA

Henkipöllön pesäsivulle on koottu opiskelijalle hyödyllisiä linkkejä. Tämä on yksinkertainen staattinen sivu joka oli nopea tehdä. Sivun sisältö koottiin yhteistyöhön opinto-ohjaajan kanssa.

#### Toteutus

```javascript
TÄHÄN TULEE KOODIA
```

#### Haasteet

#### Oppiminen

***

### Alkuperäinen sisäänkirjautuminen

<img src="./Sovelluskuvat/Kirjautumis_sivu1.PNG" width="500">

Koska sovellus on jokaisella käyttäjällä henkilökohtainen, tarvitaan mahdollisuus kirjautua sisään. Samalla luotiin sovellukseen auth guard, jotta sovelluksen muille sivuille ei pääse ilman, että on kirjautunut sisään.

#### Toteutus

```javascript
TÄHÄN TULEE KOODIA
```

#### Haasteet

#### Oppiminen

***

### Henkipöllön kommentointi-ikkuna

<img src="./Sovelluskuvat/Sisaankirjautumisen_tervehdys.PNG" width="300">

Henkipöllön kommentointi-ikkuna ilmestyy kun käyttäjä kirjautuu sisälle ja kun tämä saa kurssitehtävän tehtyä. Sisääbkirjautumisen osalta toiminnon saa pois asetuksista.

#### Toteutus

Perusteet tälle löytyi [Angular Material-sivulta](https://material.angular.io/components/dialog/overview).
Henkipöllön kommentointi-ikkunalle on luotu oma componentti, jossa Henkipöllön mahdollisista kommenteista arvotaan jokin lause avautuvaan dialogi-ikkunaan.

```typescript
// Taulukko, jossa on kaikki tervehdysvaihtoehdot sisäänkirjautuessa
  tervehdykset = [
    "Olet tehnyt upeasti hommia viime aikoina, hyvää työtä!",
    "Olet ollut mestari ajankäyttäjä. Jatka samaan malliin!",
    "Olen seurannut sinun ahkeraa työskentelyäsi. Osaat hyvin!",
    "Et ole yhtään pöllömpi tyyppi! (◉Θ◉)",
    "Kiva, että tulit taas! Sinua on aina kiva nähdä!",
    "Olet taitava! Olen sinusta ylpeä!",
    "Et taida olla eilisen teeren poikia.",
    "Hienoa katsella, kun joku osaa.",
    "Sinulla on homma hallussa! Ja vaikka ei olisikaan, otat homman kyllä aina lopulta haltuun!",
    "Tähän aktiivisuuteen ei ole kellään nokan koputtamista."
  ];
  
  //arpoo randomilla yhden kehun aiemmin luodusta taulukosta
  randomTervehdys() {
    this.valittuTervehdys = this.tervehdykset[
      Math.floor(Math.random() * this.tervehdykset.length)
    ];
  }
```
Tämä lause viedään html-sivulle yhdessä Henkipöllön kuvan kanssa.

```html
<div class="mat-dialog-content">
  <div class="otsikko">
    <h1 class="mat-dialog-title">Tervetuloa!</h1>
    <p>
      {{ valittuTervehdys }}
    </p>
  </div>
  <!-- <div class="tekstit">
  </div> -->
  <div class="nappi">
    <button class="mat-button" mat-dialog-close>OK</button>
  </div>
  <div class="kuva">
    <img src="../../assets/images/Henkipollo.svg" id="henkipollo_kuva" alt="kuva Henkipöllöstä" />
  </div>
</div>
```

Seuraavaksi valittiin kohta sovelluksesta josta halutaan kommentti-ikkunan avautuvan. Sovelluksessa näitä kohtia olivat sisäänkirjautumisen yhteydessä ja kun sai tehtävän suoritettua. 

Sisään kirjautumisen yhteydessä piti myös huomioida, ettei ikkuna saa aueta jos tunnus tai salasana ovat väärin. Eli vain onnistuneen kirjautumisen jälkeen, ikkuna sai avautua.

Tarkoitus oli, että asetuksista sai valita, haluaako kommentti-ikkunan avautuvan vai ei. Tämä ominaisuus ehdittiin tehdä sisäänkirjautumisen yhteyteen. Jos asetuksien chackbox on rastitettu, ikkuna avautuu, jos ei niin ikkunakaan ei ilmesty sisäänkirjautumisen yhteydessä.

```typescript
this.userService.login(this.loginData).subscribe(
      (res: any) => {
        localStorage.setItem("token", res.token);
        localStorage.setItem("user", this.loginData.tunnus);
        this.router.navigate(["/kalenteri"]);
        // hakee asetuksista tiedon, haluaanko käyttäjä nähdä Henkipöllön tervehdyksen sisään kirjautuessa
        this.http.get(
          "henkipolloOpinnot",
          this.dialogiasetukset.asetusLadattu.henkipolloOpinnot
        );
        // Jos käyttäjä on raksinut asetuksista ruudun jossa sallitaan tervehdys, kutsutaan tervehdyksen käynnitävä metodi
        if (this.dialogiasetukset.asetusLadattu.henkipolloOpinnot == true) {
          this.popup();
        }
      },
      err => {
        alert("Invalid username or password");
      }
    );
    this.AuthService.login();
  }

  // Avaa sisäänkirjautuessa Henkipöllön tervehdyksen popup-ikkunan
  popup() {
    this.dialog.open(DialogComponent);
  }
```

#### Haasteet ja oppiminen
Tämä oli varmasti monimutkaisin kokonaisuus jonka sain tehtyä. Onneksi sen sai tehdä palasissa, että ensin toimiva dialogi-ikkuna ja sitten opeteltiin miten ja mihin kohti koodia se kannattaa laittaa. Huomasin tässä vaiheessa kevättä, että hahmotuskykyni koodin lukemiselle oli kehittynyt. Eli ymmärsin pääpiirteittäin muiden tekemää koodia vaikka en ole ollut sitä itse tekemässä. 

Kokonaisuus vaati lopulta jo ymmärrystä frontin ja backin yhdistämisestä, jonka maailma oli vasta aukenemassa minulle. Sain selvittää kuinka hyödyntää kannassa olevia asetustietoja ja niiden tietojen tarkastuksen jälkeen ikkuna joko avautui tai ei. Tämä oli hyvä ja konkreettinen esimerkki siitä, että vaikka en ole koodannut backiä, sen ymmärtäminen on kriittinen askel kehittyä myös frontti-koodarina. Opin tässä paljon.

## Tuoteomistajana toimiminen
Lintukoto-sovelluksesta kehiteltiin joulukuussa 2019 alustava konsepti, jossa toimin pääideoijana ja suunnittelijana. Tästä syystä minulle oli luonteva rooli ottaa tuoteomistajan eli product ownerin (PO jatkossa) rooli. Tämä rooli oli sivutoimeni kevään 2020 aikana.

PO:na otin vastuun ZehHub ja GitHub työkalumme käyttöönotosta ja ylläpidosta. Niiden osalta työnkuvaani kuului:
* ZenHubin ja GitHubin rakenteen hahmottelu projektia varten
  * Epicien ja UserStrorien kirjoittamisen päävastuu 
  * Sovelluksen eri haarojen (branch) luonti ja käyttöönoton varmistaminen
* Vastuu siitä että GitHubia ja ZenHubia käytetän oikein ja tehokkaasti
  * Järjestää tarvittaessa koulutuksia ohjaajilta koko tiimille
  * Huolehtia siitä että tiimi sopii yhdessä yhteiset koodauskäytänteet ja pitäytyy niissä
* Priorisoida product backlog niin, että ylimpänä listassa on aina tärkeimmät työt sovelluksen kehittymisen kannalta
* Bugikorjauskäytänteiden tuominen ZenHubiin, jotta kuka tahansa voi tehdä bugikorjailuja ja nähdä mitä bugeja muu tiimi työstää
* Pull requestien tarkastaminen ja hyväksyminen yhdessä päätestaajan kanssa

Muut PO-toimet joita kevään aikana hoidin:
* Projektisuunnitelman ja Esitutkimuksen visio-osuuksien kirjoittaminen ja tarvittaessa päivittäminen
* Alussa sovelluksen sisällön ja ulkoasukuvauksen kouluttaminen tiimille
* Vaikuttaa sovelluksen visuaalisen ilmeen kehittymiseen
  * Järjestää palautekeskusteluja ja äänestyksiä ulkoasusta tiimin ulkopuolisten henkilöiden kanssa
* Bugipalaveri testaajien kanssa bugien priorisoinnista ja määristä
* Esitysmateriaalien kasaaminen ja esittäminen (demot ja liiketoimintasuunnitelma)
* Keskustelut opinto-ohjaajan kanssa, jotta sovellus kehittyisi myös opiskelija tuen kannalta oikeaan suuntaan


## Muut aikaansaannokset

* Visual guide
* Liiketoimintasuunnitelman materiaalit
* Markkinointivideossa avustaminen
* Tietokantasuunnitelmapiirros Henrin kanssa
* Sovelluksen kehittymisen tallentaminen videomateriaaleihin joka sprintin päätteeksi
* Mock up kurssitiedot ja kursseille tehtävät
* Tutustuminen sähköisiin allekirjoitustapoihin projektisopimuksen kannalta

## Itsearviointi
