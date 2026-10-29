[ 🌐 عربي ](README.ar.md) | [ 🇩🇪 Deutsch ](README.de.md) | [ 🇫🇷 Français ](README.fr.md) | [ 🇳🇱 Nederlands ](README.nl.md) | [ 🇪🇸 Español ](README.sp.md) | [ 🇬🇧 English ](README.md)


# Fondseenheidsverrekening & NAV-boekhouding Excel-sjabloon: eigendom van investeringspools, partnerkapitaalrekeningen en cashflows op meerdere data bijhouden

<div align="left">

![License](https://img.shields.io/badge/license-MIT-blue)
![Platform](https://img.shields.io/badge/platform-Microsoft%20Excel-217346)
![Domain](https://img.shields.io/badge/domain-Fund%20NAV%20Accounting-orange)

**Een dynamisch Microsoft Excel-spreadsheet voor fondseenheidsverrekening en NAV (Net Asset Value)-calculator, gebouwd voor investeringsclubs, vastgoedsyndicaten, particuliere handelspools en family offices die gefaseerde stortingen en terugnames van investeerders beheren.**

[Lanceer de interactieve webdemo van de fondseenheidsverrekening- & NAV-calculator](https://hyvoid.github.io/investment-pool-nav-excel-template/) 

[Download de volledige fondseenheidsverrekening- & NAV-boekhouding Excel-werkmap (gratis)](https://www.theseusworkshop.com/l/FundUnitizationDashboad?utm_source=github&utm_medium=GitHub%20README&utm_campaign=readme%20new%20launch&utm_content=fund-unitization-nav)

</div>

**Fondseenheidsverrekening & NAV-boekhouding Werkmap** is een geautomatiseerde **Microsoft Excel-investeringspooltracker** en **kapitaalrekening-grootboek voor partners**. Het berekent de **Net Asset Value (NAV) per unit**, automatiseert de **prijsstelling bij uitgifte en terugname van units**, voorkomt **verwatering van winst vóór instap** en onderhoudt een **auditklare investeerders-cap table** over gefaseerde stortingsdata heen—zonder dat institutionele fondsadministratiesoftware nodig is.

---

## Visuele preview: NAV-berekeningsengine & dashboard met partnerkapitaalrekeningen

<img width="1536" height="1024" alt="Fund Unitization Excel Template Dashboard showing Net Asset Value per unit and investor ownership percentages" src="https://github.com/user-attachments/assets/42e2fe30-0173-45cc-945a-0d066ac2c974" />
<img width="1672" height="941" alt="Investment Pool Transaction Ledger in Excel tracking staggered capital contributions, withdrawals, and P&L updates" src="https://github.com/user-attachments/assets/1b9a5b9c-5037-4e2a-8ddb-fd1584d48a5c" />
<img width="1448" height="1086" alt="Partner Capital Account Statement in Excel displaying unit issuance, entry NAV pricing, and real-time redemption balances" src="https://github.com/user-attachments/assets/71d0cb5b-76f8-4152-b13d-0b58f792e9bc" />

> Test de rekenkunde van de toewijzing op unitbasis in je browser voordat je downloadt: [Interactieve demo van de simulator voor fondseenheidsverrekening & NAV-boekhouding](https://hyvoid.github.io/Fund-Unitization-NAV-Excel-tool-for-cashflow-management/)

---

## Waarom statische cap tables falen in investeringspools met meerdere stortingsdata

Geschillen over investeringspoolboekhouding ontstaan wanneer thesauriers vaste eigendomspercentages, gefaseerde instapdata en handmatige toerekening van winst en verlies (P&L) combineren in een plat spreadsheet. Wanneer een investeerder maanden later een gedeeltelijke of volledige terugname aanvraagt, legt de reconstructie van het exacte kapitaalrekeningsaldo de structurele zwaktes van statische percentagemodellen bloot.

**De traditionele workflow met statische percentages (hoog geschillenrisico):**

```text
New capital subscription logged
-> Partner ownership percentage split adjusted manually
-> Unrealized pre-entry market gains mixed with new capital
-> Valuation and dilution dispute surfaces at investor withdrawal

```

**De geautomatiseerde NAV-eenheidsverrekening-workflow (auditklaar):**

```text
New capital subscription logged
-> Pool units issued at current mark-to-market NAV per unit
-> Early investors' accumulated gains locked in structurally
-> Real-time capital account balances updated at every cash flow event

```

Poolbeheerders, syndicaat-GP's en clubthesauriers hebben verifieerbare operationele helderheid nodig. Elke gewone partner en beperkte partner moet op elke waarderingsdatum exacte liquidatiesaldi, unitbezit en impliciete eigendomsbelangen kunnen verifiëren.

---

## De bedrijfslogica & methodiek: eenheidsverrekening NAV-boekhouding vs. percentagesplitsingen

Deze werkmap lost het **probleem van kapitaaltoewijzing over meerdere periodes** op met behulp van **eenheidsverrekening volgens de units-methodiek en tijdgewogen Net Asset Value (NAV)-boekhouding** (in lijn met FASB ASC 946 en de IOSCO-waarderingsnormen voor collectieve beleggingen).

### Het commerciële probleem: asynchrone kapitaalstromen vs. continue marktbeweging

In een dynamische investeringspool veranderen twee variabelen asynchroon:

1. **Portefeuillewaardering (markt-P&L):** De onderliggende activa schommelen dagelijks, wekelijks of maandelijks.
2. **Cashflows van deelnemers (inschrijvingen & terugnames):** Investeerders storten of nemen kapitaal op op onregelmatige momenten.

Wanneer een pool eigendom strikt bijhoudt als cumulatief gestort kapitaal gedeeld door het totale poolvermogen, draagt elke storting na een marktwinst een deel van de ongerealiseerde winst van de vroege investeerders over aan de binnenkomende deelnemer. Omgekeerd dwingt een storting na een daling de nieuweling om historische verliezen te subsidiëren die hij nooit heeft gedragen.

### De kernmethodiek: uitgifte van units tegen mark-to-market waardering

In plaats van eigendomspercentages direct aan te passen, scheidt de werkmap **economische prestatie** van **kapitaalverwatering** via een toestandsmachine met drie vergelijkingen die bij elke transactieregel wordt uitgevoerd:

1. **NAV-waardering vóór de transactie:**

$$\text{NAV per Unit}_{t} = \frac{\text{Total Pool Market Value}_{t}}{\text{Total Outstanding Units}_{t-1}}$$



*Zakelijk effect:* Alle gerealiseerde en ongerealiseerde markt-P&L verandert de unitprijs ($\text{NAV per Unit}$), terwijl het unitaantal van elke deelnemer onaangetast blijft.
2. **Prijsstelling van inschrijvingen en terugnames tegen reële waarde:**

$$\text{Units Issued or Redeemed}_{i,t} = \frac{\text{Cash Flow}_{i,t}}{\text{NAV per Unit}_{t}}$$



*Zakelijk effect:* Nieuw kapitaal koopt units tegen de huidige marktaangepaste NAV in plaats van tegen pari. Vroege investeerders behouden 100% van hun winst vóór instap, omdat de binnenkomende investeerder een hogere prijs per unit betaalt.
3. **Doorlopende kapitaalrekening als afgeleide toestand:**

$$\text{Investor Balance}_{i,t} = \text{Units Held}_{i,t} \times \text{NAV per Unit}_{t}$$


$$\text{Economic Ownership \%}_{i,t} = \frac{\text{Units Held}_{i,t}}{\text{Total Outstanding Units}_{t}}$$



*Zakelijk effect:* Eigendomspercentages worden een output die is afgeleid uit het unitbezit in plaats van een handmatige invoertabel. Terugnames worden direct afgewikkeld tegen $\text{Units Redeemed} \times \text{Current NAV}$ zonder enige retroactieve herberekening.

---

## Drie valkuilen van kapitaaltoewijzing in handmatige investeringsspreadsheets

### Valkuil 1: Statische percentagesplitsingen verwateren marktwinst vóór instap

Eigendom toewijzen op basis van het aandeel in de kapitaalbijdrage faalt zodra twee investeerders op verschillende data instappen in een stijgende portefeuille.

Stel dat een investeringspool groeit van $100,000 naar $130,000 (+30% rendement) en dat een tweede investeerder $65,000 stort, waardoor de totale poolactiva op $195,000 uitkomen. Als de beheerder de nieuwe deelnemer een vlak eigendomsbelang van 33.3% toekent ($65,000 / $195,000) zonder het eerdere vermogen via de units-methodiek te verrekenen, verwerft de nieuwe investeerder onmiddellijk een claim op de winst van $30,000 die de eerste investeerder vóór zijn instap behaalde.

Poolbeheerders die vlakke percentagesplitsingen berekenen op stortingsdata ondercompenseren vroege geldschieters routinematig. De boekhoudkundige discrepantie stapelt zich geruisloos op over meerdere financieringsrondes en leidt tot geschillen bij liquidatie.

### Valkuil 2: Excel XIRR gebruiken om partnerkapitaalsaldi te berekenen

De `XIRR`-functie van Excel berekent een geannualiseerd intern rendement over één reeks gedateerde cashflows. Het meet **historische, tijdgewogen prestatie**, terwijl pooladministratie **boekhouding van huidige liquidatiesaldi** vereist.

`XIRR` gebruiken als aandelenverdelingsmechanisme dwingt de thesaurier om aparte cashflowreeksen bij te houden voor elke deelnemer, rendementsstromen opnieuw te berekenen na elke storting, en totale saldi handmatig af te stemmen op de werkelijke effectenrekening. `XIRR` houdt geen doorlopende grootboekstaat bij; elke kapitaaloproeping midden in de periode, elke gedeeltelijke uitkering of elke mark-to-market waarderingsboeking vereist een verse handmatige afstemmingsronde.

### Valkuil 3: Uitgestelde verwateringsafstemming bij de afwikkeling aan het einde van de periode

In traditionele partnerschapsmodellen op percentagebasis worden nieuwe kapitaalinschrijvingen vaak geregistreerd als ruwe cash en pas aan het einde van het kwartaal of jaar afgestemd. Op de afwikkelingsdatum is de exacte portefeuillemarktwaarde op het tijdstip van de storting midden in de periode begraven onder latere marktschommelingen.

Als de portefeuille 25% won vóór een storting midden in het kwartaal en daarna 10% verloor, wist het samennemen van de periode het timingvoordeel van de vroege investeerder. Eenheidsverrekening NAV-boekhouding lost verwatering op het exacte moment op waarop kapitaal binnenkomt, door de transactie te koppelen aan de NAV per unit van die dag.

---

## Voor wie deze fondseenheidsverrekening Excel-sjabloon is

Deze sjabloon bedient beheerders die voorbij ad-hoc percentagespreadsheets zijn gegroeid en logica van **NAV-boekhoudsoftware op institutioneel niveau binnen Microsoft Excel** nodig hebben:

| Rol & zoekpersona | Specifiek operationeel scenario & sjabloongebruik |
| --- | --- |
| **Thesauriers van investeringsclubs** *(Investeringsclub boekhoudspreadsheet)* | Beheer maandelijkse ledenbijdragen, onregelmatige bijschrijvingen en volledige liduitkopen voor 3–20 leden, met verifieerbare kapitaaloverzichten per lid als resultaat. |
| **Syndicaatleiders & GP-beheerders** *(SPV & syndicaat cap table Excel-sjabloon)* | Neem laat-fase kapitaalpartners aan over meerdere closing-tranches (rolling closes), terwijl vroege LP's worden beschermd tegen verwatering van de pre-close waardering. |
| **Startende hedgefondsen & crypto-poolbeheerders** *(Shadow NAV-calculator voor incubatorfondsen)* | Draai een onafhankelijk shadow-accounting grootboek naast effectenrekeningoverzichten om LP-aandeelklassen, unitprijzen en NAV per aandeel bij te houden voordat een externe fondsadministrateur wordt ingehuurd. |
| **Coördinatoren van family offices** *(Werkboek voor de toewijzing van familiale beleggingspools)* | Meng kapitaal uit meerdere familietrusts of generatierekeningen die op verschillende data instappen, met eerlijke P&L-toerekening en schone audittrajecten voor belasting-CPA's. |
| **Leiders van prop trading- & discretionaire groepen** *(Tracker voor de P&L-verdeling van handelspools)* | Geef deelname-units uit wanneer nieuwe traders of geldschieters margekapitaal storten, en wijk gedeeltelijke winstopnames af tegen mark-to-market unitprijzen. |

---

## Praktijkvoorbeelden: scenario's van kapitaaltoewijzing op meerdere data oplossen

### Scenario A: Rolling closes in particuliere investeringssyndicaten & SPV's

Wanneer een syndicaat-general partner (GP) kapitaal aantrekt over drie afzonderlijke sluitingsdata verspreid over zes maanden, terwijl de onderliggende activa al waarderen, eisen vroege limited partners (LP's) bescherming tegen meeliflen door latere tranches. Door elke closing-tranche te boeken als **unitinschrijving tegen de huidige NAV**, kopen latere instappers in tegen de verhoogde unitprijs, waarmee 100% van de pre-close winsten behouden blijft voor Tranche 1-investeerders.

### Scenario B: Lidinstap, bijschrijvingen en uitkopen in aandelen- & crypto-investeringsclubs

Investeringsclubs innen doorgaans ongelijke maandstorten, terwijl bestaande leden bijdragen kunnen pauzeren of gedeeltelijk kunnen uitkassen. In plaats van elke maand de partnerschapsovereenkomsten te heronderhandelen, registreert de clubthesaurier de huidige liquidatiewaarde van de effectenrekening, werkt de **NAV per unit** bij en verwerkt alle maandstorten en uitkoopverzoeken tegen die ene afwikkelingsprijs.

### Scenario C: Incubatorfondsen & friends-and-family handelspools die shadow accounting nodig hebben

Startende fondsbeheerders die een friends-and-family portefeuille van $100K–$5M beheren, rechtvaardigen zelden $15,000+/jaar aan institutionele fondsadministratiekosten. Deze werkmap functioneert als een lokaal **Excel shadow NAV-boekhoudsysteem** en produceert unitgrootboeken op investeerdersniveau, stortingshistorieën en kapitaalrekeningsamenvattingen, klaar voor belastingvoorbereiding door de CPA (Schedule K-1-ondersteuning) of LP-rapportage.

---

## Wat de werkmap bijhoudt: mapping van pijnpunt naar oplossing

| Pijnpunt poolboekhouding | Vaak gezochte vereiste | Ingebouwde Excel-werkmapoplossing |
| --- | --- | --- |
| **Oneerlijke verwatering bij gefaseerde stortingen** | *Winst toewijzen wanneer investeerders op verschillende momenten instappen* | **Geautomatiseerde unituitgifte-engine:** Zet binnenkomende stortingen om in pool-units geprijsd tegen de exacte NAV per unit vóór de storting, waarbij eerdere winsten automatisch worden geïsoleerd. |
| **Fouten bij handmatige P&L-verdeling** | *Investeringspool P&L-toewijzingsspreadsheet* | **Doorlopende NAV-herberekening:** Portefeuillewinsten en -verliezen werken de globale NAV per unit bij; individuele investeerderssaldi (`Units × Current NAV`) passen dynamisch aan zonder handmatige percentagebewerkingen. |
| **Complexe rekenkunde voor gedeeltelijke opnames** | *Uitkoopwaarde / terugnamewaarde van een investeerder berekenen in een partnerschapspool* | **Mark-to-market unitterugname:** Zet opnameverzoeken in dollars om in exacte unitterugnames tegen de huidige NAV, waarbij de saldi van de overige partners onaangetast blijven. |
| **Ondoorzichtig saldo-overzicht voor investeerders** | *Partnerkapitaalrekening-tracker & cap table Excel-sjabloon* | **Realtime dashboard per deelnemer:** Toont per investeerder het netto geïnvesteerde kapitaal, het unitsaldo, het economisch eigendomspercentage, de gewogen instap-NAV en de cumulatieve dollar-P&L. |
| **Wrijving bij audit- & belastingafstemming** | *Auditbaar fondstransactiegrootboek voor CPA-review* | **Chronologische transactie-audittrail:** Registreert elke waarderingsgebeurtenis, storting en terugname met tijdstempel-NAV, unitdelta en poolstatus na de transactie, voor directe CSV/PDF-export. |

---

## Casestudy: handmatige percentageverdeling vs. geautomatiseerde NAV-eenheidsverrekening

**Poolprofiel:** 8 kapitaalpartners die ongelijk storten over 18 maanden in een actief verhandelde portefeuille die in totaal ~40% waardeerde. Aanvankelijk bijgehouden door de leidende beherende partner in een handmatige percentagesplits-spreadsheet.

**De operationele afgang:** Drie investeerders stapten halverwege de cyclus in tijdens maanden met hoge volatiliteit. De beherende partner herberekende de kapitaalbijdragepercentages handmatig na elke storting en verdeelde de maandelijkse P&L op basis van die statische wegingen.

Toen twee vroege partners volledige kapitaalterugnames aanvroegen, stopten drie boekhoudkundige geschillen de uitkeringen:

1. Hoe een portefeuilledaling van 15% halverwege het jaar toe te rekenen, die plaatsvond tussen de financieringsdata van Cohort 1 en Cohort 2.
2. Hoe een partnerstorting van $25,000 te corrigeren die op het verkeerde maandelijkse afstemmingstabblad was geboekt.
3. Welke eigendomspercentagetabel gold voor de laatste gedeeltelijke maand vóór de terugname-afwikkeling.

De reconstructie van de historische kapitaalrekeningen vereiste drie weken forensische boekhouding door een externe CPA.

### Vergelijking: statische percentagespreadsheets vs. eenheidsverrekening NAV-boekhouding

| Boekhoudkundige operatie | Handmatige percentagesplits-spreadsheet (voor) | Geautomatiseerde fondseenheidsverrekening Excel-werkmap (na) |
| --- | --- | --- |
| **Eigendomsmodel** | Statische percentages op basis van kapitaalbijdrage, na elke storting handmatig overschreven | Dynamisch **eenheidsverrekend NAV-model**; units uitgegeven tegen mark-to-market prijs bij storting |
| **Omgaan met late instappers & verwatering** | Nieuw kapitaal verwaterde eerdere ongerealiseerde winsten tenzij per tranche handmatig afgeschermd | **Automatische anti-verwateringsprijsstelling**; binnenkomend kapitaal koopt units tegen de huidige NAV |
| **Periodieke P&L-toewijzing** | Handmatige herberekening aan het einde van de periode over verschuivende partnerpercentagetabellen | **Realtime NAV-per-unit-aanpassing**; unitbalansen van investeerders blijven constant tijdens marktbewegingen |
| **Terugname- & uitkoopafwikkeling door partners** | Forensische reconstructie van historische maandelijkse P&L-tabbladen vereist vóór uitbetaling | **Directe liquidatieprijsstelling** (`Redeemed Units × Current NAV`) direct afgelezen uit het live grootboek |
| **Audittrail & geschiloppervlak** | Hoog foutenrisico bij elke handmatige formule-override en periode-overdracht | **Eén bron: chronologisch transactiegrootboek**; afstemming afgehandeld op het boekhoudniveau |

---

## Institutionele normen achter eenheidsverrekening NAV-boekhouding

Gereguleerde collectieve beleggingsvoertuigen—waaronder mutual funds, ETF's, private equity SPV's en hedgefondsen—vertrouwen op eenheidsverrekening NAV-boekhouding, omdat asynchrone investeerderscashflows een economisch toerekeningsprobleem creëren dat platte percentagetabellen niet kunnen oplossen.

Een investeerder die op dag 90 inschrijft in een waarderende portefeuille droeg het marktrisico van dag 1 tot en met 89 niet. De eenheidsstructuur codeert het instaptijdstip direct in de **inschrijvingsunitprijs (NAV op stortingsdatum)**. Latere marktprestaties stromen uitsluitend door **NAV-per-unit-schommelingen**, terwijl opnames van investeerders worden afgewikkeld tegen de heersende liquidatie-NAV.

| Dimensie fondsboekhouding | Institutioneel NAV-mechanisme geïmplementeerd in deze werkmap |
| --- | --- |
| **Tijdstip van de kapitaalinschrijving** | Vergrendeld in de aankoopprijs van de investeerder via **NAV per unit op stortingsdatum** |
| **Portefeuillemarktprestatie (P&L)** | Uitsluitend weerspiegeld via **NAV-per-unit-beweging**; uitstaande unitaantallen blijven onveranderd |
| **Omvang van de kapitaalbijdrage** | Weerspiegeld in de **hoeveelheid uitgegeven pool-units** ($\text{Deposit} \div \text{Current NAV}$) |
| **Verwateringsbescherming voor bestaande LP's** | Afgedwongen door nieuwe units uit te geven tegen de **huidige mark-to-market NAV** in plaats van de oorspronkelijke pari-waarde |

**Geraadpleegde gezaghebbende boekhoud- & waarderingsnormen:**

* [CFA Institute: Structuur en waardering van pooled beleggingsvoertuigen](https://www.cfainstitute.org)
* [IOSCO: Beginselen voor de waardering van collectieve beleggingsregelingen](https://www.iosco.org)
* [FASB ASC 946: Financiële dienstverlening — boekhoudnormen voor beleggingsmaatschappijen](https://www.fasb.org)

---

## Rekenvoorbeeld: hoe unituitgifte en NAV-prijsstelling werken

De **Net Asset Value per unit** van een pool is gelijk aan de totale portefeuillemarktwaarde gedeeld door het totale aantal uitstaande units. Binnenkomend kapitaal koopt nieuwe units tegen de huidige NAV per unit. Marktwinsten en -verliezen veranderen de NAV per unit terwijl de uitstaande unitaantallen onveranderd blijven.

| Transactiegebeurtenis | Totale poolmarktwaarde | Totale uitstaande units | NAV per unit | Unitdelta van partner & boekhoudkundig effect |
| --- | --- | --- | --- | --- |
| **1. Investeerder A stort $100,000** | $100,000 | 100,000 | $1.000 | Investeerder A krijgt **100,000 units** uitgegeven tegen $1.000 openings-pari-NAV (100% eigendom) |
| **2. Marktwinst portefeuille: +30%** | $130,000 | 100,000 | $1.300 | Unitantal onveranderd; NAV stijgt naar **$1.300/unit** (saldo investeerder A = $130,000) |
| **3. Investeerder B stort $65,000** | $195,000 | 150,000 | $1.300 | Investeerder B koopt **50,000 units** tegen $1.300 NAV (33.33% eigendom; A behoudt $130,000) |
| **4. Marktverlies portefeuille: −15%** | $165,750 | 150,000 | $1.105 | Unitantal onveranderd; NAV daalt naar **$1.105/unit** (A = $110,500; B = $55,250) |
| **5. Investeerder A neemt 50,000 units terug** | $110,250 | 100,000 | $1.105 | Investeerder A neemt **$55,250 cash** op (50,000 × $1.105); houdt 50,000 units (50% van de resterende pool) |

**Waarom de rekenkunde van de eenheidsverrekening elke deelnemer beschermt:**

* **Eerlijke instapprijsstelling:** Investeerder B stort $65,000 wanneer de unitprijs $1.300 is en ontvangt 50,000 units. De winst van $30,000 vóór instap van investeerder A blijft 100% intact binnen de 100,000 units van investeerder A.
* **Proportionele toerekening van dalingen:** Na het marktverlies van 15% daalt de NAV van $1.300 naar $1.105. De 50,000 units van investeerder B zijn $55,250 waard—precies een verlies van 15% absorberend op hun instapkapitaal van $65,000, zonder de eerdere periode van investeerder A te erven of te subsidiëren.

---

## Snelstart-tutorial: je NAV-grootboek voor investeringspools opzetten in 6 stappen

Volg deze stapsgewijze workflow om je investeringsclub, syndicaat of handelspool over te zetten van handmatige percentagesplitsingen naar geautomatiseerde NAV-eenheidsverrekening:

1. **Test je cashflowscenario in de live browsersimulator**
Open de [interactieve webdemo voor fondseenheidsverrekening & NAV-boekhouding](https://hyvoid.github.io/Fund-Unitization-NAV-Excel-tool-for-cashflow-management/) om gefaseerde stortingen, marktp&L-schommelingen en terugnames te simuleren voordat je je live partnerschapsgegevens invoert.
2. **Initialiseer poolparameters en partnerprofielen**
Registreer je initiële investeerders, stel je basisvaluta in en bepaal je openings-pari-NAV per unit (bijv. $1.00 of $100.00 per unit) op de oprichtingsdatum.
3. **Registreer kapitaalinschrijvingen om automatisch units uit te geven**
Leg elke investeerdersstorting vast naast de huidige portefeuillemarktwaarde. De werkmap berekent de heersende NAV per unit en geeft de exacte hoeveelheid fractionele of hele units uit op de kapitaalrekening van de partner.
4. **Registreer periodieke mark-to-market portefeuille-P&L**
Voer gerealiseerde en ongerealiseerde portefeuillewaarderingsupdates in op een dagelijks, wekelijks of maandelijks schema—en onmiddellijk vóór elke externe cashflow—om de NAV per unit van de pool bij te werken.
5. **Verwerk investeerdersopnames en unitterugnames**
Voer gedeeltelijke of volledige terugnameverzoeken in. De engine liquideert het overeenkomstige aantal units tegen de huidige NAV, vermindert het totale aantal uitstaande units en herberekent de eigendomsgewichten na terugname voor de overige partners.
6. **Controleer kapitaalrekeningoverzichten en download de herbruikbare Excel-werkmap**
Controleer de saldointegriteit via de geautomatiseerde foutcontrole-vlaggen en exporteer schone transactielogboeken voor LP-rapportage of belastingvoorbereiding. Zodra je de workflow in de single-session webdemo hebt gevalideerd, **[download dan de volledige, herbruikbare fondseenheidsverrekening & NAV-boekhouding Excel-sjabloon](https://www.theseusworkshop.com/l/FundUnitizationDashboad?utm_source=github&utm_medium=GitHub%20README&utm_campaign=readme%20new%20launch&utm_content=fund-unitization-nav)** om permanente historische grootboeken op te slaan, partnerdashboards aan te passen en doorlopende meerjarige pooloperaties offline in Microsoft Excel te beheren.

*Disclaimer: Deze werkmap is een operationeel boekhoud- en beslissingsondersteuningssjabloon. Raadpleeg een gekwalificeerde CPA of fondsadvocaat over fiscale partnerschapstoerekeningen (bijv. IRC Section 704(b) / Schedule K-1) en effectenrechtelijke naleving in jouw jurisdictie.*

---

## Download de volledige Excel-sjabloon

Klaar om je investeringspoolboekhouding te automatiseren en een permanent, auditbaar partnergrootboek bij te houden?

👉 **[Ontvang de volledige fondseenheidsverrekening & NAV-boekhouding Excel-werkmap (gratis download)](https://www.theseusworkshop.com/l/FundUnitizationDashboad?utm_source=github&utm_medium=GitHub%20README&utm_campaign=readme%20new%20launch&utm_content=fund-unitization-nav)**

---

## Technische reikwijdte & operationele beperkingen

* **Afhankelijkheid van nauwkeurige invoergegevens:** De nauwkeurigheid van de NAV per unit hangt af van het invoeren van mark-to-market portefeuillewaarderingen onmiddellijk vóór het registreren van elke nieuwe kapitaalstorting of -opname.
* **Operationele boekhoudkundige reikwijdte (geen fiscaal/juridisch advies):** Weerspiegelt de standaard rekenkunde van tijdgewogen NAV-eenheidsverrekening; specifieke fiscale partnerschapstoerekeningen, boek-naar-belasting-afstemmingen en regelgevingsaangiften vereisen validatie door een gediplomeerde CPA of juridisch adviseur.
* **Handmatige waarderingsinvoer offline:** Ontworpen voor privacy en nul externe afhankelijkheden; portefeuillemarktwaarden worden handmatig ingevoerd in plaats van via live broker-API's opgehaald.
* **Standaard reikwijdte van kosten & cashflows:** Dek kapitaalinschrijvingen, terugnames en markt-P&L af. Complexe GP/LP carried interest-watervallen, hurdle rates, high-water mark performancekosten en valutadekking over meerdere valuta vallen buiten het bereik van deze basisversie.
* **Aanbevolen poolschaal:** Geoptimaliseerd voor investeringspools met **3 tot 20 deelnemers** die wekelijkse of maandelijkse transacties registreren.
* **Systeemcompatibiliteit:** Gebouwd voor **Microsoft Excel 2016 of later (Windows & macOS)** met standaard native formules en nul macro/VBA-beveiligingsafhankelijkheden.
* **Speciale structurele voorzieningen:** Side-pocket illiquide toewijzingen, lock-up verloopschema's en gated terugnamewachtrijen vereisen aangepaste schema-aanpassingen buiten het kern-grootboektabblad.

---

## Over Theseus Workshop

Wij bouwen transparante, auditklare financiële en operationele Excel-modellen voor kleine fondsen, syndicaten en door operators geleide bedrijven die institutionele boekhoudlogica binnen Microsoft Excel nodig hebben.

Elke sjabloon draait lokaal op native spreadsheetformules, waardoor je team volledig inzicht heeft in elke berekencel en elke grootboekregistratie van eigendom.

Complex werk voor kapitaaltoewijzing, afstemming of eigendomstracking in spreadsheets beheren? **[Bekijk onze volledige bibliotheek met financiële & operationele Excel-sjablonen bij Theseus Workshop →](https://www.theseusworkshop.com)**

---

## Licentie

Gedistribueerd onder de [MIT Open Source-licentie](https://opensource.org/licenses/MIT).

