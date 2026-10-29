[ 🌐 عربي ](README.ar.md) | [ 🇩🇪 Deutsch ](README.de.md) | [ 🇫🇷 Français ](README.fr.md) | [ 🇳🇱 Nederlands ](README.nl.md) | [ 🇪🇸 Español ](README.sp.md) | [ 🇬🇧 English ](README.md)


# Excel-Vorlage für Fund Unitization & NAV Accounting: Eigentümerschaft im Investmentpool, Partner-Kapitalkonten und Multi-Date-Cashflows nachverfolgen

<div align="left">

![License](https://img.shields.io/badge/license-MIT-blue)
![Platform](https://img.shields.io/badge/platform-Microsoft%20Excel-217346)
![Domain](https://img.shields.io/badge/domain-Fund%20NAV%20Accounting-orange)

**Eine dynamische Microsoft-Excel-Tabelle zur Fund-Unitisierung und ein Net Asset Value (NAV)-Rechner – entwickelt für Investmentclubs, Immobilien-Syndikate, private Handelspools und Family Offices, die gestaffelte Investoreneinzahlungen und Rücknahmen verwalten.**

[Die interaktive Web-Demo des Fund Unitization & NAV-Rechners starten](https://hyvoid.github.io/investment-pool-nav-excel-template/) 

[Die vollständige Excel-Arbeitsmappe für Fund Unitization & NAV Accounting herunterladen (kostenlos)](https://www.theseusworkshop.com/l/FundUnitizationDashboad?utm_source=github&utm_medium=GitHub%20README&utm_campaign=readme%20new%20launch&utm_content=fund-unitization-nav)

</div>

Die **Fund Unitization & NAV Accounting Workbook** ist ein automatisierter **Microsoft Excel Investment-Pool-Tracker** und ein **Partner-Kapitalkonto-Ledger**. Sie berechnet den **Net Asset Value (NAV) pro Anteil**, automatisiert die **Preisbildung für Anteilsausgabe und Rücknahme**, verhindert die **Verwässerung von Gewinnen vor dem Eintritt** und führt eine **prüffähige Investoren-Cap-Table** über gestaffelte Einzahlungsdaten hinweg – ganz ohne institutionelle Fondsverwaltungssoftware.

---

## Visuelle Vorschau: NAV-Berechnungs-Engine & Partner-Kapitalkonto-Dashboard

<img width="1536" height="1024" alt="Fund Unitization Excel Template Dashboard showing Net Asset Value per unit and investor ownership percentages" src="https://github.com/user-attachments/assets/42e2fe30-0173-45cc-945a-0d066ac2c974" />
<img width="1672" height="941" alt="Investment Pool Transaction Ledger in Excel tracking staggered capital contributions, withdrawals, and P&L updates" src="https://github.com/user-attachments/assets/1b9a5b9c-5037-4e2a-8ddb-fd1584d48a5c" />
<img width="1448" height="1086" alt="Partner Capital Account Statement in Excel displaying unit issuance, entry NAV pricing, and real-time redemption balances" src="https://github.com/user-attachments/assets/71d0cb5b-76f8-4152-b13d-0b58f792e9bc" />

> Testen Sie die anteilsbasierte Zuordnungsmathematik im Browser, bevor Sie herunterladen: [Interaktive Fund Unitization & NAV Accounting Simulator-Demo](https://hyvoid.github.io/Fund-Unitization-NAV-Excel-tool-for-cashflow-management/)

---

## Warum statische Cap Tables in Investmentpools mit mehreren Einzahlungsdaten scheitern

Streitigkeiten über die Pool-Buchhaltung entstehen, wenn Schatzmeister feste Eigentümerschaftsprozentsätze, gestaffelte Kapitaleintrittsdaten und manuelle Gewinn-und-Verlust-(P&L)-Zuordnungen in einer flachen Tabelle kombinieren. Wenn ein Investor Monate später eine Teil- oder Voltrücknahme anfordert, deckt die Rekonstruktion seines exakten Kapitalkontosaldos strukturelle Schwächen statischer Prozentsatzmodelle auf.

**Der herkömmliche statische Prozentsatz-Workflow (hohes Streitrisiko):**

```text
New capital subscription logged
-> Partner ownership percentage split adjusted manually
-> Unrealized pre-entry market gains mixed with new capital
-> Valuation and dilution dispute surfaces at investor withdrawal

```

**Der automatisierte NAV-Unitisierungs-Workflow (prüffähig):**

```text
New capital subscription logged
-> Pool units issued at current mark-to-market NAV per unit
-> Early investors' accumulated gains locked in structurally
-> Real-time capital account balances updated at every cash flow event

```

Pool-Betreiber, Syndikats-GPs und Club-Schatzmeister benötigen überprüfbare operative Klarheit. Jeder Komplementär und Kommanditist muss exakte Liquidationssalden, Anteilsbestände und implizite Eigentümerschaftsanteile zu jedem Bewertungsstichtag verifizieren können.

---

## Die Geschäftslogik & Methodik: Unitisierte NAV-Bewertung vs. Prozentsatzaufteilungen

Diese Arbeitsmappe löst das **Mehrperioden-Kapitalzuordnungsproblem** mittels **Unitisierung nach Fondsmodell und zeitgewichteter Net Asset Value (NAV)-Bewertung** (ausgerichtet an FASB ASC 946 und den IOSCO-Standards zur Bewertung kollektiver Investmentvehikel).

### Das geschäftliche Problem: Asynchrone Kapitalflüsse vs. kontinuierliche Marktbewegung

In einem dynamischen Investmentpool ändern sich zwei Variablen asynchron:

1. **Portfolio-Bewertung (Markt-P&L):** Die zugrunde liegenden Assets schwanken täglich, wöchentlich oder monatlich.
2. **Teilnehmer-Cashflows (Zeichnungen & Rücknahmen):** Investoren zahlen Kapital in unregelmäßigen Abständen ein oder ab.

Verfolgt ein Pool die Eigentümerschaft streng über die kumulierte Einzahlungssumme geteilt durch das gesamte Pool-Eigenkapital, dann überträgt jede Einzahlung nach einem Marktgewinn einen Teil der unrealisierten Gewinne der frühen Investoren auf den neuen Teilnehmer. Umgekehrt zwingt eine Einzahlung nach einem Drawdown den Neueintretenden, historische Verluste mitzufinanzieren, die er nie erlitten hat.

### Die Kernmethodik: Anteilsausgabe zum Marktwert (Mark-to-Market)

Statt Eigentümerschaftsprozentsätze direkt anzupassen, trennt die Arbeitsmappe **wirtschaftliche Performance** von **Kapitalverwässerung** durch eine Zustandsmaschine mit drei Gleichungen, die bei jeder Transaktionszeile ausgeführt wird:

1. **NAV-Bewertung vor der Transaktion:**

$$\text{NAV per Unit}_{t} = \frac{\text{Total Pool Market Value}_{t}}{\text{Total Outstanding Units}_{t-1}}$$



*Geschäftlicher Effekt:* Alle realisierten und unrealisierten Markt-P&L-Veränderungen wirken sich auf den Anteilspreis ($\text{NAV per Unit}$) aus, ohne die Anteilsanzahl eines Teilnehmers zu verändern.
2. **Preisbildung für Zeichnung & Rücknahme zum Fair Value:**

$$\text{Units Issued or Redeemed}_{i,t} = \frac{\text{Cash Flow}_{i,t}}{\text{NAV per Unit}_{t}}$$



*Geschäftlicher Effekt:* Neues Kapital kauft Anteile zur aktuellen, marktgerechten NAV und nicht zum Nennwert. Frühe Investoren behalten 100% ihrer Wertsteigerung vor dem Eintritt, weil der neue Investor einen höheren Preis pro Anteil zahlt.
3. **Kontinuierlich abgeleiteter Kapitalkonto-Zustand:**

$$\text{Investor Balance}_{i,t} = \text{Units Held}_{i,t} \times \text{NAV per Unit}_{t}$$


$$\text{Economic Ownership \%}_{i,t} = \frac{\text{Units Held}_{i,t}}{\text{Total Outstanding Units}_{t}}$$



*Geschäftlicher Effekt:* Eigentümerschaftsprozentsätze werden zu einer aus den Anteilsbeständen abgeleiteten Ausgabe statt einer manuellen Eingabetabelle. Rücknahmen werden sofort zu $\text{Units Redeemed} \times \text{Current NAV}$ abgerechnet, ganz ohne rückwirkende Neuberechnung.

---

## Drei Kapitalzuordnungsfallen in manuellen Investment-Tabellen

### Falle 1: Statische Prozentsatzaufteilungen verwässern Marktgewinne vor dem Eintritt

Weist man Eigentümerschaft nach dem Anteil an der Kapitaleinlage zu, scheitert dieses Modell genau in dem Moment, in dem zwei Investoren zu unterschiedlichen Daten in ein steigendes Portfolio eintreten.

Angenommen, ein Investmentpool wächst von $100,000 auf $130,000 (+30% Rendite), und ein zweiter Investor zahlt $65,000 ein, wodurch die Pool-Gesamtassets $195,000 erreichen. Weist der Betreiber dem neuen Teilnehmer einen pauschalen Eigentümerschaftsanteil von 33.3% zu ($65,000 / $195,000), ohne das bisherige Eigenkapital zu unitisieren, erhält der neue Investor sofort einen Anspruch auf den $30,000-Gewinn des ersten Investors aus der Zeit vor dessen Eintritt.

Pool-Betreiber, die bei Einzahlungsdaten pauschale Prozentsatzaufteilungen berechnen, benachteiligen frühere Geldgeber routinemäßig. Die buchhalterische Abweichung vergrößert sich lautlos über mehrere Finanzierungsrunden hinweg und löst bei der Liquidation Streitigkeiten aus.

### Falle 2: Excel-XIRR zur Berechnung von Partner-Kapitalsalden verwenden

Die Excel-Funktion `XIRR` berechnet eine annualisierte interne Rendite über eine einzige Reihe datierter Cashflows. Sie misst die **historische, zeitadjustierte Performance**, während die Pool-Verwaltung eine **Bewertung der aktuellen Liquidationssalden** erfordert.

Verwendet man `XIRR` als Eigenkapitalzuordnungsmechanismus, muss der Schatzmeister für jeden Teilnehmer separate Cashflow-Arrays pflegen, die Renditeverläufe nach jeder Einzahlung neu berechnen und die Gesamtsalden manuell gegen das tatsächliche Brokerage-Eigenkapital abstimmen. `XIRR` hält keinen kontinuierlichen Ledger-Zustand; jeder Kapitalabruf während der Periode, jede Teilausschüttung und jede Mark-to-Market-Bewertungsbuchung erfordert einen neuen manuellen Abstimmungsdurchlauf.

### Falle 3: Aufgeschobene Verwässerungsabstimmung bei der Periodenendabwicklung

In traditionellen prozentsatzbasierten Partnerschaftsmodellen werden neue Kapitalzeichnungen oft als reine Bareingänge erfasst und erst zum Quartals- oder Jahresabschluss abgestimmt. Zum Abwicklungstermin ist der exakte Portfolio-Marktwert zum Zeitpunkt der Einzahlung mitten in der Periode unter den nachfolgenden Marktschwankungen begraben.

Gewann das Portfolio 25% vor einer Einzahlung mitten im Quartal und verlor danach 10%, löscht die pauschale Zusammenfassung der Periode den Timing-Vorteil des frühen Investors. Die unitisierte NAV-Bewertung löst die Verwässerung genau in dem Moment, in dem das Kapital eingeht, indem sie die Transaktion an die NAV pro Anteil dieses Tages bindet.

---

## Für wen diese Fund-Unitisierungs-Excel-Vorlage gedacht ist

Diese Vorlage richtet sich an Betreiber, die über Ad-hoc-Prozentsatztabellen hinausgewachsen sind und institutionelle **NAV-Bewertungs-Softwarelogik in Microsoft Excel** benötigen:

| Rolle & Suchpersona | Konkretes Betriebsszenario & Anwendungsfall der Vorlage |
| --- | --- |
| **Schatzmeister von Investmentclubs** *(Investment Club Accounting Spreadsheet)* | Monatliche Mitgliedsbeiträge, unregelmäßige Nachschüsse und vollständige Mitgliederauszahlungen für 3–20 Mitglieder verwalten und dabei überprüfbare Mitglieds-Kapitalabrechnungen erstellen. |
| **Syndikats-Leads & GP-Betreiber** *(SPV & Syndikat Cap Table Excel-Vorlage)* | Kapitalpartner in späteren Phasen über mehrere Closing-Tranchen (Rolling Closes) hinweg aufnehmen und dabei frühe LPs vor Bewertungsverwässerung vor dem Close schützen. |
| **Manager aufstrebender Hedgefonds & Krypto-Pools** *(Incubator Fund Shadow NAV Calculator)* | Ein unabhängiges Shadow-Accounting-Ledger neben den Brokerage-Kontoauszügen führen, um LP-Anteilklassen, Anteilspreise und NAV pro Anteil zu verfolgen, bevor ein Drittanbieter-Fondsadministrator beauftragt wird. |
| **Family-Office-Koordinatoren** *(Family Investment Pool Allocation Workbook)* | Kapital aus mehreren Familienstiftungen oder Generationenkonten mit unterschiedlichen Eintrittsdaten zusammenführen und dabei eine faire P&L-Zurechnung sowie saubere Prüfpfade für die Steuer-CPAs sicherstellen. |
| **Leads von Prop-Trading- & diskretionären Gruppen** *(Trading Pool P&L Distribution Tracker)* | Partizipationsanteile ausgeben, wenn neue Trader oder Geldgeber Margin-Kapital einzahlen, und teilweise Gewinnauszahlungen zu Mark-to-Market-Anteilspreisen abwickeln. |

---

## Anwendungsfälle aus der Praxis: Szenarien der Kapitalzuordnung über mehrere Daten hinweg lösen

### Szenario A: Rolling Closes in privaten Investmentsyndikaten & SPVs

Wenn der Komplementär (General Partner, GP) eines Syndikats über drei separate Closing-Termine innerhalb von sechs Monaten Kapital aufnimmt, während die zugrunde liegenden Assets bereits an Wert gewinnen, verlangen frühe Kommanditisten (Limited Partners, LPs) Schutz vor Free-Riding späterer Tranchen. Indem jede Closing-Tranche als **Anteilszeichnung zur aktuellen NAV** gebucht wird, kaufen spätere Einsteiger zum gestiegenen Anteilspreis ein, wodurch 100% der Gewinne vor dem Close für die Tranche-1-Investoren erhalten bleiben.

### Szenario B: Mitgliederbeitritt, Nachschüsse und Auszahlungen in Aktien- & Krypto-Investmentclubs

Investmentclubs ziehen typischerweise ungleiche monatliche Einzahlungen ein und erlauben bestehenden Mitgliedern, Beiträge auszusetzen oder sich teilweise auszahlen zu lassen. Statt die Partnerschaftsvereinbarungen jeden Monat neu zu verhandeln, erfasst der Club-Schatzmeister den aktuellen Liquidationswert des Brokerage-Kontos, aktualisiert die **NAV pro Anteil** und wickelt alle monatlichen Einzahlungen und Auszahlungsanfragen zu diesem einen Abrechnungskurs ab.

### Szenario C: Inkubatorfonds & Friends-and-Family-Handelspools mit Bedarf an Shadow Accounting

Aufstrebende Fondsmanager, die ein Friends-and-Family-Portfolio von $100K–$5M verwalten, rechtfertigen selten institutionelle Fondsverwaltungsgebühren von $15,000+/Jahr. Diese Arbeitsmappe fungiert als lokales **Excel-Shadow-NAV-Bewertungssystem** und erzeugt Anteils-Ledgers auf Investorenebene, Einzahlungshistorien und Kapitalkonto-Zusammenfassungen, bereit für die Steuererstellung durch den CPA (Schedule K-1-Unterstützung) oder das LP-Reporting.

---

## Was die Arbeitsmappe verfolgt: Zuordnung von Schmerzpunkten zu Lösungen

| Schmerzpunkt der Pool-Buchhaltung | Häufig gesuchte Anforderung | Eingebaute Excel-Arbeitsmappen-Lösung |
| --- | --- | --- |
| **Unfaire Verwässerung bei gestaffelten Einzahlungen** | *Wie man Gewinne zuordnet, wenn Investoren zu unterschiedlichen Zeiten beitreten* | **Automatisierte Anteilsausgabe-Engine:** Wandelt eingehende Bareinzahlungen in Pool-Anteile um, die zum exakten NAV pro Anteil vor der Einzahlung bepreist sind, und isoliert frühere Gewinne automatisch. |
| **Manuelle Fehler bei der P&L-Verteilung** | *Investment-Pool-P&L-Zuordnungstabelle* | **Kontinuierliche NAV-Neuberechnung:** Portfolio-Gewinne und -Verluste aktualisieren die globale NAV pro Anteil; die einzelnen Investorensalden (`Units × Current NAV`) passen sich dynamisch an – ganz ohne manuelle Prozentsatzänderungen. |
| **Komplizierte Rechnungen bei Teilauszahlungen** | *Auszahlungs-/Rücknahmewert eines Investors im Partnerschaftspool berechnen* | **Anteilsrücknahme zum Marktwert (Mark-to-Market):** Wandelt Auszahlungsanfragen in Dollar in exakte Anteilsrücknahmen zur aktuellen NAV um und lässt die Salden der übrigen Partner unangetastet. |
| **Intransparente Investorensaldo-Berichte** | *Partner-Kapitalkonto-Tracker & Cap Table Excel-Vorlage* | **Echtzeit-Dashboard pro Teilnehmer:** Zeigt das investierte Nettokapital, den Anteilsbestand, den wirtschaftlichen Eigentümerschafts-%, die gewichtete Eintritts-NAV und den kumulativen Dollar-P&L jedes Investors. |
| **Reibung bei Prüfung & Steuerabstimmung** | *Prüffähiges Fonds-Transaktionsledger für die CPA-Prüfung* | **Chronologischer Transaktions-Audit-Trail:** Protokolliert jedes Bewertungsereignis, jede Einzahlung und jede Rücknahme mit zeitgestempelter NAV, Anteilsdelta und Pool-Zustand nach der Transaktion für sofortigen CSV/PDF-Export. |

---

## Fallstudie: Manuelle Prozentsatzzuordnung vs. automatisierte NAV-Unitisierung

**Pool-Profil:** 8 Kapitalpartner zahlen über 18 Monate ungleich in ein aktiv gehandeltes Portfolio ein, das sich insgesamt um ~40% wertsteigerte. Zunächst vom federführenden verwaltenden Partner in einer manuellen Prozentsatzsplit-Tabelle verfolgt.

**Der operative Zusammenbruch:** Drei Investoren traten mitten im Zyklus in Monaten hoher Volatilität bei. Der verwaltende Partner berechnete die Kapitalbeteiligungsprozentsätze nach jeder Einzahlung manuell neu und verteilte den monatlichen P&L nach diesen statischen Gewichten.

Als zwei frühe Partner die vollständige Kapitalrücknahme beantragten, blockierten drei buchhalterische Streitigkeiten die Ausschüttungen:

1. Wie ein 15%iger Portfolio-Drawdown mitten im Jahr zuzuordnen ist, der zwischen den Finanzierungsdaten von Kohorte 1 und Kohorte 2 auftrat.
2. Wie eine Partner-Einzahlung von $25,000 zu korrigieren ist, die im falschen monatlichen Abstimmungs-Tab erfasst worden war.
3. Welche Eigentümerschaftsprozentsatztabelle für den letzten Teilmonat vor der Rücknahmeabwicklung galt.

Die Rekonstruktion der historischen Kapitalkonten erforderte drei Wochen Forensic Accounting durch einen externen CPA.

### Vergleich: Statische Prozentsatztabellen vs. unitisierte NAV-Bewertung

| Buchhaltungsvorgang | Manuelle Prozentsatzsplit-Tabelle (vorher) | Automatisierte Fund-Unitisierungs-Excel-Arbeitsmappe (nachher) |
| --- | --- | --- |
| **Eigenkapital-Eigentümerschaftsmodell** | Statische Kapitaleinlage-Prozentsätze, nach jeder Einzahlung manuell überschrieben | Dynamisches **unitisiertes NAV-Modell**; Anteile werden bei Einzahlung zum Mark-to-Market-Preis ausgegeben |
| **Behandlung von Späteinsteigern & Verwässerung** | Neues Kapital verwässerte frühere unrealisierte Gewinne, sofern nicht pro Tranche manuell abgeschottet | **Automatische Anti-Verwässerungs-Preisbildung**; eingehendes Kapital kauft Anteile zur aktuellen NAV |
| **Periodische P&L-Zuordnung** | Manuelle Neuberechnung zum Periodenende über sich verschiebende Partner-Prozentsatztabellen | **Echtzeit-Anpassung der NAV pro Anteil**; die Anteilsbestände der Investoren bleiben bei Marktbewegungen konstant |
| **Partner-Rücknahme & Auszahlungsabwicklung** | Forensische Rekonstruktion historischer monatlicher P&L-Tabs vor der Auszahlung erforderlich | **Sofortige Liquidationspreisbildung** (`Redeemed Units × Current NAV`), direkt aus dem Live-Ledger abgelesen |
| **Audit-Trail & Streitfläche** | Hohes Fehlerrisiko bei jeder manuellen Formelüberschreibung und jedem Perioden-Rollforward | **Chronologisches Transaktionsledger aus einer einzigen Quelle**; die Abstimmung erfolgt auf der Buchhaltungsebene |

---

## Institutionelle Standards hinter der unitisierten NAV-Bewertung

Regulierte kollektive Investmentvehikel – darunter Investmentfonds, ETFs, Private-Equity-SPVs und Hedgefonds – setzen auf unitisierte Net Asset Value-Bewertung, weil asynchrone Investoren-Cashflows ein wirtschaftliches Zurechnungsproblem schaffen, das flache Prozentsatztabellen nicht lösen können.

Ein Investor, der an Tag 90 in ein steigendes Portfolio zeichnet, trug das Marktrisiko der Tage 1 bis 89 nicht. Die unitisierte Struktur kodiert das Einstiegstiming direkt in den **Zeichnungsanteilspreis (NAV am Einzahlungsdatum)**. Die nachfolgende Marktperformance fließt ausschließlich durch die **Schwankungen der NAV pro Anteil**, während Investorenauszahlungen zur jeweils geltenden Liquidations-NAV abgerechnet werden.

| Dimension der Fonds-Buchhaltung | Institutioneller NAV-Mechanismus in dieser Arbeitsmappe |
| --- | --- |
| **Zeitpunkt der Kapitalzeichnung** | Verankert im Kaufpreis des Investors über die **NAV pro Anteil am Einzahlungsdatum** |
| **Portfolio-Marktperformance (P&L)** | Spiegelt sich ausschließlich in der **Bewegung der NAV pro Anteil**; die Anzahl der ausstehenden Anteile bleibt unverändert |
| **Höhe der Kapitaleinlage** | Spiegelt sich in der **Menge der ausgegebenen Pool-Anteile** ($\text{Deposit} \div \text{Current NAV}$) |
| **Verwässerungsschutz für bestehende LPs** | Durchgesetzt durch die Ausgabe neuer Anteile zur **aktuellen Mark-to-Market-NAV** statt zum anfänglichen Nennwert |

**Referenzierte maßgebliche Bewertungs- und Rechnungslegungsstandards:**

* [CFA Institute: Struktur und Bewertung von Pooled Investment Vehicles](https://www.cfainstitute.org)
* [IOSCO: Grundsätze für die Bewertung kollektiver Kapitalanlagen](https://www.iosco.org)
* [FASB ASC 946: Financial Services — Rechnungslegungsstandards für Investmentgesellschaften](https://www.fasb.org)

---

## Durchgerechnetes Zahlenbeispiel: Wie Anteilsausgabe und NAV-Preisbildung funktionieren

Der **Net Asset Value pro Anteil** eines Pools entspricht dem gesamten Portfolio-Marktwert geteilt durch die Gesamtzahl der ausstehenden Anteile. Eingehendes Kapital kauft neue Anteile zur aktuellen NAV pro Anteil. Marktgewinne und -verluste verändern die NAV pro Anteil, während die Anzahl der ausstehenden Anteile unverändert bleibt.

| Transaktionsereignis | Gesamter Pool-Marktwert | Ausstehende Anteile insgesamt | NAV pro Anteil | Anteilsdelta der Partner & buchhalterische Auswirkung |
| --- | --- | --- | --- | --- |
| **1. Investor A zahlt $100,000 ein** | $100,000 | 100,000 | $1.000 | Investor A erhält **100,000 Anteile** zur Eröffnungs-NAV von $1.000 (Nennwert) ausgestellt (100% Eigentümerschaft) |
| **2. Portfolio-Marktgewinn: +30%** | $130,000 | 100,000 | $1.300 | Anteilsanzahl unverändert; die NAV steigt auf **$1.300/Anteil** (Saldo von Investor A = $130,000) |
| **3. Investor B zahlt $65,000 ein** | $195,000 | 150,000 | $1.300 | Investor B kauft **50,000 Anteile** zur NAV von $1.300 (33.33% Eigentümerschaft; A behält $130,000) |
| **4. Portfolio-Marktverlust: −15%** | $165,750 | 150,000 | $1.105 | Anteilsanzahl unverändert; die NAV fällt auf **$1.105/Anteil** (A = $110,500; B = $55,250) |
| **5. Investor A löst 50,000 Anteile ein** | $110,250 | 100,000 | $1.105 | Investor A hebt **$55,250 in bar** ab (50,000 × $1.105); hält 50,000 Anteile (50% des verbleibenden Pools) |

**Warum die unitisierte Rechnung jeden Teilnehmer schützt:**

* **Faire Einstiegspreisbildung:** Investor B zahlt $65,000 ein, wenn der Anteilspreis $1.300 beträgt, und erhält dafür 50,000 Anteile. Der $30,000-Gewinn von Investor A aus der Zeit vor dem Eintritt bleibt zu 100% innerhalb seiner 100,000 Anteile unangetastet.
* **Proportionale Drawdown-Zurechnung:** Nach dem 15%igen Marktverlust fällt die NAV von $1.300 auf $1.105. Die 50,000 Anteile von Investor B sind $55,250 wert – er absorbiert exakt einen 15%igen Verlust auf sein Einstiegskapital von $65,000, ohne die frühere Periode von Investor A zu erben oder zu subventionieren.

---

## Schnellstart-Tutorial: Ihr Investment-Pool-NAV-Ledger in 6 Schritten einrichten

Folgen Sie diesem Schritt-für-Schritt-Workflow, um Ihren Investmentclub, Ihr Syndikat oder Ihren Handelspool von manuellen Prozentsatzsplits zur automatisierten NAV-Unitisierung zu überführen:

1. **Testen Sie Ihr Cashflow-Szenario im Live-Browser-Simulator**
Öffnen Sie die [interaktive Web-Demo für Fund Unitization & NAV Accounting](https://hyvoid.github.io/Fund-Unitization-NAV-Excel-tool-for-cashflow-management/), um gestaffelte Einzahlungen, Markt-P&L-Schwankungen und Rücknahmen zu simulieren, bevor Sie Ihre echten Partnerschaftszahlen eingeben.
2. **Pool-Parameter und Partnerprofile initialisieren**
Registrieren Sie Ihre anfänglichen Investoren, legen Sie Ihre Basiswährung fest und definieren Sie Ihre Eröffnungs-NAV pro Anteil zum Nennwert (z. B. $1.00 oder $100.00 pro Anteil) zum Startdatum.
3. **Kapitalzeichnungen erfassen, um Anteile automatisch auszugeben**
Erfassen Sie jede Investoreneinzahlung zusammen mit dem aktuellen Portfolio-Marktwert. Die Arbeitsmappe berechnet die geltende NAV pro Anteil und schreibt die exakte Bruchteil- oder Gesamtanzahl an Anteilen dem Kapitalkonto des Partners gut.
4. **Periodisches Mark-to-Market-Portfolio-P&L erfassen**
Erfassen Sie realisierte und unrealisierte Portfolio-Bewertungsaktualisierungen täglich, wöchentlich oder monatlich – und unmittelbar vor jedem externen Cashflow –, um die NAV pro Anteil des Pools zu aktualisieren.
5. **Investorenauszahlungen und Anteilsrücknahmen abwickeln**
Geben Sie Teil- oder Voltrücknahme-Anfragen ein. Die Engine liquidiert die entsprechende Anzahl an Anteilen zur aktuellen NAV, verringert die Gesamtzahl der ausstehenden Anteile und berechnet die Eigentümerschaftsgewichte nach der Rücknahme für die verbleibenden Partner neu.
6. **Kapitalkonto-Auszüge prüfen und die wiederverwendbare Excel-Arbeitsmappe herunterladen**
Überprüfen Sie die Saldointegrität über die automatisierten Fehlerprüf-Flags und exportieren Sie saubere Transaktionsprotokolle für das LP-Reporting oder die Steuervorbereitung. Sobald Sie den Workflow in der Web-Demo für eine Sitzung validiert haben, **[laden Sie die vollständige, wiederverwendbare Fund-Unitisierungs- & NAV-Accounting-Excel-Vorlage herunter](https://www.theseusworkshop.com/l/FundUnitizationDashboad?utm_source=github&utm_medium=GitHub%20README&utm_campaign=readme%20new%20launch&utm_content=fund-unitization-nav)**, um dauerhafte historische Ledgers zu speichern, Partner-Dashboards anzupassen und laufende mehrjährige Pool-Betriebe offline in Microsoft Excel zu verwalten.

*Haftungsausschluss: Diese Arbeitsmappe ist eine betriebliche Buchhaltungs- und Entscheidungsunterstützungsvorlage. Ziehen Sie einen qualifizierten CPA oder Fondsanwalt zu Fragen der steuerlichen Zuordnung in Partnerschaften (z. B. IRC Section 704(b) / Schedule K-1) und der Wertpapier-Compliance in Ihrer Rechtsordnung hinzu.*

---

## Die vollständige Excel-Vorlage herunterladen

Bereit, die Buchhaltung Ihres Investmentpools zu automatisieren und ein dauerhaftes, prüffähiges Partner-Ledger zu führen?

👉 **[Holen Sie sich die vollständige Fund Unitization & NAV Accounting Excel-Arbeitsmappe (kostenloser Download)](https://www.theseusworkshop.com/l/FundUnitizationDashboad?utm_source=github&utm_medium=GitHub%20README&utm_campaign=readme%20new%20launch&utm_content=fund-unitization-nav)**

---

## Technischer Umfang & betriebliche Einschränkungen

* **Abhängigkeit von der Eingabedatengenauigkeit:** Die Genauigkeit der NAV pro Anteil hängt davon ab, Mark-to-Market-Portfolio-Bewertungen unmittelbar vor der Erfassung jeder neuen Kapitaleinzahlung oder -auszahlung einzugeben.
* **Betrieblicher Buchhaltungsumfang (keine Steuer-/Rechtsberatung):** Spiegelt die Standard-Mathematik der zeitgewichteten NAV-Unitisierung wider; spezifische steuerliche Partnerschaftszuordnungen, Buch-zu-Steuer-Abstimmungen und regulatorische Einreichungen erfordern eine Validierung durch einen zugelassenen CPA oder Rechtsanwalt.
* **Manuelle Bewertungseingabe offline:** Ausgelegt auf Privatsphäre und null externe Abhängigkeiten; Portfolio-Marktwerte werden manuell eingegeben und nicht über Live-Brokerage-APIs abgerufen.
* **Standard-Umfang für Gebühren & Cashflows:** Deckt Kapitalzeichnungen, Rücknahmen und Markt-P&L ab. Komplexe GP/LP-Carried-Interest-Wasserfälle, Hurdle Rates, High-Water-Mark-Performance-Gebühren und Multiwährungs-FX-Absicherung liegen außerhalb des Umfangs dieser Basisversion.
* **Empfohlene Pool-Größe:** Optimiert für Investmentpools mit **3 bis 20 Teilnehmern**, die wöchentliche oder monatliche Transaktionen erfassen.
* **Systemkompatibilität:** Gebaut für **Microsoft Excel 2016 oder höher (Windows & macOS)**, unter Verwendung Standard-nativer Formeln ohne jegliche Makro-/VBA-Sicherheitsabhängigkeiten.
* **Besondere Strukturvorkehrungen:** Side-Pocket-Zuordnungen illiquider Positionen, Lock-up-Ablaufpläne und gated Rücknahmewarteschlangen erfordern individuelle Terminanpassungen außerhalb des Kern-Ledger-Tabs.

---

## Über Theseus Workshop

Wir entwickeln transparente, prüffähige Finanz- und operative Excel-Modelle für kleine Fonds, Syndikate und operator-geführte Unternehmen, die institutionelle Buchhaltungslogik in Microsoft Excel benötigen.

Jede Vorlage läuft lokal auf nativen Tabellenkalkulationsformeln und gibt Ihrem Team volle Einsicht in jede Berechnungszelle und jede Eigentümerschafts-Ledger-Eintragung.

Verwalten Sie komplexe Kapitalzuordnungs-, Abstimmungs- oder Eigentümerschaftsverfolgungs-Workflows in Tabellen? **[Entdecken Sie unsere vollständige Bibliothek Finanz- & operativer Excel-Vorlagen bei Theseus Workshop →](https://www.theseusworkshop.com)**

---

## Lizenz

Vertrieben unter der [MIT-Open-Source-Lizenz](https://opensource.org/licenses/MIT).

