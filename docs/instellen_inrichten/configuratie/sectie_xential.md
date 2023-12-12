# Sectie Xential

Hieronder de instellingen uit de configuratietabel configuratietabel (tbinitialisatie) van de _Sectie: Xential_ gerangschikt op item. Deze instellingen zijn alleen van belang indien gebruik gemaakt wordt van Xential als sjabloongenerator. Zie: [Xential](/docs/probleemoplossing/programmablokken/xential.md)

| Item | Kolom | Omschrijving |
| ---- | ----- | ------------ |
| endpointwebhookurl | Tekst | Het endpoint dat Xential moet gebruiken om het samengestelde document terug te sturen naar OpenWave bijv. _<https://demo2.open-wave.nl:4444/api/xential/index.php>_ |
| Genereervoorafdocidentifier | Aanvinkvakje | Indien aangevinkt en methode = 2 (dus gegenereerde document wordt via stuf/zaak in DMS opgeslagen) dan zal OpenWave voordat Xential aangeroepen wordt, bij het DMS een documentidentifier opvragen (genereerDocumentidentificatie). Deze documentidentifier wordt in de xml met merge data meegenomen in de tag `<docidentifier>` zodat deze gebruikt kan worden in het sjabloon. |
| login | Tekst | De loginnaam van de integratie-gebruiker voor de API-aanroepen vanuit OpenWave. |
| messagelog | Aanvinkvakje | Indien aangevinkt worden de berichten naar Xential gelogd mits de algemene instelling _Sectie: OWB en Item: MessageLog_ ook aangevinkt is. |
| methode | Getal1 | 1, 2 of 3, waarbij 3 deprecated is. 1 wil zeggen dat het geretourneerde document door OpenWave op de fileserver wordt opgeslagen, 2 wil zeggen dat het geretourneerde document in het DMS (stuf-zaak/dms) door OpenWave wordt opgeslagen. 3 (deprecated!) betekent dat het document door Xential in het DMS wordt opgeslagen. |
| password | Tekst | Password van de integratie-gebruiker voor de API-aanroepen vanuit OpenWave. Kan gecrypt worden opgeslagen (zie [Sectie Encryption](/docs/instellen_inrichten/configuratie/sectie_encryption.md)) |
| restendpoint | Tekst | Endpoint voor de REST aanroepen vanuit OpenWave (impersonate, getususbletemplates createticket, logout) bijv. _<https://openwave.labs.xential.nl/xential/modpages/next.oas/api>_ |
| robotusername | Tekst | loginnaam die door OpenWave bij de getTicket-aanroep wordt meegegeven waarmee Xential zich kan identificeren op het endpointwebhookurl om het samengestelde document te retourneren. Robotusername en robotpassword moeten ook in de medewerkerstabel van OpenWave zijn opgeslagen (zonder 2 factor, verloopt nooit, geen loginverklaring). |
| robotpassword | Tekst | password dat door OpenWave bij de getTicket-aanroep wordt meegegeven waarmee Xential zich kan identificeren op het endpointwebhookurl om het samengestelde document te retourneren. Kan gecrypt worden opgeslagen (zie [Sectie Encryption](/docs/instellen_inrichten/configuratie/sectie_encryption.md)). Robotusername en robotpassword moeten ook in de medewerkerstabel van OpenWave zijn opgeslagen. |
| root | Tekst | Vast gedeelte van de URL waaraan de respons van de getTicket-API (startDocumentUrl) aan vast wordt geplakt om Xential als gebruiker aan te kunnen roepen met het gekozen sjabloon bijv. _<https://openwave.labs.xential.nl>>_ |
| username | Tekst | De username waarmee de impersonate-API moet worden aangeroepen om een sessie-id te verkrijgen. |