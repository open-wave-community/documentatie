# Zaakportaal Bouw/Sloop

AanroepAction: OpenTabPage(#bouwsloop/x) waarbij x = primary key uit tbbouwvergunningen.

Schermtype portal.

## Problemen

1. Het scherm ziet er raar uit (al of niet met foutmelding) of reageert niet:

- de variabele x uit de aanroep verwijst niet naar een bestaande tbbouwvergunningen.dnkey
- inlogger heeft geen kijkrechten voor Bouw/Sloop zaken (zie rechten: de inlogger behoort tot een rechtengroep waarbij _Bouw/Sloop zaken Zichtbaar_ niet is aangevinkt)
- de variabele x uit de aanroep verwijst naar een zaak van een gemeente waarvoor de inlogger geen kijkrechten rechten (zie instelling medewerker: alleen gemeentes en/of medewerker is lid van compartiment en de locatie van de zaak valt niet onder de aan het compartiment toegekende gemeentes)
- alle tegels zijn disabled of onzichtbaar op conditie (zie [Portaldefinitie](../../instellen_inrichten/portaldefinitie/README.md))
- geen enkele tegel uit dit portal is toegekend aan inlogger.

2. Medewerker a ziet meer of minder tegels dan medewerker b:

kan alleen indien aan medewerkers a andere tegels zijn toegekend dan aan medewerker b.

## Triggers

Welke knop/triggers rechtsboven?

### Externe link

Knop is zichtbaar en enabled indien:

- voor niet-compartimentszaken kolom _Logic_ van de instelling _Sectie: ExterneLink_ en _Item: BouwSloop_ aangevinkt is
  - voor compartimentszaken veld _Externe link naar DMS (portaalknop Externe link kijkt naar deze instelling)_ bij het desbetreffende compartiment in het beheerportaal-Nieuw gevuld is
  - en het Handhavingszaakrecht _starten van hyperlink vanuit portaal_ aangevinkt is bij de rechtengroep van de inlogger. Van de kolom _Tekst_ van bovengenoemde instelling wordt een hyperlink gemaakt, waarbij de variabelen in die Tekst:
    - `%zaakjaar%` met het jaar van startdatum van de handhavingszaak wordt vervangen: YYYY
    - `%zaakjaar%` met jaar en maand van startdatum wordt vervangen: YYYYMM
    - `%zaaknr%` met de OpenWave Zaakcode (dvaanschrijfnr) van de bouwsloopzaak
    - `%dmsnr%` met externe zaak/dms nummer (dvintzaakcode) van de bouwsloopzaak (indien aangevinkt is dat het DMS E-Suite is dan wordt de benodigde vertaalslag op deze tag uitgevoerd)
    - `%postcode%` met postcode van locatie adres
    - `%huisnummer%` met huisnummer van locatie adres.

### Docs

- Indien de instelling _Sectie: Documenten Item: Documentregistratie_ is aangevinkt, dan wordt direct de lijst met [geregistreerde documenten](/probleemoplossing/module_overstijgende_schermen/geregistreerde_documenten/README.md) geopend (op basis van tbcorrespondentie). De knop is in dit geval zichtbaar en enabled indien de gebruiker het recht _Inzien geregistreerde documenten (tbrechten.dlcbwvcorregvsb)_ heeft
  - anders, (deze instelling staat uit) dan wordt de (live-)lijst van opgeslagen documenten bij de zaak geopend: zie [Toon documenten en download](../programmablokken/toon_documenten_en_download.md). De knop is in dit geval zichtbaar en enabled indien de gebruiker het recht _Inzien documenten buiten registratie om (dlcbwvcorvsb)_ heeft.

### Kaart

Knop is altijd zichtbaar en enabled. Afhankelijk van het al of niet ingevuld zijn van de kolom _Info_ van de instelling _Sectie: Programma Item: ToonKaart_ wordt met deze knop een externe kaart geopend (conform de URL in die kolom info, waarbij %x% en %y% vervangen worden door de locatiecoördinaten en %zoom% door _Getal2_), of een interne kaart van OpenWave. Zie:[Kaart](/probleemoplossing/module_overstijgende_schermen/kaart.md).

### Memo

Knop is altijd zichtbaar en enabled maar indrukken kan leiden tot melding onvoldoende rechten (rechten _Bouw/Sloop Memo wijzigen_).

### Locatie

Knop is altijd zichtbaar en enabled, maar indrukken kan leiden tot melding onvoldoende rechten (hoofdscherm rechten: locatie adressen zichtbaar).

- _Detailscherm Bouw/Sloop_

Knop is altijd zichtbaar en enabled.

### Overige triggers

Klikken op tegel opent een vervolgscherm. Indien niet klikbaar dan is de tegel ingesteld als disabled (zie [Portaldefinitie](../../instellen_inrichten/portaldefinitie/README.md))

## Gerelateerde pagina's

- [Detailscherm Bouw/Sloop zaak](/probleemoplossing/portalen_en_moduleschermen/zaakportaal_bouw_sloop/detailscherm_bouw_sloop.md)
- [Tegel Afgehandelde Adviezen](/probleemoplossing/portalen_en_moduleschermen/zaakportaal_bouw_sloop/tegel_afgehandelde_adviezen.md)
- [Tegel Afgehandelde Processtappen](/probleemoplossing/portalen_en_moduleschermen/zaakportaal_bouw_sloop/tegel_afgehandelde_stappen.md)
- [Tegel Afgesloten Inspectiebezoeken](/probleemoplossing/portalen_en_moduleschermen/zaakportaal_bouw_sloop/tegel_afgesloten_inspectiebezoeken.md)
- [Tegel Afgeronde Inspectietrajecten](/probleemoplossing/portalen_en_moduleschermen/zaakportaal_bouw_sloop/tegel_afgesloten_inspectietrajecten.md)
- [Tegel Afgeronde Overtredingen](/probleemoplossing/portalen_en_moduleschermen/zaakportaal_bouw_sloop/tegel_afgesloten_issues.md)
- [Tegel Afgeronde zaken op dit adres](/probleemoplossing/portalen_en_moduleschermen/zaakportaal_bouw_sloop/tegel_afgesloten_zaken_op_dit_adres.md)
- [Tegel Alle Processtappen](/probleemoplossing/portalen_en_moduleschermen/zaakportaal_bouw_sloop/tegel_alle_stappen.md)
- [Tegel Contactadressen](/probleemoplossing/portalen_en_moduleschermen/zaakportaal_bouw_sloop/tegel_contactadressen.md)
- [Tegel Dossierbehandelaars](/probleemoplossing/portalen_en_moduleschermen/zaakportaal_bouw_sloop/tegel_dossierbehandelaars.md)
- [Tegel Gebouwen](/probleemoplossing/portalen_en_moduleschermen/zaakportaal_bouw_sloop/tegel_gebouwen.md)
- [Tegel Gekoppeld aan inrichting](/probleemoplossing/portalen_en_moduleschermen/zaakportaal_bouw_sloop/tegel_gekoppeld_aan_inrichting.md)
- [Tegel Geregistreerde Documenten](/probleemoplossing/portalen_en_moduleschermen/zaakportaal_bouw_sloop/tegel_geregistreerde_documenten.md)
- [Tegel Installaties](/probleemoplossing/portalen_en_moduleschermen/zaakportaal_bouw_sloop/tegel_installaties.md)
- [Tegel Leges](/probleemoplossing/portalen_en_moduleschermen/zaakportaal_bouw_sloop/tegel_leges.md)
- [Tegel Lopende Inspectietrajecten](/probleemoplossing/portalen_en_moduleschermen/zaakportaal_bouw_sloop/tegel_lopende_inspectietrajecten.md)
- [Tegel Lopende zaken op dit adres](/probleemoplossing/portalen_en_moduleschermen/zaakportaal_bouw_sloop/tegel_lopende_zaken_op_dit_adres.md)
- [Tegel Openstaande Adviezen](/probleemoplossing/portalen_en_moduleschermen/zaakportaal_bouw_sloop/tegel_openstaande_adviezen.md)
- [Tegel Openstaande Inspectiebezoeken](/probleemoplossing/portalen_en_moduleschermen/zaakportaal_bouw_sloop/tegel_openstaande_inspectiebezoeken.md)
- [Tegel Openstaande Overtredingen](/probleemoplossing/portalen_en_moduleschermen/zaakportaal_bouw_sloop/tegel_openstaande_issues.md)
- [Tegel Openstaande processtappen](/probleemoplossing/portalen_en_moduleschermen/zaakportaal_bouw_sloop/tegel_openstaande_stappen.md)
- [Tegel Preparaties](/probleemoplossing/portalen_en_moduleschermen/zaakportaal_bouw_sloop/tegel_preparaties.md)
- [Tegel Status](/probleemoplossing/portalen_en_moduleschermen/zaakportaal_bouw_sloop/tegel_status.md)
- [Tegel Verbonden aan Groep](/probleemoplossing/portalen_en_moduleschermen/zaakportaal_bouw_sloop/tegel_verbonden_aan_groep.md)
