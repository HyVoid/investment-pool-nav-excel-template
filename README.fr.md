[ 🌐 عربي ](README.ar.md) | [ 🇩🇪 Deutsch ](README.de.md) | [ 🇫🇷 Français ](README.fr.md) | [ 🇳🇱 Nederlands ](README.nl.md) | [ 🇪🇸 Español ](README.sp.md) | [ 🇬🇧 English ](README.md)


# Modèle Excel de comptabilisation par unités et de valeur liquidative (NAV) d'un fonds : suivre la détention d'un pool d'investissement, les comptes de capital des associés et les flux de trésorerie multi-dates

<div align="left">

![License](https://img.shields.io/badge/license-MIT-blue)
![Platform](https://img.shields.io/badge/platform-Microsoft%20Excel-217346)
![Domain](https://img.shields.io/badge/domain-Fund%20NAV%20Accounting-orange)

**Un tableur dynamique Microsoft Excel de comptabilisation par unités de fonds et calculateur de valeur liquidative (NAV), conçu pour les clubs d'investissement, les syndicats immobiliers, les pools de négociation privés et les family offices qui gèrent des souscriptions et des rachats d'investisseurs échelonnés dans le temps.**

[Lancer la démo web interactive du calculateur de comptabilisation par unités et de NAV de fonds](https://hyvoid.github.io/investment-pool-nav-excel-template/) 

[Télécharger le classeur Excel complet de comptabilisation par unités et de comptabilité NAV de fonds (gratuit)](https://www.theseusworkshop.com/l/FundUnitizationDashboad?utm_source=github&utm_medium=GitHub%20README&utm_campaign=readme%20new%20launch&utm_content=fund-unitization-nav)

</div>

**Le classeur de comptabilisation par unités et de comptabilité NAV de fonds** est un **suivi automatisé de pool d'investissement Microsoft Excel** et un **registre des comptes de capital des associés**. Il calcule la **valeur liquidative (NAV) par part**, automatise **l'émission de parts et la tarification des rachats**, prévient la **dilution des profits pré-entrée** et maintient une **table de capitalisation des investisseurs prête pour l'audit** sur des dates de souscription échelonnées, sans nécessiter de logiciel institutionnel d'administration de fonds.

---

## Aperçu visuel : moteur de calcul de la NAV et tableau de bord des comptes de capital des associés

<img width="1536" height="1024" alt="Fund Unitization Excel Template Dashboard showing Net Asset Value per unit and investor ownership percentages" src="https://github.com/user-attachments/assets/42e2fe30-0173-45cc-945a-0d066ac2c974" />
<img width="1672" height="941" alt="Investment Pool Transaction Ledger in Excel tracking staggered capital contributions, withdrawals, and P&L updates" src="https://github.com/user-attachments/assets/1b9a5b9c-5037-4e2a-8ddb-fd1584d48a5c" />
<img width="1448" height="1086" alt="Partner Capital Account Statement in Excel displaying unit issuance, entry NAV pricing, and real-time redemption balances" src="https://github.com/user-attachments/assets/71d0cb5b-76f8-4152-b13d-0b58f792e9bc" />

> Testez la mathématique d'allocation par parts dans votre navigateur avant de télécharger : [Démo du simulateur interactif de comptabilisation par unités et de comptabilité NAV de fonds](https://hyvoid.github.io/Fund-Unitization-NAV-Excel-tool-for-cashflow-management/)

---

## Pourquoi les tables de capitalisation statiques échouent dans les pools d'investissement multi-dates

Les litiges comptables dans les pools d'investissement surviennent lorsque les trésoriers combinent des pourcentages de détention figés, des dates d'entrée en capital échelonnées et des imputations manuelles du compte de résultat (P&L) dans un tableur plat. Lorsqu'un investisseur demande un rachat partiel ou total plusieurs mois plus tard, la reconstitution de son solde exact de compte de capital révèle les failles structurelles des modèles à pourcentages statiques.

**Le flux de travail hérité à pourcentages statiques (risque de litige élevé) :**

```text
New capital subscription logged
-> Partner ownership percentage split adjusted manually
-> Unrealized pre-entry market gains mixed with new capital
-> Valuation and dilution dispute surfaces at investor withdrawal

```

**Le flux de travail automatisé de comptabilisation par unités NAV (prêt pour l'audit) :**

```text
New capital subscription logged
-> Pool units issued at current mark-to-market NAV per unit
-> Early investors' accumulated gains locked in structurally
-> Real-time capital account balances updated at every cash flow event

```

Les opérateurs de pools, les GP de syndicats et les trésoriers de clubs ont besoin d'une clarté opérationnelle vérifiable. Chaque associé commandité et commanditaire doit pouvoir vérifier les soldes exacts de liquidation, les parts détenues et les participations implicites à toute date de valorisation.

---

## La logique métier et la méthodologie : comptabilité NAV par unités vs. répartitions en pourcentage

Ce classeur résout le **problème d'allocation de capital multi-périodes** en utilisant la **comptabilisation par unités à la manière des fonds mutuels et la comptabilité de la valeur liquidative (NAV) pondérée dans le temps** (conforme à FASB ASC 946 et aux normes de l'IOSCO sur l'évaluation des investissements collectifs).

### Le problème commercial : flux de capitaux asynchrones vs. mouvement continu du marché

Dans un pool d'investissement dynamique, deux variables évoluent de manière asynchrone :

1. **Valorisation du portefeuille (P&L de marché) :** les actifs sous-jacents fluctuent chaque jour, chaque semaine ou chaque mois.
2. **Flux de trésorerie des participants (souscriptions et rachats) :** les investisseurs déposent ou retirent des capitaux à intervalles irréguliers.

Lorsqu'un pool suit la détention strictement par le cumul du capital apporté divisé par les fonds propres totaux du pool, chaque dépôt effectué après un gain de marché transfère une partie du profit non réalisé des premiers investisseurs au participant entrant. Inversement, un dépôt effectué après une baisse oblige le nouvel entrant à subventionner des pertes historiques qu'il n'a jamais subies.

### La méthodologie centrale : émission de parts à la valeur de marché

Plutôt que d'ajuster directement les pourcentages de détention, le classeur sépare la **performance économique** de la **dilution du capital** grâce à une machine à états à trois équations exécutée à chaque ligne de transaction :

1. **Valorisation NAV pré-transaction :**

$$\text{NAV per Unit}_{t} = \frac{\text{Total Pool Market Value}_{t}}{\text{Total Outstanding Units}_{t-1}}$$



*Effet métier :* toutes les variations de P&L de marché, réalisé et non réalisé, modifient le prix de la part ($\text{NAV per Unit}$), sans toucher au nombre de parts de chaque participant.
2. **Tarification des souscriptions et rachats à la juste valeur :**

$$\text{Units Issued or Redeemed}_{i,t} = \frac{\text{Cash Flow}_{i,t}}{\text{NAV per Unit}_{t}}$$



*Effet métier :* le nouveau capital achète des parts à la NAV ajustée au marché actuelle plutôt qu'à la valeur nominale. Les premiers investisseurs conservent 100 % de leur plus-value pré-entrée, car l'investisseur entrant paie un prix par part plus élevé.
3. **État dérivé du compte de capital en continu :**

$$\text{Investor Balance}_{i,t} = \text{Units Held}_{i,t} \times \text{NAV per Unit}_{t}$$


$$\text{Economic Ownership \%}_{i,t} = \frac{\text{Units Held}_{i,t}}{\text{Total Outstanding Units}_{t}}$$



*Effet métier :* les pourcentages de détention deviennent un résultat dérivé des parts détenues plutôt qu'une table de saisie manuelle. Les rachats se règlent immédiatement à $\text{Units Redeemed} \times \text{Current NAV}$ sans aucun recalcul rétroactif.

---

## Trois pièges d'allocation de capital dans les tableurs d'investissement manuels

### Piège 1 : les répartitions statiques en pourcentage diluent les gains de marché pré-entrée

Attribuer la détention selon la part de contribution en capital échoue dès que deux investisseurs entrent dans un portefeuille en hausse à des dates différentes.

Supposons qu'un pool d'investissement passe de $100,000 à $130,000 (rendement de +30 %), et qu'un second investisseur apporte $65,000, portant l'actif total du pool à $195,000. Si l'opérateur attribue au nouveau participant une part de détention fixe de 33.3 % ($65,000 / $195,000) sans comptabiliser par unités les fonds propres antérieurs, le nouvel investisseur capte immédiatement un droit sur le gain pré-entrée de $30,000 du premier investisseur.

Les opérateurs de pools qui calculent des répartitions plates en pourcentage aux dates de contribution sous-compensent régulièrement les premiers investisseurs. L'écart comptable s'accumule silencieusement sur plusieurs tours de financement et déclenche des litiges lors de la liquidation.

### Piège 2 : utiliser Excel XIRR pour calculer les soldes de capital des associés

La fonction `XIRR` d'Excel calcule un taux de rendement interne annualisé sur une seule série de flux de trésorerie datés. Elle mesure la **performance historique ajustée du temps**, alors que l'administration d'un pool exige une **comptabilité du solde de liquidation courant**.

Utiliser `XIRR` comme mécanisme d'allocation du capital oblige le trésorier à maintenir des tableaux de flux de trésorerie séparés pour chaque participant, à recalculer les séries de rendement après chaque dépôt et à rapprocher manuellement les soldes totaux avec les fonds propres réels du courtage. `XIRR` ne conserve aucun état de registre continu ; chaque appel de capital en cours de période, chaque distribution partielle ou chaque écriture de valorisation au marché exige une nouvelle passe de rapprochement manuel.

### Piège 3 : rapprochement de dilution différé au règlement de fin de période

Dans les modèles de partenariat traditionnels basés sur les pourcentages, les nouvelles souscriptions de capital sont souvent enregistrées comme de la trésorerie brute et rapprochées uniquement à la clôture trimestrielle ou annuelle. À la date de règlement, la valeur de marché exacte du portefeuille au moment du dépôt en cours de période est enfouie sous les mouvements de marché ultérieurs.

Si le portefeuille a gagné 25 % avant un dépôt en cours de trimestre et perdu 10 % ensuite, fusionner la période efface l'avantage de temporalité du premier investisseur. La comptabilisation par unités NAV résout la dilution au moment exact où le capital est réglé, en verrouillant la transaction sur la NAV par part de ce jour-là.

---

## À qui s'adresse ce modèle Excel de comptabilisation par unités de fonds

Ce modèle s'adresse aux opérateurs qui ont dépassé les tableurs ad hoc en pourcentages et ont besoin d'une **logique de logiciel de comptabilité NAV de niveau institutionnel dans Microsoft Excel** :

| Rôle et persona de recherche | Scénario opérationnel spécifique et cas d'usage du modèle |
| --- | --- |
| **Trésoriers de clubs d'investissement** *(Comptabilité de club d'investissement sur tableur)* | Gérer les cotisations mensuelles des membres, les compléments irréguliers et les rachats complets de membres pour 3 à 20 membres, tout en produisant des relevés de capital vérifiables. |
| **Responsables de syndicats et opérateurs GP** *(Modèle Excel de table de capitalisation SPV et syndicat)* | Intégrer des partenaires de capital en stade avancé sur plusieurs tranches de clôture (rolling closes) tout en protégeant les premiers LP de la dilution de valorisation pré-clôture. |
| **Gérants émergents de hedge funds et de pools crypto** *(Calculateur shadow NAV de fonds incubateur)* | Tenir un registre de comptabilité parallèle indépendant à côté des relevés de courtage pour suivre les classes de parts LP, les prix des parts et la NAV par part avant de recruter un administrateur de fonds tiers. |
| **Coordinateurs de family office** *(Classeur d'allocation de pool d'investissement familial)* | Mixer les capitaux de plusieurs trusts familiaux ou comptes générationaux entrant à des dates différentes, en garantissant une imputation équitable du P&L et des pistes d'audit propres pour les CPA fiscalistes. |
| **Responsables de groupes de trading prop et discrétionnaires** *(Suivi de distribution de P&L de pool de trading)* | Émettre des parts de participation lorsque de nouveaux traders ou apporteurs déposent du capital sur marge, et régler les retraits partiels de profits aux prix de parts au marché. |

---

## Cas d'usage réels : résoudre des scénarios d'allocation de capital multi-dates

### Scénario A : clôtures successives dans les syndicats d'investissement privés et les SPV

Lorsqu'un associé commandité (GP) de syndicat lève des capitaux sur trois dates de clôture distinctes en six mois alors que les actifs sous-jacents s'apprécient déjà, les premiers commanditaires (LP) exigent une protection contre le free-riding des tranches ultérieures. En enregistrant chaque tranche de clôture comme une **souscription de parts à la NAV courante**, les entrants tardifs achètent au prix de part relevé, préservant 100 % des gains pré-clôture pour les investisseurs de la tranche 1.

### Scénario B : entrées de membres, compléments et rachats dans les clubs d'investissement actions et crypto

Les clubs d'investissement collectent typiquement des dépôts mensuels inégaux tout en permettant aux membres existants de suspendre leurs contributions ou de sortir partiellement. Plutôt que de renégocier les accords de partenariat chaque mois, le trésorier du club enregistre la valeur de liquidation courante du compte de courtage, met à jour la **NAV par part** et traite tous les dépôts mensuels et demandes de rachat à ce prix unique de règlement.

### Scénario C : fonds incubateurs et pools de trading entre amis et famille nécessitant une comptabilité parallèle

Les gérants de fonds émergents qui gèrent un portefeuille entre amis et famille de $100K–$5M justifient rarement des frais d'administration de fonds institutionnels de $15,000+/an. Ce classeur fonctionne comme un **système Excel local de comptabilité shadow NAV**, produisant des registres de parts par investisseur, des historiques de contributions et des synthèses de comptes de capital prêts pour la préparation fiscale par un CPA (prise en charge du Schedule K-1) ou le reporting LP.

---

## Ce que suit le classeur : correspondance entre points sensibles et solutions

| Point sensible comptable du pool | Exigence de recherche à haute fréquence | Solution intégrée du classeur Excel |
| --- | --- | --- |
| **Dilution injuste sur les dépôts échelonnés** | *Comment imputer le profit lorsque les investisseurs entrent à des moments différents* | **Moteur d'émission de parts automatisé :** convertit les dépôts de trésorerie entrants en parts du pool au prix exact de la NAV par part pré-dépôt, isolant automatiquement les gains antérieurs. |
| **Erreurs de distribution manuelle du P&L** | *Tableur d'imputation de P&L de pool d'investissement* | **Recalcul NAV en continu :** les gains et pertes du portefeuille mettent à jour la NAV par part globale ; les soldes individuels des investisseurs (`Units × Current NAV`) s'ajustent dynamiquement sans aucune édition manuelle de pourcentages. |
| **Calculs complexes de retraits partiels** | *Calculer la valeur de rachat / sortie d'un investisseur dans un pool de partenariat* | **Rachat de parts au marché :** convertit les demandes de retrait en dollars en rachats exacts de parts à la NAV courante, laissant intacts les soldes des partenaires restants. |
| **Reporting opaque des soldes des investisseurs** | *Suivi des comptes de capital des associés et table de capitalisation — modèle Excel* | **Tableau de bord en temps réel par participant :** affiche le capital net investi, le solde de parts, le pourcentage de détention économique, la NAV d'entrée pondérée et le P&L cumulé en dollars de chaque investisseur. |
| **Friction de rapprochement audit et fiscalité** | *Registre de transactions de fonds auditable pour revue CPA* | **Piste d'audit chronologique des transactions :** journalise chaque événement de valorisation, dépôt et rachat avec la NAV horodatée, le delta de parts et l'état du pool post-transaction pour un export CSV/PDF instantané. |

---

## Étude de cas : allocation manuelle en pourcentages vs. comptabilisation par unités NAV automatisée

**Profil du pool :** 8 associés en capital contribuant de manière inégale sur 18 mois dans un portefeuille activement négocié qui s'est apprécié d'environ 40 % au total. Suivi initialement par le gérant principal dans un tableur manuel de répartition en pourcentages.

**La panne opérationnelle :** trois investisseurs ont rejoint le cycle en cours de période, durant des mois de forte volatilité. Le gérant recalculait manuellement les pourcentages de contribution en capital après chaque dépôt et répartissait le P&L mensuel selon ces poids statiques.

Lorsque deux premiers associés ont demandé le rachat total de leur capital, trois litiges comptables ont bloqué les distributions :

1. Comment imputer un repli de 15 % du portefeuille en milieu d'année survenu entre les dates de financement de la cohorte 1 et de la cohorte 2.
2. Comment corriger un dépôt de $25,000 d'un associé comptabilisé dans le mauvais onglet de rapprochement mensuel.
3. Quelle table de pourcentages de détention régissait le dernier mois partiel avant le règlement du rachat.

La reconstitution des comptes de capital historiques a exigé trois semaines de comptabilité judiciaire par un CPA externe.

### Comparaison : tableurs à pourcentages statiques vs. comptabilité NAV par unités

| Opération comptable | Tableur manuel de répartition en pourcentages (avant) | Classeur Excel automatisé de comptabilisation par unités de fonds (après) |
| --- | --- | --- |
| **Modèle de détention du capital** | Pourcentages de contribution en capital statiques, écrasés manuellement après chaque dépôt | **Modèle NAV par unités** dynamique ; parts émises au prix du marché lors du dépôt |
| **Traitement des entrants tardifs et de la dilution** | Le nouveau capital diluait les gains non réalisés antérieurs sauf isolement manuel par tranche | **Tarification anti-dilution automatique** ; le capital entrant achète des parts à la NAV courante |
| **Imputation périodique du P&L** | Recalcul manuel de fin de période sur des tables de pourcentages de partenaires en évolution | **Ajustement de la NAV par part en temps réel** ; les soldes de parts des investisseurs restent constants pendant les mouvements de marché |
| **Règlement des rachats et sorties des associés** | Reconstitution judiciaire des onglets mensuels de P&L historique requise avant tout paiement | **Tarification de liquidation instantanée** (`Redeemed Units × Current NAV`) lue directement dans le registre en direct |
| **Piste d'audit et surface de litige** | Risque d'erreur élevé à chaque écrasement manuel de formule et report de période | **Registre chronologique des transactions à source unique** ; le rapprochement est traité au niveau comptable |

---

## Normes institutionnelles derrière la comptabilité NAV par unités

Les véhicules d'investissement collectif réglementés — fonds mutuels, ETF, SPV de capital-investissement et hedge funds — s'appuient sur la comptabilité de valeur liquidative par unités parce que les flux de trésorerie asynchrones des investisseurs créent un problème d'attribution économique que les tables plates de pourcentages ne peuvent pas résoudre.

Un investisseur qui souscrit au jour 90 dans un portefeuille en appréciation n'a pas porté le risque de marché des jours 1 à 89. La structure par unités encode le calendrier d'entrée directement dans le **prix de souscription de la part (NAV à la date de dépôt)**. La performance de marché ultérieure transite strictement par les **fluctuations de la NAV par part**, tandis que les retraits des investisseurs se règlent à la NAV de liquidation en vigueur.

| Dimension comptable du fonds | Mécanisme NAV institutionnel implémenté dans ce classeur |
| --- | --- |
| **Calendrier de souscription du capital** | Verrouillé dans le prix d'achat de l'investisseur via la **NAV par part à la date de dépôt** |
| **Performance de marché du portefeuille (P&L)** | Reflétée strictement par le **mouvement de la NAV par part** ; le nombre de parts en circulation reste inchangé |
| **Taille de la contribution en capital** | Reflétée dans la **quantité de parts du pool émises** ($\text{Deposit} \div \text{Current NAV}$) |
| **Protection contre la dilution pour les LP existants** | Garantie par l'émission de nouvelles parts à la **NAV au marché courante** plutôt qu'à la valeur nominale initiale |

**Normes comptables et d'évaluation de référence :**

* [CFA Institute : structure et valorisation des véhicules d'investissement collectifs](https://www.cfainstitute.org)
* [IOSCO : principes pour la valorisation des fonds d'investissement collectifs](https://www.iosco.org)
* [FASB ASC 946 : services financiers — normes comptables des sociétés d'investissement](https://www.fasb.org)

---

## Exemple numérique détaillé : fonctionnement de l'émission de parts et de la tarification NAV

La **valeur liquidative par part** d'un pool est égale à la valeur de marché totale du portefeuille divisée par le nombre total de parts en circulation. Le capital entrant achète de nouvelles parts à la NAV par part courante. Les gains et pertes de marché modifient la NAV par part sans changer le nombre de parts en circulation.

| Événement de transaction | Valeur de marché totale du pool | Total des parts en circulation | NAV par part | Delta de parts des associés et impact comptable |
| --- | --- | --- | --- | --- |
| **1. L'investisseur A dépose $100,000** | $100,000 | 100,000 | $1.000 | L'investisseur A se voit émettre **100,000 parts** à la NAV nominale d'ouverture de $1.000 (100 % de détention) |
| **2. Gain de marché du portefeuille : +30 %** | $130,000 | 100,000 | $1.300 | Nombre de parts inchangé ; la NAV monte à **$1.300/part** (solde de l'investisseur A = $130,000) |
| **3. L'investisseur B dépose $65,000** | $195,000 | 150,000 | $1.300 | L'investisseur B achète **50,000 parts** à la NAV de $1.300 (33.33 % de détention ; A conserve $130,000) |
| **4. Perte de marché du portefeuille : −15 %** | $165,750 | 150,000 | $1.105 | Nombre de parts inchangé ; la NAV descend à **$1.105/part** (A = $110,500 ; B = $55,250) |
| **5. L'investisseur A rachète 50,000 parts** | $110,250 | 100,000 | $1.105 | L'investisseur A retire **$55,250 en espèces** (50,000 × $1.105) ; détient 50,000 parts (50 % du pool restant) |

**Pourquoi la mathématique par unités protège chaque participant :**

* **Tarification d'entrée équitable :** l'investisseur B apporte $65,000 alors que le prix de la part est de $1.300 et reçoit 50,000 parts. Le profit pré-entrée de $30,000 de l'investisseur A reste 100 % intact dans les 100,000 parts de l'investisseur A.
* **Imputation proportionnelle du repli :** après la perte de marché de 15 %, la NAV passe de $1.300 à $1.105. Les 50,000 parts de l'investisseur B valent $55,250 — absorbant exactement une perte de 15 % sur son capital d'entrée de $65,000, sans hériter ni subventionner la période antérieure de l'investisseur A.

---

## Tutoriel de démarrage rapide : configurer votre registre NAV de pool d'investissement en 6 étapes

Suivez ce flux de travail étape par étape pour faire passer votre club d'investissement, votre syndicat ou votre pool de trading des répartitions manuelles en pourcentages à la comptabilisation par unités NAV automatisée :

1. **Testez votre scénario de flux de trésorerie dans le simulateur en ligne**
Ouvrez la [démo web interactive de comptabilisation par unités et de comptabilité NAV de fonds](https://hyvoid.github.io/Fund-Unitization-NAV-Excel-tool-for-cashflow-management/) pour simuler des dépôts échelonnés, des fluctuations de P&L de marché et des rachats avant de saisir les chiffres réels de votre partenariat.
2. **Initialisez les paramètres du pool et les profils des associés**
Enregistrez vos investisseurs initiaux, définissez votre devise de base et établissez votre NAV nominale d'ouverture par part (par ex. $1.00 ou $100.00 par part) à la date de constitution.
3. **Journalisez les souscriptions de capital pour émettre les parts automatiquement**
Enregistrez chaque dépôt d'investisseur avec la valeur de marché courante du portefeuille. Le classeur calcule la NAV par part en vigueur et émet la quantité exacte de parts, fractionnaire ou entière, au compte de capital de l'associé.
4. **Enregistrez le P&L de marché périodique du portefeuille**
Saisissez les mises à jour de valorisation du portefeuille, réalisées et non réalisées, selon un calendrier quotidien, hebdomadaire ou mensuel — et immédiatement avant tout flux de trésorerie externe — pour mettre à jour la NAV par part du pool.
5. **Traitez les retraits des investisseurs et les rachats de parts**
Saisissez les demandes de rachat partielles ou totales. Le moteur liquide le nombre de parts correspondant à la NAV courante, réduit le total des parts en circulation et recalcule les poids de détention post-rachat pour les associés restants.
6. **Auditez les relevés des comptes de capital et téléchargez le classeur Excel réutilisable**
Vérifiez l'intégrité des soldes via les indicateurs automatisés de contrôle d'erreurs et exportez des journaux de transactions propres pour le reporting LP ou la préparation fiscale. Une fois le flux de travail validé dans la démo web à session unique, **[téléchargez le modèle Excel complet et réutilisable de comptabilisation par unités et de comptabilité NAV de fonds](https://www.theseusworkshop.com/l/FundUnitizationDashboad?utm_source=github&utm_medium=GitHub%20README&utm_campaign=readme%20new%20launch&utm_content=fund-unitization-nav)** pour conserver des registres historiques permanents, personnaliser les tableaux de bord des associés et gérer les opérations continues du pool sur plusieurs années, hors ligne, dans Microsoft Excel.

*Avertissement : ce classeur est un modèle opérationnel de comptabilité et d'aide à la décision. Consultez un CPA qualifié ou un avocat spécialisé en fonds concernant les allocations fiscales de partenariat (par ex. IRC Section 704(b) / Schedule K-1) et la conformité aux valeurs mobilières dans votre juridiction.*

---

## Télécharger le modèle Excel complet

Prêt à automatiser la comptabilité de votre pool d'investissement et à tenir un registre permanent et auditable des associés ?

👉 **[Obtenir le classeur Excel complet de comptabilisation par unités et de comptabilité NAV de fonds (téléchargement gratuit)](https://www.theseusworkshop.com/l/FundUnitizationDashboad?utm_source=github&utm_medium=GitHub%20README&utm_campaign=readme%20new%20launch&utm_content=fund-unitization-nav)**

---

## Périmètre technique et limites opérationnelles

* **Dépendance à l'exactitude des données d'entrée :** l'exactitude de la NAV par part dépend de la saisie des valorisations de portefeuille au marché immédiatement avant l'enregistrement de tout nouveau dépôt ou retrait de capital.
* **Périmètre comptable opérationnel (ni conseil fiscal ni juridique) :** reflète la mathématique standard de comptabilisation par unités NAV pondérée dans le temps ; les allocations fiscales de partenariat spécifiques, les rapprochements comptabilité-fiscalité et les dépôts réglementaires exigent la validation d'un CPA agréé ou d'un conseil juridique.
* **Saisie manuelle des valorisations hors ligne :** conçu pour la confidentialité et l'absence de dépendances externes ; les valeurs de marché du portefeuille sont saisies manuellement plutôt que récupérées via des API de courtage en direct.
* **Périmètre standard des frais et flux de trésorerie :** couvre les souscriptions de capital, les rachats et le P&L de marché. Les cascades de carried interest GP/LP complexes, les taux obstacles, les frais de performance à high-water mark et les couvertures de change multi-devises sont hors du périmètre de cette version de base.
* **Échelle de pool recommandée :** optimisé pour les pools d'investissement de **3 à 20 participants** enregistrant des transactions hebdomadaires ou mensuelles.
* **Compatibilité système :** conçu pour **Microsoft Excel 2016 ou version ultérieure (Windows et macOS)** avec des formules natives standard et aucune dépendance de sécurité macro/VBA.
* **Dispositions structurelles particulières :** les allocations illiquides en side pocket, les calendriers d'expiration des périodes de blocage et les files d'attente de rachat contingentées exigent des ajustements de calendrier personnalisés hors de l'onglet central du registre.

---

## À propos de Theseus Workshop

Nous construisons des modèles Excel financiers et opérationnels transparents et prêts pour l'audit pour les petits fonds, les syndicats et les entreprises pilotées par des opérateurs qui ont besoin d'une logique comptable institutionnelle dans Microsoft Excel.

Chaque modèle fonctionne localement sur des formules de tableur natives, donnant à votre équipe une visibilité complète sur chaque cellule de calcul et chaque écriture du registre de détention.

Vous gérez dans des tableurs des flux de travail complexes d'allocation de capital, de rapprochement ou de suivi de détention ? **[Explorez notre bibliothèque complète de modèles Excel financiers et opérationnels chez Theseus Workshop →](https://www.theseusworkshop.com)**

---

## Licence

Distribué sous la [licence open source MIT](https://opensource.org/licenses/MIT).

