# Tegel Asbest

## Trigger

De tegel is een trigger voor een tabel met *Asbestsaneringen* per inrichting.

* De tegel is alleen zichtbaar voor inlogger wanneer:
  * deze aan hem/haar is toegekend
  * de evaluatie van het *SQL statement onzichtbaar* bij de tegeldefinitie een waarde ongelijk aan 0 oplevert.
* Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Probleem

Het dynamische opschrift op tegels is niet zichtbaar:

* indien foutieve queryverwijzing (codering *inrichting_asbest*)
* indien query zelf niet correct (zie [Queries](../../../instellen_inrichten/queries.md))
* indien inlogger geen recht heeft om query uit te voeren.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](../../../instellen_inrichten/portaldefinitie/portal_tegel.md)):

* Portaal: *inrichtingdetail*
* Kolom: *Veiligheid*
* Kopregel: *Asbest*
* Dynamisch tegelopschrift: *getTileContent(inrichting_asbest,{id})*
* Actie: *getFlexList(tbmilasbest,tbmilinrichtingen,{id},,V)*
