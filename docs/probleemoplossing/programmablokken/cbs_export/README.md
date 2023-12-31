# CBS export

## Algemeen

In OpenWave kunnen de CBS-gegevens die volgens het W011-formulier moeten worden opgestuurd worden aan het CBS, verzameld worden in een vooraf gespecificeerd exportbestand. Het exportbestand kan vervolgens door CBS bepaalde indienmogelijkheden, aangeboden worden aan het CBS.

Het exportbestand wordt opgesteld volgens de handleiding van het CBS: _HandleidingElektronischAanleverenVerleendeBouwvergunningen.pdf_.

## Export altijd per gemeente

Het exporteren van de CBS-gegevens gebeurt altijd per gemeente. Op basis van de gemeentecode/id (altijd vier karakters lang) wordt door de programmatuur het **Gemeentenummer** bepaald wat moet worden doorgegeven aan het CBS. Het CBS verwacht een 6-cijferig gemeentenummer. Dit wordt normaliter samengesteld door de wel bekende viercijferige gemeentecode op te vullen met twee voorloopnullen.

Indien men gewend is om het gemeentenummer aan CBS door te geven opgesteld als viercijferige gemeentecode met daarachter twee vaste cijfers, dan dient men PER gemeente de volgende instelling aan te maken: _Sectie: CBS_, _Item: <gemeentecode>_ (bijvoorbeeld '0228') en bij _Tekst_ de twee cijfers op te geven.

**Let op:** de eigenschap **Opnemen in keuzelijst maken CBS-exportlijst** dient aangevinkt te zijn voor de gemeente(s) waarvoor men CBS-gegevens wil exporteren. Dit kan men in het beheerportaal-Nieuw via de tegel _OIN_ beheren. Bij het opstellen van de CBS-exportlijst kan er alleen gekozen worden uit gemeentes waarvoor deze eigenschap van toepassing is.

## Werking

In portaal _Operations_ is onder de tegel _CBS Export_, alle functionaliteit omtrent de CBS export terug te vinden. Benodigde instellingen voor de export kunnen aangemaakt worden/zijn te beheren via de tegel _Configuratie_ in het beheerportaal-Nieuw. Zie [Configuratie instellingen CBS](../../../../instellen_inrichten/configuratie/sectie_cbs) voor een overzicht van deze instellingen. Ook kan men in de configuratie instellingen ([Operations instellingen](../../../../instellen_inrichten/configuratie/sectie_operations).md) terugvinden of er al een operatie draait voor de CBS export: zodra of de lijst gegenereerd wordt, ofwel het exportbestand gegenereerd wordt, wordt instelling _Sectie: Operations, Item: ExportCBS_ aangemaakt/aangepast met vullen van datum, medewerker die de operatie gestart heeft en _Getal1_ = 1 gezet. Is de operatie klaar dan wordt _Getal1_ leeggehaald.

De volgende stappen dienen te worden doorlopen voor het verzamelen van de te exporteren CBS-gegevens en daarmee tot stand brengen van het uiteindelijke exportbestand:

- **Samenstellen van de lijst met de te exporteren CBS-gegevens**
- **Genereren van het exportbestand**
- **Downloaden van het gegenereerde exportbestand**

### Samenstellen van de lijst met de te exporteren CBS-gegevens

Allereerst dienen de te exporteren CBS-gegevens verzameld te worden die uiteindelijk geëxporteerd moeten worden. Het maken van de zo genoemde _Lijst met te exporteren CBS-gegevens_ gebeurt via een wizard waarbij gevraagd wordt voor welke gemeente de lijst moet worden opgesteld. Uitgebreide uitleg over het aanmaken van de lijst is beschreven op pagina: [Lijst met te exporteren CBS-gegevens](cbs_export/lijst_met_te_exporteren_cbsgegevens.md)

![](../../../img/applicatiebeheer/probleemoplossing/programmablokken/cbslijstexportgegevens.png){ class="media" loading="lazy" alt="" width="1400" }

#### Operationslog: Aanmaken lijst CBS exportregels

Tijdens het aanmaken van de CBS exportlijst (vullen van tabel tbcbsexport) wordt in de tabel tboperationslog een kaart aangemaakt met de code _Aanmaken lijst CBS-exportregels_. De Operationslog is terug te vinden in portaal _Operations_, kolom _Overig_, tegel _Operationslog_.

In de kolom _aantal verwerkt_ in deze tabel wordt het aantal CBS-regels bijgehouden dat door het proces van aanmaken van de lijst is gegaan. De gebruiker zal zelf af en toe de refreshknop linksonder moeten gebruiken om deze voortgang te kunnen zien (het aanmaken van de lijst is een onafhankelijk proces zonder user-interface).

In de kolom voortgang staat _Ben bezig_ OF _Klaar_ OF _Afgebroken door gebruiker_. Deze laatste mogelijkheid is het geval wanneer de gebruiker tijdens het proces de kolom tboperations.dlstop op T heeft gezet.

In de kolom LOG (te openen via knop linksonder) worden de aantallen bijgehouden.

### Genereren van Exportbestand

Het genereren van het exportbestand gebeurt via een wizard die aan te roepen is vanaf lijstscherm _Lijst met te exporteren CBS-gegevens_.
Het exportbestand is een .txt bestand (ASCII) dat door de programmatuur regel voor regel gevuld wordt met de te exporteren CBS-gegevens. Hierbij worden alleen de met witte kleurbol aangegeven regels uit lijst _Lijst met te exporteren CBS-gegevens_ doorlopen met de voor de gebruiker geldende compartimentsconditie. TENZIJ bewust wordt aangevinkt dat men ook de met oranje kleurbol aangegeven regels uit de lijst wilt exporteren: dit zijn de regels waarvoor of het aardbesluit NIET _Verleend_ is, en/of de besluitdatum van de vergunning niet gevuld is.

Het bestand zal als bestandsnaam de vorm krijgen: W011GGGG.MM.TXT waarbij GGGG vervangen wordt door de viercijferige gemeentecode en MM vervangen wordt door de verslagmaand (maand uit de gekozen verstuurdatum). Elke regel in het exportbestand is opgeknipt in een aantal kolommen. Er is geen scheidingteken tussen de kolommen en elke kolom heeft een vast aantal posities.

#### Test of Definitief?

Bij het maken van het exportbestand wordt de gebruiker gevraagd of het gaat om een _Test_ export of _Definitieve_ export. Indien er gekozen wordt voor _Test_ dan zal de naam van het exportbestand beginnen met _Test\__ en de eerste regel van het exportbestand _TESTTESTTEST_ zijn. Na het genereren van de export zullen de onderliggende CBS regels niet worden voorzien van een verstuurdatum. De gebruiker kan het genereren van het exportbestand op basis van de lijst met te exporteren CBS-gegevens herhalen. Indien er gekozen was voor _Definitief_ dan zal voor de geëxporteerde CBS regels de verstuurdatum gevuld worden met datum zoals gekozen in de wizard (default de datum van vandaag). De gehele lijst met te exporteren CBS-gegevens zal leeggemaakt worden.

#### Operationslog: Exporteren CBS-exportregels

Tijdens het generen van het exportbestand wordt er ook een kaart aangemaakt in de tabel tboperationslog, maar dan met code _Exporteren CBS-exportregels_. Deze logging is terug te vinden onder de knop _Exportbestanden_ in de lijst _Lijst met te exporteren CBS-gegevens_.

In de kolom _aantal verwerkt_ in deze tabel wordt het aantal exportregels bijgehouden dat door het proces van exportbestand opstellen is gegaan. De gebruiker zal zelf af en toe de refreshknop linksonder moeten gebruiken om deze voortgang te kunnen zien (het exportbestand genereren is een onafhankelijk proces zonder userinterface).

In de kolom voortgang staat _Ben bezig_ OF _Bestand_ OF _Afgebroken door gebruiker_. Deze laatste mogelijkheid is het geval wanneer de gebruiker tijdens het proces de kolom tboperations.dlstop op T heeft gezet.

### Downloaden van het gegenereerde exportbestand

Het exportbestand wordt na genereren als een base64 string opgeslagen in tboperationslog en is terug te vinden in blok _Bestand_ in het detailscherm van de log. Hier is ook de bestandsnaam terug te vinden.

In het lijstscherm _Logboek Operations_ dat te openen is vanuit _Lijst met te exporteren CBS-gegevens_ bevindt zich een downloadknop (linksonder). Hiermee is het gegenereerde exportbestand te downloaden. **Via deze knop kan men dus daadwerkelijk het exportbestand verkrijgen!**

### Kolommenoverzicht

De kolommen van het exportbestand liggen vast en zijn altijd gelijk qua volgorde, hun lengte en positie. Deze worden door CBS bepaald en staan beschreven in de door CBS uitgegeven elektronische handleiding. Om het ook via de dokuwiki inzichtelijk te maken wat de gebruiker kan verwachten qua opmaak van het exportbestand, is het kolommenoverzicht zoals de programmatuur deze maakt inzichtelijk op pagina [Kolommenoverzicht CBS](cbs_export/kolommen_overzicht.md)
