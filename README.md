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


```markdown
<h1>Asetukset</h1>
    <form (ngSubmit)="onSubmit(form1.value)" #form1="ngForm">
      <div class="form-group">
        <label for="aloituspaiva">Opintojen aloituspäivä</label>
        <br/>
        <input
          type="text" [value]="tunnus" hidden [(ngModel)]="asetuslomake.tunnus" name="tunnus"/>
        <!--Max-arvo on tällä puolella 2020-05-05 mutta ts-tiedoston puolelta siihen syötetään aina current date, 
            joten tästä ei tarvitse välittää-->
        <input
          type="date" id="datefield" min="1990-01-01" max="2020-05-05" [(ngModel)]="asetuksetLadattu.asetukset.aloituspaiva"
          name="aloituspaiva" class="form-control" [value]="asetuksetLadattu.asetukset.aloituspaiva"/>
      </div>

      <div class="form-group">
        <label for="ryhmatunnus">Ryhmätunnus</label>
        <br/>
        <input
          type="text" [(ngModel)]="asetuksetLadattu.asetukset.ryhmatunnus" class="form-control"
          name="ryhmatunnus" [value]="asetuksetLadattu.asetukset.ryhmatunnus"
        />
      </div>

      <div class="form-group">
        <label class="bold" for="kokonaisOp"
          >Koulutusohjelman opintopisteiden kokonaismäärä</label
        ><br />
        <input
          type="number"
          min="0"
          max="800"
          [(ngModel)]="asetuksetLadattu.asetukset.kokonaisOp"
          class="form-control"
          name="kokonaisOp"
          [placeholder]="asetuksetLadattu.asetukset.kokonaisOp"
          [value]="asetuksetLadattu.asetukset.kokonaisOp"
        />
      </div>

      <!--checkboxit tästä eteenpäin-->
      <!--checkboxeilla varmistetaan kiinnostusta yhdessä opiskeluun, pöllöjen näkyminen sivuilla sekä henkipöllön asetukset-->
      <div class="form-check">
        <label class="form-check-label bold" for="yhteisetTuokiot"
          >Olen kiinnostunut osallistumaan mahdollisiin ryhmäni
          opiskelutuokioihin</label
        ><br />
        <input
          type="checkbox"
          [(ngModel)]="asetuksetLadattu.asetukset.yhteisetTuokiot"
          name="yhteisetTuokiot"
          class="form-check-input"
        />
        Kyllä<br />
      </div>

      <div class="form-check">
        <label class="form-check-label bold" for="pollojenNakyminen"
          >Haluan nähdä pöllöt sovelluksessani:</label
        ><br />
        <input
          type="checkbox"
          [(ngModel)]="asetuksetLadattu.asetukset.pollojenNakyminen"
          checked="checked"
          name="pollojenNakyminen"
          class="form-check-input"
        />
        Kyllä<br />
      </div>

      <div class="form-check">
        <label class="form-check-label bold" for="henkipollonAsetukset"
          >Haluan nämä Henkipöllön ominaisuudet:</label
        ><br />
        <div>
          <label
            class="form-check-label labeli"
            for="henkipolloOpinnot"
          ></label>
          <input
            type="checkbox"
            [(ngModel)]="asetuksetLadattu.asetukset.henkipolloOpinnot"
            name="henkipolloOpinnot"
            checked="checked"
            class="form-check-input inblock"
          />
          Tervehdys sisäänkirjautuessa
        </div>
        <!-- Opinnot<br /> -->
        <div>
          <label class="form-check-label labeli" for="henkipolloElama"></label>
          <input
            type="checkbox"
            [(ngModel)]="asetuksetLadattu.asetukset.henkipolloElama"
            name="henkipolloElama"
            checked="checked"
            class="form-check-input inblock"
          />
          Kehut suoritettuani jotain
        </div>
        <!-- Elämänhallinta<br /> -->
        <div>
          <label
            class="form-check-label labeli"
            for="henkipolloValistus"
          ></label>
          <input
            type="checkbox"
            [(ngModel)]="asetuksetLadattu.asetukset.henkipolloValistus"
            name="henkipolloValistus"
            checked="checked"
            class="form-check-input inblock"
          />
          Apu jos opinnoissa on haasteita
        </div>
        <!-- Valistus<br /> -->
      </div>

      <!--Radio-napit, joilla kysytään onko opiskeluajankohdalla väliä-->
      <div class="form-check">
        <label class="form-check-label bold" for="opiskeluajankohta"
          >Opiskelen tehokkaimmin tähän aikaan päivästä:</label
        ><br />
        <input
          type="radio"
          name="opiskeluajankohta"
          [(ngModel)]="asetuksetLadattu.asetukset.opiskeluajankohta"
          class="form-check-input"
          value="milloinVain"
        />
        Mihin aikaan vain<br />
        <input
          type="radio"
          name="opiskeluajankohta"
          [(ngModel)]="asetuksetLadattu.asetukset.opiskeluajankohta"
          class="form-check-input"
          value="aamupaiva"
        />
        Aamupäivä<br />
        <input
          type="radio"
          name="opiskeluajankohta"
          [(ngModel)]="asetuksetLadattu.asetukset.opiskeluajankohta"
          class="form-check-input"
          value="iltapaiva"
        />
        Iltapäivä<br />
      </div>

      <!--Tallennusnappi-->
      <div class="btn-container">
        <div>
          <button
            class=" btn btn-primary tallennusnappi"
            type="submit"
            value="Submit"
          >
            Tallenna
          </button>
          <p id="ilmoitus" class="piilotaIlmoitus">Asetukset tallennettu!</p>
        </div>
      </div>
    </form>
  </div>
```

#### Toteutus

[Image](https://jamkstudent-my.sharepoint.com/:i:/g/personal/m2936_student_jamk_fi/ETXxptZ0d49Nm38MbstL78QBuftxZrgHmPfWfxyKU5RFhw?e=xw7q4Z)

#### Haasteet

#### Oppiminen



### Henkipöllön pesäsivu

#### Toteutus

#### Haasteet

#### Oppiminen



### Alkuperäinen sisäänkirjautuminen

#### Toteutus

#### Haasteet

#### Oppiminen



### Henkipöllön kommentointi-ikkuna

#### Toteutus

#### Haasteet

#### Oppiminen



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
