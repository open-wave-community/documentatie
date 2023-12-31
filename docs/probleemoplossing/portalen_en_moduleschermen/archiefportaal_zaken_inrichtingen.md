# Archiefportaal zaken/inrichtingen

## LET OP: DEPRECATED

Ga terug naar [Portalen en Moduleschermen](/probleemoplossing/portalen_en_moduleschermen/README.md)

## Alternatief: de tegels op het openingsportaal

- **Alle locaties**
- **Alle Zaken**
- **Alle Inrichtingen**

AanroepAction: OpenTabPage(#zi)

Op het portal is een lijst te zien van alle zaken of inrichtingen van één straat.

- Alle zaken van één straat:

  - API geefZakenOverzicht. Zie [https://api.open-wave.nl/RemMethods/getRemMethod/100](https://api.open-wave.nl/RemMethods/getRemMethod/100.md)
  - screenidentifier voor tab zaken: MDLC_geefZakenOverzicht.xml
  - de data komen uit vwfrmalleaanvragen gefilterd op de gekozen straat waarbij:
    - de eerste kolom wordt gevuld met een stop/blokkeericoontje indien de betreffende zaak is geblokkeerd
    - de tweede kolom wordt gevuld met het ketenicoontje indien de zaak is verbonden met een of meer andere zaken in een groep (zie tegel verbonden aan groep op het zaakportaal van de zaak
    - de derde kolom wordt gevuld met het monumenticoontje indien het locatieadres van de zaak aangeduid is als een monument
    - de zevende kolom wordt gevuld met een soort-zaak-icoontje. Per zaaktype kan deze worden gekozen in dropdownlijstje icoon (beheertegels _Zaaktypes omgeving, APV/overig/ bouw/sloop/ handhaving/ milieu/gebruik_). De zaaktypes bij bouw/sloop hebben allemaal dezelfde icoon (fabriek). Zo ook die van InfoAaanvragen (een _I_) en zo ook die van horeca (een bierpul)
    - de twaalfde kolom wordt gevuld met een weegschaal-icoontje. Indien de instelling _Sectie: Programma Item: BezwaarberoepDesktop_ bestaat en is aangevinkt kijkt het programma of één van de kolommen ddindieningbezwaar of ddrbindieningberoep is gevuld (omgeving, handhaving en APV/overig). Bestaat de instelling niet of indien deze niet is aangevinkt dan kijkt het programma naar de tabel tbbezwaarberoep: indien aan de zaak een of meer bezwaar/beroep kaarten zijn verbonden wordt het icoontje getoond.

- Alle inrichtingen van één straat:
  - API geefInrichtigenoverzicht. Zie [https://api.open-wave.nl/RemMethods/getRemMethod/105](https://api.open-wave.nl/RemMethods/getRemMethod/105.md)
  - screenidentifier voor tab inrichtingen: geen (hard gecodeerd)
  - de data komen uit vwfrmmilinrichtingen gefilterd op de gekozen straat waarbij:
    - de eerste kolom wordt gevuld met een stop/blokkeericoontje indien de betreffende inrichting is geblokkeerd
    - de tweede kolom wordt gevuld met het ketenicoontje indien de inrichting verbonden is aan een moeder-inrichting
    - de derde kolom wordt gevuld met het monumenticoontje indien het locatieadres van de inrichting aangeduid is als een monument.

## Problemen

1. Het scherm ziet er raar uit (al of niet met foutmelding) of reageert niet:

- de inlogger is niet toegekend aan rechtengroep
- de inlogger is ingedeeld bij een rechtengroep en heeft geen enkel vinkje bij de modules (kijkrechten:).

2. De lijst is leeg of geeft maar een gedeelte van alle zaken of inrichtingen:

- de inlogger heeft kijkrechten op beperkt soorten zaken
- op de medewerkerskaart van de inlogger staat dat hij/zij alleen gegevens kan zien van bepaalde gemeentes
- de medewerker is lid van een compartiment en ziet daarom alleen zaken/inrichtingen die gelokaliseerd zijn op de aan het compartiment toegekende gemeentes.

## Triggers

Welke zijn linksonder zichtbaar?

- _Toon Kaart_ zichtbaar en enabled behalve bij een lege lijst
- _Locatieadres_ zichtbaar en enabled behalve bij een lege lijst
- _Detailgegevens_ zichtbaar en enabled behalve bij een lege lijst
- _Memo zichtbaar_ en enabled behalve bij een lege lijst
- _Naar Verzamelscherm (zaakportaal)_ zichtbaar en enabled behalve bij een lege lijst
- _insert knop op tabblad Zaken_ is zichtbaar en enabled indien inlogger op tenminste een soort zaak insertrechten heeft
- _insert knop op tabblad Inrichtingen_ is zichtbaar en enabled indien inlogger op de inrichtingen insertrechten heeft
- _samenvoeg knop op tabblad Inrichtingen_ is zichtbaar en enabled indien inlogger op de inrichtingen het samenvoegrecht (tbmilrechten.dlbmilinrsamen) heeft
- _delete knop op tabblad Zaken_ is zichtbaar en enabled indien inlogger op tenminste een soort zaak deleterechten heeft en is disabled indien lege lijst
- _delete knop op tabblad Inrichtingen_ is zichtbaar en enabled indien inlogger op inrichtingen deleterechten heeft en is disabled indien lege lijst.

**Welke knop/triggers rechtsboven**:

- _Filter_: altijd zichtbaar en altijd enabled (zie hieronder voor aanpasbare default filterinstellingen)
- _Wijzig straat_: altijd zichtbaar en altijd enabled. Indien de inlogger lid is van een compartiment kan alleen gekozen worden uit de gemeentes die toegekend zijn in dat compartiment. Het programma kijkt daarbij ook nog naar de reeks gemeente-id's op het detailscherm van de medewerker op het beheerportaal-Nieuw (alleen data van gemeentes …).

**Welke knop/triggers rechtsonder?**

- _Zoeken_: altijd zichtbaar en enabled.

**Overige triggers**:

- Klikken op de regel opent een zaakportaal (omgeving APV/Overig, handhaving, inrichting, milieu/gebruik, bouw/sloop) of een detailvenster oude stijl (info, horeca).

## Filterinstelingen

- **datumschuif**. Bij de zaakpagina (tabblad _Zaken_) kan een domein opgegeven worden op basis van aanvraag/startdatum. Dat gebeurt door een datumschuif te verplaatsen. Default staat de datumschuif op de systeemdatum minus 5 jaar: dat wil zeggen dat de zaken zichtbaar zijn vanaf 5 jaar geleden. Die datumschuif is te verplaatsen aan de rechterkant tot 1 jaar terug en aan de linkerkant conform de instelling van _Getal1_ bij _Sectie OWB_ en _Item: DatumFilterSchuifVanaf_. Hier moet een jaartal ingevoerd worden. Bestaat deze instelling niet dan neemt het programma 1998 als defaultwaarde.

Indien ook het aanvinkvakje va deze deze instelling wordt gevuld dan zal het programma de linkerkant van de datumschuif default op dit jaartal zetten: dus dan wordt gestart met alle zaken vanaf dat jaartal

Veranderingen worden pas geeffectueerd na het opnieuw inloggen.

- **Geblokkeerde kaarten zichtbaar**. Het programma kijkt wat betreft tabblad _Inrichtingen_ naar de instelling _Sectie: OWB en Item: zi_inrichtingen_geblokkeerde_zichtbaar_ en bij tabblad _Zaken_ naar de instelling _Sectie: OWB en Item: zi_zaken_geblokkeerde_zichtbaar_. Indien aangevinkt of indien deze instelling(en) ontbreekt, dan zijn de geblokkeerde rijen zichtbaar (in filtermenu staat geblokkeerd aangevinkt). Indien instellingen bestaat maar niet aangevinkt, dan zijn de geblokkeerde rijen niet zichtbaar (in filtermenu staat geblokkeerd niet aangevinkt). Veranderingen worden pas geeffectueerd na het opnieuw inloggen.
