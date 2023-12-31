# OLO/DSO/AIM Bijlage verwijzingen

De schermidentifiers voor lijst en detail zijn: MDLC_geefOloBerichtenOverzicht.xml en MDDC_geefOloBerichtDetail.xml.

Dit (lijst) scherm kan worden aangeroepen vanuit:

- het milieu/gebruikportaal (tegel _OLO/AIM-bijlagen_)
- het omgevingsportaal (tegel _OLO/DSO/AIM-bijlagen_)
- vanuit een DSO-specificatie (onder een activiteit/onderdeel bij een omgevingzaak)

De bron van de lijst is de view vwfrmoloberichten (op basis van de tabel tbomgoloberichten) die gevuld wordt bij het automatisch verwerken van OLO/DSO/AIM-berichten, zie
[Verwerking van StuF OLO / AIM berichten](../programmablokken/olo_verwerking.md).

- De lijst toont een verwijzing naar de documenten die de aanvrager, conform de aanvraag/verzoek of een wijziging/aanvulling daarop, zou moeten aanleveren in het OLO-loket of DSO-loket of AIM-loket.
- De lijst is zichtbaar indien de inlogger lid is van een rechtengroep die bij de betreffende module (omgeving of milieu/gebruik) het kijkrecht heeft op Nagekomen Berichten.

## Bijzondere Kolommen

Het gevuld zijn van de kolom **datum gezien** is van invloed op het kleurenbolletje onder kolom _OLO_ in de doorkieslijsten openstaande omgevingszaken/ milieu/gebruikszaken van het openingsportaal.

In de lijst is een kolom ingevoegd **In reg (in registratie)**. Deze kolom is zichtbaar indien de instelling _Sectie: DocumentRegistreren en Item: AlleOLODSOUploads_ aangevinkt is.

Deze kolom **InReg** is aangevinkt indien het document zich bevind in de geregistreerde documenten.

Indien de kolom **DSO volgnummer** is gevuld betekent dat, dat de betreffende bijlage met een DSO-aanvulling (die van het volgnummer) is toegevoegd.

Indien de kolom **DSO vervaldatum** is gevuld betekent dat, dat het document bij een DSO-aanvullingsbericht niet meer is genoemd. Bij afspraak geldt dat het document, dat eerder wel in het initiërend bericht was opgenomen, daarmee is komen te vervallen. De vervaldatum is de datum dat het aanvullingsbericht wordt verwerkt. Indien het vervallen document is opgenomen in de geregistreerde documenten (tbcorrespondentie), dan krijgt deze ook dezelfde vervaldatum.

De kolom **omschrijving** wordt bij het inlezen van DSO-documenten gevuld met de documentsoort uit de gevraagde bijlages.

### Probleem

Het scherm geeft een foutmelding indien er is mogelijk een zelf gedefinieerde schermindeling gebruikt (zie [Scherm(kolom)definitie](../../instellen_inrichten/schermdefinitie/README.md)) die niet valide is.

### Muteren

De inlogger kan geen nieuwe rijen aanmaken in deze tabel. Dat gebeurt automatisch door de service die de OLO-berichten verwerkt.

Indien de inlogger lid is van een rechtengroep die bij de betreffende module (omgeving of milieu/gebruik) het wijzigrecht heeft op Nagekomen Berichten, dan kan deze een rij voorzien van een datum _(datum gezien_) die de betekenis heeft: op deze datum heb ik de bijlage daadwerkelijk gezien. De kolom _gezien door_ wordt dan automatisch gevuld met de medewerkerscode van de inlogger.
Met de knop _accorderen_ linksonder kunnen in één keer alle lege datums worden gevuld.

### Haal ontbrekende documenten

De knop Haal ontbrekende documenten (downloadknop) start een wizard (als runnable) waarbij er eerst wordt gekeken of het om een DSO of OLO zaak gaat: is er voor de zaak een gevulde dnkeydsoproject dan gaat het om een DSO zaak, anders om een OLO zaak.

Indien het om een OLO zaak gaat dan worden de ontbrekende documenten rechtstreeks van de OLO FTP-site gehaald, indien het om een DSO zaak gaat dan worden de ontbrekende documenten bij het DSO opgehaald via de DSO verzoek API.

De opgehaalde documenten worden vervolgens opgeslagen op de fileshare dan wel in het DMS en vervolgens worden evenzoveel rijen aangemaakt in geregistreerde documenten. Om dubbelen te voorkomen wordt na het starten van de runnable een vlag gezet: _Getal1_ van de instelling _Sectie: Operation en Item: OphalenOntbrekendeOLODocumenten_ krijgt de waarde 1. Deze wordt weer op null gezet als de runnable klaar is.

De berichten worden gelogd indien de instelling: _Sectie: OWB, item: MessageLog_ en de instelling _Sectie Koppeling OLO en Item: FTP-messagelog_ beiden zijn aangevinkt.

Voor een **DSO-zaak** gelden de volgende voorwaarden:

- De OIN van de zender moet bekend zijn: deze wordt eerst opgezocht op basis van uitvoerende instantie: indien deze gevuld wordt de kolom _Tekst_ van de instelling _Sectie: SWF en Item: OINvanZender_ gebruikt. Anders, indien behandeldienst leeg en bevoegd gezag wel gevuld, dan wordt het OIN-nummer uit TbOin van het bevoegd gezag gebruikt. Anders, indien bevoegd gezag en behandeldienst leeg zijn dan wordt het OIN van de zender ook uit TbOin gehaald, maar dan op grond van de gemeente waar de zaak speelt.
- VarAlgemeenEndpoint moet gedefinieerd zijn in kolom _Tekst_ van _Sectie: DSO-Verzoekafhandelen en Item: AlgemeenEndpoint_.

Voor een **OLO-zaak** gelden de volgende voorwaarden

- op grond van de gemeente waar de zaak speelt wordt in tb33gemeente opgehaald (beheerportaal-Nieuw, kolom Administratie, tegel _Gemeentes_)
  - Endpoint = dvoloftpendoint
  - loginnaam = dvoloftplogin
  - password = dvoloftppass (LET OP deze kan gecrypt zijn opgeslagen)
  - poort = dvoloftpoort

Indien endpoint leeg is (dus niet gedefinieerd in tb33 gemeente) dan valt OpenWave terug op algemene instelling

- Sectie: koppeling OLO
  - Item: FTPS-site
  - Tekst: loginpassword
  - Info: loginnnaam
  - Getal1: poort
  - Info2: endpoint

### Triggers Linksonder in lijst

- **Accorderen**:
  - zichtbaar en enabled indien:
    - de inlogger bovengenoemde wijzigrechten heeft
    - en compartiment OK.
- **Refresh**:
  - zichtbaar en enabled indien:
    - de de instelling _Sectie: DocumentRegistreren en Item: AlleOLODSOUploads_ aangevinkt is.
- **Haal ontbrekende documenten** (downloadknop) waarmee OLO/DSO-bijlagen van de lijst worden vergeleken met de geregistreerde documenten in tbcorrespondentie (zie hierboven).
  - zichtbaar en enabled indien:
    - de inlogger wijzigrechten heeft
    - en indien
      _de omgevingzaak een compartimentszaak is, dan moet bij het betreffende compartiment in het beheerportaal de eigenschap tbcompartiment.dldocregalleolodsouploads aangevinkt staan
      _ anders, geen compartiment, dan moet de instelling automatische registratie in tbcorrespondentie van de binnenkomende OLO/DSO-documenten aangevinkt staat: _Sectie: DocumentRegistreren en Item: AlleOLODSOUploads_
