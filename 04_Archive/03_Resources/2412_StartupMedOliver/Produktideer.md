# Produktideer
## SmartCtrl
- To løsninger: Kontrol af forbrug og brugeradgange
- Godkend, afvis og tilføj bemærkninger
- Admin modul: 
	- overvåg status på kontrol 
	- overdrage ansvar til andre
- Påmindelsesmail 
- Kvitteringsmail når bruger færdig 
- Webapp: pc eller mobil, ingen installation påkrævet
- On-prem eller Cloud
- Prisstruktur: pr system, pr slutbruger, pr år. Ubegrænsede rapporter, ubegrænset data. 
## Projekter fra Gladsaxe Kommune
Projekter i perioden 2021-2024
* **Data Lineage**: overblik over afhængigheder mellem data, dashboards og ETL pipelines
	* Problem: stort, fragmenteret og ugennemskuelig datalandskab
	* Styrke: Inuitiv GUI, simpel funktionalitet og skræddersyet til Alteryx, Tableau og diverse datatyper
	* Alternativer: DataHub, OpenMetadata (Ingen Alteryx integration)
	* Framework: Alteryx og Tableau
	* Videreudvikling nemt at tilføje PowerBI integration
	* Generealiserbarhed: logik skal skrives om i f.eks. python
	* Markedspotentiale: virksomheder der bruger Alteryx, Tableau og PowerBI 
* **TOPdesk recommender**: automatisk match af vidensbase artikler på support sager ^f3ba9a
	* Problem: hyppig udskiftning af medarbejder, stort vidensdomæne
	* Styrke: lokal, hurtig og integreret i det eksisterende system
	* Alternativer: ??
	* Svaghed: afhænger af vidensbasens kvalitet, falske positiver
	* Framework: Python og Docker
	* Videreudvikling
	* Generealiserbarhed: klar
	* Markedspotentiale: virksomheder der bruger TOPdesk
* **Authorisationskontrol**: distribuerede kontrol af systemadgange og -rettigheder ^27c704
	* Problem: mange systemer, kedelig og tung og manuel bureaukratisk opgave
	* Alternativer: ??
	* Styrke: simpel UI, automatisk distribution, ensartede data på tværs af systemer
	* Framework: Alteryx, Tableau, SQL, Grafdata-algoritmer
	* Generealiserbarhed: Skal bygges om i open-source 
	* Markedspotentiale: Måske alle kommuner
* **Underretninger i fokus** : opslagsværktøj til info om børn ifm. underretninger
	* Problem: flere systemer og datakilder, følsom data
	* Styrke: simpel, følsom og hurtig
	* Framework: Alteryx, Tableau, Python, SQL
	* Generealiserbarhed: Skal  bygges om i open-source 
	* Markedspotentiale: andre kommuner der bruger [SBSYS](https://sbsys.dk/)
* **Smarte Anvisningsrapporter**: værktøj til stikprøvekontrol af transaktioner ^14a07c
	* Problem: gummistempel, pdf filer, for meget data, kedelig bureaukratisk opgave
	* Alternativer: 
	* Framework: Alteryx, Tableau, Python, SQL
	* Videreudvikling: anomaly detection
	* Generealiserbarhed: Skal  bygges om i open-source 
	* Markedspotentiale: [ØSIndsigt](https://oesindsigt.rn.dk/) bruges af mange kommuner og regioner
* **MinGPT - Specialiserede chatbots builder**:   designer/builder af GPT baserede chatbots med adgang til viden fra uploadede dokumenter.
	* Problem: Behov for at udforske store sprogmodeller (GPT) som teknologi på specifikke domænder
	* Styrke: intuitiv no-code gui, kompatibel med Azure OpenAi og lokale open source modeller.
	* Framework: Python
	* Svaghed: umodent, kun lidt testet og ikke færdig udviklet
	* Alternativer: Applai, PrivateGPT, MS Coplito Studio? ... 

## Konkurrencemuligheder
Alle kommuner skal fornye deres kontrakter og indhente mindst tre tilbud
* [GR-1 GDPR Scan](https://gr-1.dk/)
	* Videreudvikling Færre falske positiver, andet end CPR numre
* [Automatisk kontering ved brug af kunstig intelligens - Kaunt](https://gov.kaunt.com/da/)
* [Subit](https://subit.dk/)

## Andre ideer
* **Anonymiseringsassistent**:  word og outlook plugin der annoterer persondata i tekst. 