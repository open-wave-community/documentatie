# Lijst Openstaande InfoAanvragen

Schermidentifier: MDLC_getOpenInfoAanvragenList.xml.

## Welke gegevens worden getoond

De rijen uit de view vwfrminfoaanvragen, dat zijn alle infoaanvragen uit de tabel tbinfoaanvragen.
De API legt daar de volgende restrictie overheen:

- de datum afgehandeld is leeg
- de blokkeerdatum is leeg
- indien de kolom _alleen gemeentes_ (zie beheertegel _Medewerkers_) bij de kaart van de inlogger gevuld is, dan worden alleen die infoaanvragen getoond waarvan de id van de locatie-gemeente (bedoeld wordt de locatie waaraan de bovenliggende zaak of inrichting is verbonden) voorkomt in die kolom _alleen gemeentes_
- compartimentsrestricties. Zie hiertoe de uitleg bij de tegel waarvan deze lijst wordt aangeroepen.

### Zichtbaarheid bepaalde kolommen

- kolom **Beh.ins** (dvcompartimentsnaam) is alleen zichtbaar indien er tenminste één compartiment is gedefinieerd (beheertegel _Compartimentsrechten_)
- kolom **Team** (dvteamnaamzaakverantw) is alleen zichtbaar indien _Getal1_ van de instelling _Sectie: Zaakverantwoordelijke en Item = InfoAanvraag_ de waarde 2 of 3 heeft
- de kolommen **CT Uit** (dnaantalctuitstaand) en **CT Ret** (dnaantalctretour) en **CT Gez** (dnaantalctgezien) zijn alleen zichtbaar indien de instelling _Sectie: Programma_ en _Item: InfAantCollegToetsZichtbaar_ aangevinkt is.

Dnaantalctuitstaand met het aantal uitstaande (dus nog niet geretourneerde) collegiale toetsen bij de zaak.

Dnaantalctretour met het aantal geretourneerde collegiale toetsen bij de zaak. Dnaantalctgezien met het aantal geretourneerde + geziene collegiale toetsen bij de zaak.

## Problemen

- De lijst is leeg of geeft maar een gedeelte van de open infoaanvragen:
  - de inlogger heeft geen kijkrechten op infoaanvragen
  - op de medewerkerskaart van de inlogger staat dat hij/zij alleen gegevens kan zien van bepaalde gemeentes
  - de inlogger is lid van een compartiment.
- De lijst geeft foutmelding:
  - er is mogelijk een zelf gedefinieerde schermindeling gebruikt (Schermkolomdefinitie onder Beheer) die niet valide is.

## Triggers

Welke zijn van toepassing op deze lijst?

- zoekeditbox rechtsonder: altijd aanwezig
- pagingknoppen rechtsboven: aanwezig indien aantal rijen groter dan de instelling _Getal1_ bij _Sectie: Paging_ en _Item: pagesize_ (defaultwaarde = 100)
- klikken op regel opent altijd bijbehorend zaakportaal infoaanvraag
- versie-informatie rechtsonder (hierop klikken en screensource = tbscreencolumns geeft aan of er een afwijkende schermkolommen definitie gebruikt wordt).

## Betekenis kleurenballetjes

- Eerste kolom (dvzaakgevaar):
  - leeg indien de fatale datum leeg is
  - rood indien datum_van_vandaag > fatale datum
  - oranje indien vandaag < = fatale datum < = datum_van_vandaag + 2 (overmorgen)
  - wit in alle andere gevallen.
- Kolom Proces (dvprocesgevaar):
  \*leeg indien geen proces gedefinieerd bij zaak
  - groen indien er geen openstaande processtappen zijn
    \*rood indien er tenminste één openstaande processtap is met een streefdatum < = datum_van_vandaag
  - oranje indien er tenminste één openstaande processtap is met vandaag < streefdatum < = datum_van_vandaag + 2 (overmorgen)
  - wit in alle andere gevallen.
- Kolom Advies (dvadviesgevaar):
  \*leeg indien geen advies gedefinieerd bij zaak
  - groen indien er geen openstaande adviezen zijn
    \*rood indien er tenminste één openstaand advies is met een rappeldatum < = datum_van_vandaag
  - oranje indien er tenminste één openstaande advies is met vandaag < rappeldatum < = datum_van_vandaag + 2 (overmorgen)
  - wit in alle andere gevallen.

Het is mogelijk om de kleurenballetjes te veranderen in gekleurde iconen, zie hiervoor [Sectie OWB](../../../../instellen_inrichten/configuratie/sectie_owb.md).
