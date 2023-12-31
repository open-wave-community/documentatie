# Detailscherm Geregistreerd Document

De schermidentifier is: MDDC_getGeregistreerdeDocumentenDetail.xml.

Zie voor verzendstroom, collegiale toetsing, bijlages, cc's, ondertekening: [Documenten/Verzendstroom](../programmablokken/documenten_verzendstroom.md).

Dit scherm kan worden aangeroepen vanuit de lijst _Geregistreerde documenten_ bij een zaak.

## Error

Het scherm geeft een foutmelding, indien:

- er mogelijk een zelf gedefinieerde schermindeling gebruikt is die niet valide is
- de inlogger geen kijkrechten heeft op de adviezen bij betreffende hoofdzaak.

### Muteerbaarheid kolommen

In zijn algemeenheid geldt voor de blokken **adressering** en **status** dat de kolommen hierin alleen muteerbaar zijn indien de verstuurddatum (tbcorrespondentie.ddbriefdatum) nog leeg is. Voor de kolom _Verstuurd_ zelf geldt dit dan weer niet. Deze kolom blijft muteerbaar indien de ingelogde medewerker:

- een beheerniveau > 98 heeft (tbmedewerkers.dnbeheerniveau) of
- het recht _Mag digitaal ondertekenen_ heeft (tbmedewerkers.dlmagdigondertekenen)

Zie verder bij [Documenten/Verzendstroom](../programmablokken/documenten_verzendstroom.md) en kopje _Aantekenen_ hieronder.

Bij het blok **meta** is de _Vereiste Vertrouwelijkheid_ enkel muteerbaar indien de inlogger hetzelfde of een hoger vertrouwelijkheidsniveau toegekend heeft gekregen in de medewerkerskaart. De _DSO Vertrouwelijkheid_ (DSO vert.) is net als het _Niveau_ niet muteerbaar.

### Blok Document

Voor de kolom **omschrijving/titel** (dvomschrijving) geldt het volgende:

- wordt bij synchronisatie vanuit stuf zaak/DMS overschreven met titel
- wordt bij opslaan OLO/DSO documenten initieel gevuld met OLO/DSO-omschrijving
- wordt bij registreren van documenten afkomstig uit Stuf zaak/DMS ook gevuld met de titel, mits de opgegeven omschrijving leeg is (of niet van toepassing).

De kolom **mByte** (dfdocgrootte) wordt bij registratie van een document gevuld met het aantal Megabytes (in zoverre mogelijk). Van documenten in het DMS kan via stuf zaak/DMS niet achterhaald worden wat de actuele grootte is. Verder geldt dat documenten op een fileshare van buitenaf gewijzigd kunnen zijn, zonder dat OpenWave hier weet van heeft.

De vwfrmcorrespondentie.dvfilenaam wordt bij OLO-documenten berekend op grond van de tbcorrespondentie.dvdocfilenaam (de echte documentnaam en bij opslag op fileserver voorafgegaan door het volledige pad), door slechts het gedeelte vanaf de laatste slash c.q. backslash te laten zien. Dus de echte documentnaam is bijvoorbeeld _mijnservernaam/2023/2023W0034/OLO/8103577/basisset_aanvraag/8103577_1696421488416_publiceerbareaanvraag.pdf_, maar de gebruiker ziet: _8103577_1696421488416_publiceerbareaanvraag.pdf_

Bij opslag in DSM (stuf Zaak/DMS) bestaat tbcorrespondentie.dvdocfilenaam uit enkel de bestandsnaam. Vwfrmcorrespondentie.dvfilenaam en tbcorrespondentie.dvdocfilenaam zijn dan identiek.

De kolom **(O)LO (D)SO (S)WF** (dvuitolodsoswf) wordt automatisch gevuld bij het plaatsen van documenten uit SWF of OLO of DSO.

Indien deze kolom is gevuld met een _D_ (DSO) dan wordt de bestandsnaam (dvdocfilenaam) vanaf de laatste hyphen c.q. slash opgezocht in tbomgoloberichten en - indien gevonden - worden van daaruit de **specificatievraag en activiteit** erbij gehaald in de kolommen vwfrmcorrespondentie.dvdsovraag en dvdsoactiviteit.

### Blok Adressering

De hoofdgeadresseerde kan alleen worden gekozen tijdens het aanmaken van een document op basis van een sjabloon: in alle gevallen Ã©Ã©n van de contactpersonen bij de bovenliggende zaak. De achterliggende adresgegevens kunnen wel via het knopje contactadreskaart worden aangepast (zie bij [Contactadres](contact_adres.md) in welk scherm op grond van recht). Uitzondering hierop (dus wel aan te wijzen) is wanneer

- de instelling _Sectie: DocumentRegistreren en Item: ContactWijzigbaar_ aangevinkt is
- en de brief nog niet verstuurd is
- en - indien richting is uitgaand - de status nog niet definitief is.

Post of per mail: zie hieronder bij kopje _Verzendwijze_.

### Blok Aangetekend

Indien de verzendwijze staat op _Per Post_ (dlmoetperpost = 'T') en de richting = (U)itgaand dan is het blok _Aangetekend_ zichtbaar.

Zolang de verzenddatum (ddbriefdatum) nog leeg is, kan het vakje _Aangetekend_ (dlaangetekend) aan- of uitgevinkt worden. Bij het creÃ«ren van een brief op basis van een sjabloon kan aldaar deze status al worden toegekend. Indien verzendwijze of richting wordt veranderd zal het vinkje worden leeggemaakt.

De kolom **externe Track- en tracecode** (dvexttracktrace) is alleen muteerbaar indien:

- dlaangetekend is Aangevinkt
- en de verzenddatum (ddbriefdatum) is gevuld
- en indien de inlogger voor de betreffende module geautoriseerd is om deze kolom te vullen. Zie beheertegel _Functionele rechten_ bijvoorbeeld bij omgevingszaken het recht in blok documenten: _Wijzigrecht externe track- en trace code geregistreerd document (dlcomgcorregtent)_.

Op het moment dat deze track- en trace code wordt gewijzigd zal automatisch de muteerder en datum/tijdstip van de wijziging worden toegekend (dvcodemutexttracktrace en ddexttracktrace).

### Blok URL

In de kolom URL kan een externe link staan (die met de achterliggende _open url_-knop wordt benaderd, mits de URL begint met _http_ of // of \).

Deze link kan automatisch worden gevuld bij registratie van een document dat succesvol **in het DMS** wordt opgeslagen op grond van de kolom _Tekst_ van de instelling _Sectie: koppelingDOCNaarDMS_ en _Item: ExterneDocLink_ en waarbij _Getal1_ van die instelling de waarde 1 heeft.

Een compartiment heeft hiertoe eigen instellingen in de kolommen dvexternedoclink en dlextlinkautovul.

Bij de registratie worden de substrings %dmszaakcode% en %dmsdoccode% door OpenWave vervangen door hun echte waarde bij het betreffende document.

> [!NOTE]
> De ExterneDocLink `https://corsa-as1-a/Corsa/web/index.html#search/q=%dmsdoccode%` zal bij registratie van een document met documentidentifier Rommeldam20230918113151515 opgeslagen worden in de kolom dvurl als `https://corsa-as1-a/Corsa/web/index.html#search/q=Rommeldam20230918113151515>`

Indien wenselijk kan de hyperlink ook via het lijstscherm van de geregistreerde documenten worden gestart. Zie daartoe kopje Triggers in lijstscherm: _schermknop hyperlink op grond van gevulde dvurl_ van [Lijst Geregistreerde Documenten bij een zaak](geregistreerde_documenten/lijst_geregistreerde_documenten_bij_zaak.md)

### Blok Bodem

De beheertabel _Documenttypes_ heeft een aanvinkvakje _Is documenttype voor bodem_ (dlisdoctypebodem). Het **blok Bodem** (tussen het blok Meta en Collegiale toetsing) is alleen zichtbaar indien het documenttype van het betreffende geregistreerde document een bodemdocumenttype is. In het blok Bodem is momenteel aan te geven of het bodemrapport doorgezet is naar het BIS en onder welke code.

### Blok CC's

In het **blok cc's** kunnen Ã©Ã©n of meer contactpersonen worden opgevoerd die bij verzending het document (inclusief bijlagen) toegezonden krijgen per mail. De kolom ddemailverzonden wordt bij succes gevuld met de datum van de email, zodat voorkomen wordt dat de email twee keer verzonden wordt. Uiteraard dient ook het emailadres gevuld te zijn. Het plusknopje om een nieuwe persoon toe te voegen is altijd zichtbaar. De wizard die gestart wordt zal uitleg geven indien er op dat moment toch geen nieuwe cc kan worden toegevoegd.

De gebruiker kan kiezen uit de:

- contactpersonen die horen bij de bovenliggende zaak met uitzondering van de hoofdgeadresseerde die genoemd staat op de geregistreerde documentkaart. Echter, indien het geregistreerde document geboekt staat als te verzenden per post, dan kan toch ook deze hoofdgeadresseerde hier opgevoerd worden. Deze persoon krijgt in dat geval dus het document per post en per email
- de contactpersonen bij een inrichting die gekoppeld is aan de hoofdzaak. Hiervoor moet de instelling _Sectie: DocumentRegistreren en Item: Inrichtingcontactpersonen_ aangevinkt staan.

OpenWave zorgt dat er geen doublures kunnen ontstaan in de lijst met cc's.

Wanneer de mailverzending niet goed gaat (bijv. document te groot), wordt indien mogelijk de oorzaak en datum/tijdstip van de mislukte poging bij de cc's gedocumenteerd. Indien bij een tweede poging de verzending wel lukt dan worden deze kolommen weer leeggemaakt (en ddmailverzonden gevuld).

Door de kolom **Bcc** aan te vinken kan ervoor gezorgd worden dat de ontvanger als bcc de mail krijgt in plaats van cc. De defaultwaarde van dit vakje is cc, maar indien de instelling _Sectie: DocumentRegistreren en Item: Emailccalsbcc_ is aangevinkt dan bcc.

Er zijn twee manieren waarop de cc's een mail krijgen:

- Het geregistreerde document staat geboekt als per mail te verzenden. In dat geval is de email-knop onderaan het documentscherm zichtbaar (zie voor de voorwaarden hieronder bij de knop _verzend email_), waarmee zowel de hoofdgeadresseerde van de documentkaart als alle cc's de documenten per email krijgen. Ook de inlogger die de knop start krijgt als cc dezelfde mail. Bij succes wordt de datum verstuurd gevuld van het geregistreerde document.
- Het geregistreerde document staat geboekt als per post te verzenden. In dat geval is de email-knop onderaan het documentscherm NIET zichtbaar. De hoofdgeadresseerde krijgt de documenten per post. Maar de cc's kunnen wel de documenten per mail krijgen. Hiertoe moet het emailknopje onderaan de lijst van cc's worden gebruikt (voorwaarde is onder meer dat document definitief is of al verstuurd: OpenWave geeft zo nodig uitleg indien er instellingen ontbreken). De hoofdgeadresseerde is in dit geval de inlogger zelf.

Zie ook hieronder bij kopje _Verzendwijze_.

Indien:

- de instelling _Sectie: DocumentRegistreren en Item: MailOokOpslaanInCorresp_ aangevinkt is
- en de email naar de cc's is succesvol verzonden (in zoverre OpenWave daar weet van heeft)

dan zal de verzonden email worden opgeslagen als .EML bestand en wordt er een nieuwe correspondentiekaart aangemaakt die hiernaar verwijst.

### Maak PDF

Vooralsnog uitdrukkelijk bedoeld voor documenten die zich op een fileshare bevinden. Wordt getriggerd door een knop onderaan het detailscherm (zie hieronder voor de zichtbaarheidscondities van de knop) of door digitale ondertekening (zie voor condities hieronder bij kopje _Digitale ondertekening_).

De knop, of de digitale ondertekening, start een actie waarbij het document omgezet wordt naar PDF en opgeslagen op de plek waar het document vandaan kwam. Deze PDF behoud dezelfde registratie in de geregistreerde documenten (alleen de extensie van de filenaam verandert en eventueel de externe documentidentificatiecode bij opslag in DMS). De registratie van het oorspronkelijke document wordt dus vervangen door de PDF. Het fysieke oorspronkelijke document zelf wordt dus niet verwijderd, maar is niet meer via de geregistreerde documenten terug te vinden.

De eigenschap **Definitief** op de registratiekaart van de nieuwe pdf wordt op (J)a gezet (een voorwaarde voor digitale ondertekening).

Als de knop zichtbaar is, is direct ook de knop _refresh scherm_ zichtbaar. Dit komt omdat het programma niet weet wanneer de omzetting naar PDF afgerond is (externe schijven c.q. extern DMS).

Na klikken op de Maak PDF-knop, zal onderwater voor het document tbcorrespondentie.dlpdfmakenbezig op true gezet worden zodat de programmatuur weet dat er een proces van PDF maken bezig is. De Maak PDF-knop zal vervolgens als inactief worden weergegeven (grijs). Hiermee wordt voorkomen dat het maak PDF proces meerdere keren wordt aangeroepen terwijl er al een proces bezig is. Vervolgens kan de gebruiker via de refreshknop het scherm opnieuw laten uitgeschreven en zullen de knoppen verdwijnen zodra het maak PDF proces is afgerond, en zal de extensie .pdf zichtbaar worden.

LET OP: Het renderen van documenten met de extensies ods, odt, doc, docx, xls, xlsx,txt en xml kan alleen indien de kolom _Tekst_ gebeurt via OnlyOffice (mits geÃ¯nstalleerd). Indien _Getal1_ van _Sectie: Documenten en Item: ConverteerPDF_ de waarde 1 heeft. Zo niet, dan worden documenten geconverteerd naar PDF via LibreOffice. In dit laatste geval dient de instelling _Sectie: Koppeling Converter en Item: EndpointClassDocument_ gevuld te zijn met een valide endpoint van de libreoffice-converter.

Bijvoorbeeld:

```
http://localhost:9763/services/nl.rem.docconv.manager.published.Documents.nl.rem.docconv.manager.published.DocumentsHttpsSoap11Endpoint/>
```

## Digitaal ondertekenen

De documentsjablonen tabel (tbdocumenten) is uitgebreid met een aanvinkvakje om een document te typeren als zijnde _moet digitaal ondertekend worden_. Bij de geregistreerde documenten (tbcorrespondentie) wordt deze waarde overgenomen (dlmoetdigondertekenen) indien het geregistreerde document op basis van een sjabloon is gemaakt. Alleen een medeweker met het recht _Mag kolom moet digitaal ondertekend worden aanpassen_ tbmedewerkers.dlmagmoetdiotaanpassen mag deze kolom muteren.

Het aanvinkvakje _digitaal ondertekenen_ (dlisdigondertekend) is alleen muteerbaar indien:

- de inlogger het recht _mag digitaal ondertekenen_ in de medewerkerstabel aangevinkt heeft staan
- en het betreffende document gemarkeerd staat als Definitief en Uitgaand
- en de kaart niet geblokkeerd is en de compartimentsrechten OK zijn.

Indien:

- het betreffende document nog geen PDF is (de extensie van upper(dvdocfilenaam) <> âPDFâ)
- en dat document bevindt zich op de server en dus niet lokaal (dvdocplaats moet de waarde S hebben)
- en de instelling _Sectie: DocumentRegistreren en Item: MaakPDFbijOndertekening_ is aangevinkt

Dan zal de ondertekening automatisch leiden tot omzetting van het document naar PDF: zie hierboven onder kopje _PDF_.

### Document moet aangepast worden

Het aanvinkvakje document moet aangepast worden(dlbriefmoetaangpast) is alleen muteerbaar indien:

- de inlogger het recht _mag digitaal ondertekenen_ in de medewerkerstabel aangevinkt heeft staan
- en het betreffende document gemarkeerd staat als Definitief en Uitgaand
- en de kaart niet geblokkeerd is en de compartimentsrechten OK zijn
- en wanneer de kolom _digitaal ondertekenen_ (dlisdigondertekend) NIET is aangevinkt. |

Met het aanvinken wordt de status definitief automatisch op Nee gezet.

### Document Definitief maken

Is muteerbaar voor iedereen met recht _Registreren en wijzigen metadata van geregistreerde documenten_ (bijv. tbomgrechten.dlcomgcoredt). Het definitief maken heeft automatisch tot gevolg dat het aanvinkvakje _document moet aangepast worden_ (dlbriefmoetaangpast) leeggemaakt wordt.

### Documentfase

Is zichtbaar indien instelling _Sectie: DocumentRegistreren en Item: Documentfase_ is aangevinkt. Muteerbaar indien gebruiker recht heeft op het wijzigen van metadata van geregistreerde documenten.

### Vereiste Vertrouwelijkheid

Om het document te kunnen inzien moet de vereiste vertrouwelijkheid (dnkeyvertrouwelijkheid) een lege waarde hebben OF de inlogger moet een vertrouwelijkheidsniveau hebben (beheertabel medewerkers: _Mag docs inzien tot vertrouwelijkheidsniveau_) dat hoger is dan (of gelijk aan) het vereiste niveau bij het geregistreerde document. De niveaus zijn vastgelegd in de beheertabel tbvertrouwelijkheid (tegel _Vertrouwelijkheidsindicatie_).

Een inlogger met wijzigrechten op de geregistreerde documenten kan een vereist niveau alleen aanpassen indien dat niveau lager of gelijk is aan het ingestelde niveau bij de medewerker.

Bij (automatische) registratie van documenten uit OLO, DSO of SWF geldt het volgende:

- OLO document en de zaak speelt in een compartiment. De registratie krijgt een niveau dat gelijk is aan de waarde van de kolom dvolodsovertrouwelijkheid van het betreffende compartiment. Deze tekst wordt opgezocht in de kolom omschrijving van de vertrouwlijkheidtabel. Indien niet gevonden dan wordt gepoogd om de dnkey van de tabel vertrouwelijkheid over te nemen met de waarde _openbaar_. Ook die niet gevonden dan blijft de vereiste vertrouwelijkheid leeg.
- OLO document en de zaak speelt NIET in een compartiment. De registratie krijgt een niveau dat gelijk is aan de waarde van de kolom _Tekst_ van de instelling _Sectie: KoppelingDOCNAARDMS Item: OloVertrouwelijkheid_. Deze tekst wordt opgezocht in de kolom omschrijving van de vertrouwlijkheidtabel. Indien niet gevonden dan wordt gepoogd om de dnkey van de tabel vertrouwelijkheid over te nemen met de waarde _openbaar_. Ook die niet gevonden dan blijft de vereiste vertrouwelijkheid leeg.
- DSO documenten. OpenWave kijkt naar de DSO-vertrouwelijkheidindicatie (true of false) zoals aangeleverd in het STAM-bericht (en opgeslagen in de tabel tbomgoloberichten en overgenomen in de kolom dldsoisvertrouwelijk van tbcorrespondentie). Indien true dan kijkt OpenWave naar de vertaling in de kolom _Tekst_ van de instelling _Sectie: DSO Item: VertalingVertrouwelijkheid_. Deze tekst wordt opgezocht in de kolom omschrijving van de vertrouwelijkheidstabel. Indien niet gevonden, OF als DSO-vertrouwelijkheidindicatie false is, dan wordt een poging gedaan op grond van de kolom _Tekst_ van de instelling _Sectie: KoppelingDOCNAARDMS Item: OloVertrouwelijkheid_ (of in geval van compartiment bij het compartiment in veld dvolodsovertrouwelijkheid). Indien nog geen match met een kaart in tbvertrouwelijkheid dan wordt nog een zoekpoging gedaan met de waarde _openbaar_. Ook die niet gevonden dan blijft de vereiste vertrouwelijkheid leeg.
- SWF documenten. OpenWave kijkt naar de SWF-vertrouwelijkheidindicatie (RV of SV: regulier of strikt vertrouwelijk ) zoals vermeld in de SWF-ruimte (en opgeslagen in de tabel tbswfdocumenten). Indien RV dan kijkt OpenWave naar de vertaling in de kolom _Getal1_ van de instelling _Sectie: SWF Item: VertalingVertrouwelijkheid_. Indien SV dan kijkt OpenWave naar de vertaling in de kolom _Getal2_ van deze instelling. De gevonden waarde wordt opgezocht in de dnkey-kolom van de vertrouwelijkheidstabel. Indien niet gevonden dan wordt in beide gevallen nog een poging gedaan op grond van de kolom _Tekst_ van de instelling _Sectie: KoppelingDOCNAARDMS Item: OloVertrouwelijkheid_ (of in geval van compartiment bij het compartiment in veld dvolodsovertrouwelijkheid). Indien nog geen match dan blijft de vereiste vertrouwelijkheid leeg.

Bij het automatisch registreren van documenten bij de import van erkende maatregelen kijkt OpenWave naar de kolom _Tekst_ van de instelling _Sectie: ErkendeMaatregelen en Item: DocVertrouwelijkheid_. De tekst wordt opgezocht in de kolom omschrijving van de vertrouwelijkheidstabel om de juiste dnkey te vinden. Bij probleem wordt de maatregel niet ingelezen.

Bij het registreren van rapporten uit Digitale Checklisten kijkt OpenWave naar de kolom _Tekst_ van de instelling _Sectie: KoppelingINSPTOETS en Item: VertrouwelijkheidReport.pdf_. De tekst wordt opgezocht in de kolom omschrijving van de vertrouwelijkheidstabel om de juiste dnkey te vinden. Bij probleem wordt het rapport niet opgehaald en geregistreerd.

Bij het handmatig registreren van een document moet de inlogger een keuze maken uit de tabel tbvertrouwelijkheid indien de instelling _Sectie: DocumentRegistreren en Item: DvVertrouwelijkheid_ is aangevinkt (in _Getal1_ van deze instelling kan als default een dnkey uit tbvertrouwelijkheid worden opgegeven).

Indien de instelling _Sectie: DocumentRegistreren en Item: allehandmatigeuploads_ aangevinkt is, zal tijdens het uploaden de vertrouwelijkheid moeten worden opgegeven (indien de instelling _Sectie: DocumentRegistreren en Item: DvVertrouwelijkheid_ is aangevinkt).

### Verzendwijze

Post of Email. Indien de registratie automatisch is aangemaakt vanuit het creÃ«ren van een document op basis van een documentsjabloon, en tijdens het creÃ«ren is de keuze gemaakt voor _Per Post_, dan is deze keuze hier overgenomen en NIET Muteerbaar (onder water heeft de onzichtbare kolom _tbcorrespondentie.dlperpostvastbijaanmaak_ in dat geval de waarde T gekregen).

De kolom is ook niet meer muteerbaar indien Definitie = Ja en richting is Uitgaand.

Indien per mail dan is onderaan de pagina een email-knop zichtbaar (kijk hieronder bij triggers voor overige condities), waarmee een standaard email verstuurd kan worden met het document (en alle bijlages die bij het document horen) als bijlage bij die mail. Die mail wordt ook naar alle cc's, bcc's verstuurd.

### Regenereer opgeslagen DMS document op basis van oorspronkelijke sjabloon

Indien:

- de instelling _Sectie: Documentregistreren en Item: Regeneratie_ is aangevinkt
- en de gebruiker het creÃ«er recht op documenten heeft( bijv. tbomgrechten.dlcomgcorins).

Dan geldt dat linksonder op de detailpagina de regeneratieknop zichtbaar wordt, mits dat geregistreerde document aan de volgende voorwaarden voldoet:

- Een gevulde externe documentidentifier: dus het document bevindt zich in een DMS (tbcorrespondentie.dvintdoccode is not null)
- en aangemaakt is op grond van een sjabloon en die link is nog in tact (tbcorrespondentie.dnkeydocumenten is not null)
- en nog niet is verstuurd (ddbriefdatum is null)
- en compartimentscheck OK
- en nog niet definitief is (dvdefinitief = 'N')
- en niet is geblokkeerd (dus de blokkeerdatum van de bovenliggende zaak is null).

Met die regeneratieknop wordt de maakDocument-wizard aangeroepen met een verwijzing naar hetzelfde sjabloon als waarop de registratiekaart is gebaseerd. De gebruiker krijgt nog een waarschuwing dat het bestaande document overschreven gaat worden: het nieuwe document op basis van het sjabloon wordt namelijk onder de oude externe documentidentifcatiecode opnieuw aangeboden met een (stuf) updateZaakdocument bericht.

De naam en alle andere metadata van het document worden hergebruikt: kunnen niet worden gewijzigd. De kolommen van het geregistreerde document (tbcorrespondentie) worden niet gewijzigd met uitzondering van de geadresseerde, die wel desgewenst opnieuw gekozen kan worden. Ccâs en Bijlages kunnen ook niet worden gewijzigd.

### Triggers in scherm

Knop **Contactadreskaart** in blok _Adres_. Enabled indien er een (hoofd) adres aanwezig is. Met de knop wordt het detailscherm van het contactadres geopend.

Knop **Open URL** Enabled indien de kolom dvurl begint met _http_ of met _// of \._

### Triggers linksonder

#### Maak definitief en PDF

- Zichtbaar en enabled indien:
  - de instelling _Sectie: DocumentRegistreren en Item: KnopMaakPDFZichtbaar_ is aangevinkt
  - en de geregistreerde documentkaart muteerbaar is (en niet geblokkeerd)
  - en de extensie van het document = ods, odt, odf, doc, docx, xls,xlsx of txt of xml
  - en de plaats van het document = (S) erver (dat betekent dat het document dus NIET gemarkeerd staat als _wordt lokaal bewerkt_)
  - en het document is nog niet verstuurd (tbcorrespondentie.ddbriefdatum is null).

De knop wordt alsnog onzichtbaar indien

- het document digitaal ondertekend met worden (vwfrmcorrespondentie.dlmoetdigondertekenen = T)
- en de instelling _Sectie: DocumentRegistreren en Item: MaakPDFbijOndertekening_ is aangevinkt
- en kolom _getal1_ van de instelling _Sectie: DocumentRegistreren en Item: KnopMaakPDFZichtbaar_ heeft waarde 1

Indien _Getal1_ van _Sectie: Documenten en Item: ConverteerPDF_ de waarde 1 heeft dan worden documenten geconverteerd naar PDF via de OnlyOffice installatie (mits aanwezig). Indien deze instelling niet bestaat of _Getal1_ heeft een andere waarde, dan wordt geconverteerd met LibreOffice.

#### Refresh scherm

- Zichtbaar en enabled indien:
  - de instelling _Sectie: DocumentRegistreren en Item: KnopMaakPDFZichtbaar_ is aangevinkt
  - en de geregistreerde documentkaart muteerbaar is (en niet geblokkeerd)
  - en de extensie van het document = ods, odt, odf, doc, docx, xls,xlsx of txt of xml
  - en de plaats van het document = (S) erver (dat betekent dat het document dus NIET gemarkeerd staat als _wordt lokaal bewerkt_).

#### Download document inclusief bijlages

- Zichtbaar en enabled inden de gebruiker het recht _Toelaten geforceerde download geregistreerd document_ aangevinkt heeft staan voor de betreffende module (bijv. tbomgrechten.dlcomgcorregdwl). Met de knop kan het document worden gedownload inclusief bijlagen. Indien er bijlagen zijn, dan worden deze met het hoofddocument gedownload in een zipfile naar de device van de inlogger. De naam van die zipfile is: DownloadOpenWave_datum_tijstip.zip (bijv. DownloadOpenWave_20201126_093926.zip). Indien er GEEN bijlagen zijn, dan wordt alleen het hoofddocument gedownload naar de device van de inlogger.

Er kan een afwijkende zipfilenaam worden geconstrueerd indien de kolom _Tekst_ van de instelling _Sectie: Documenten en Item: Downloadzipfilenaam_ gevuld is met een tekststring langer dan 5 tekens en eindigend op .zip In dat geval is de naam van de zipfile de waarde van deze kolom _Tekst_ waarbij de variabele (let op case sensitive):

- Úte% vervangen wordt door TimeStamp
- %login% wordt vervangen door de medewerkerscode van de inlogger
- %hoofdzaaknr% wordt vervangen door de wavezaakcode
- %hoofddmsnr% wordt vervangen door de externe zaak/DMS code
- ­res% wordt vervangen door het adres + de woonplaats.

#### Verzend email

Let op: voor de emailknop onderaan het lijstje van het blok _cc's_ zie hierboven.

- Zichtbaar en enabled indien:
  - verzendwijze = email (tbcorrespondentie.dlmoetperpost = 'F')
  - en de richting is uitgaand (tbcorrespondentie.dvdocrichting = 'U')
  - en Definitief is Ja (tbcorrespondentie.dvdefinitief = 'J')
  - en het document is nog niet verstuurd (tbcorrespondentie.ddbriefdatum is null)
  - en het document wordt niet lokaal bewerkt (tbcorrespondentie.dvdocplaats = 'S')
  - en â indien het document digitaal ondertekend moet zijn -, dan moet tbcorrespondentie.dlisdigondertekend de waarde T hebben
  - en de kolom _Tekst_ van instelling _Sectie: DocumentRegistreren en Item: StandaardEmailTekstAanhef_ moet gevuld zijn (zie bij [Documenten/Verzendstroom](../programmablokken/documenten_verzendstroom.md) voor substitutie van variabelen)
  - en de kolom _Tekst_ of kolom _Toelichting_ van instelling _Sectie: DocumentRegistreren en Item: StandaardEmailTekstBody_ moet gevuld zijn. Indien beide gevuld kijkt OpenWave naar de kolom _Toelichting_ (dvtoelichting), waarin 2000 karakters kunnen staan i.p.v. 255 van de kolom _Tekst_.

Indien:

- de instelling _Sectie: DocumentRegistreren en Item: MailOokOpslaanInCorresp_ aangevinkt is
- en de email is succesvol verzonden (in zoverre OpenWave daar weet van heeft)

dan zal de verzonden email worden opgeslagen als .EML bestand en wordt er een nieuwe correspondentiekaart aangemaakt die hiernaar verwijst.

#### Open Document

Dezelfde redenering wordt gevolgd als beschreven bij het klikken op het lijstscherm van de geregistreerde documenten.

#### Regenereer Document

Zie hierboven bij het kopje _Regenereer opgeslagen DMS document op basis van oorspronkelijke sjabloon_.
