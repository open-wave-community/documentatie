# Geregistreerde  documenten

## Trigger

De tegel is een trigger voor het lijstscherm van de *Geregistreerde documenten* bij een DSO project. Het lijstscherm toont alle geregistreerde documenten van de DSO zaken met hetzelfde dnkeydsoproject.

  - De tegel is alleen zichtbaar voor inlogger wanneer:
    - deze aan hem/haar is toegekend
    - de evaluatie van het *SQL statement onzichtbaar* bij de tegeldefinitie een waarde ongelijk aan 0 oplevert:
  - Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Probleem

Het dynamische opschrift op tegels is niet zichtbaar:

  - indien foutieve queryverwijzing (codering *dso_overig_geregdocumenten*)
  - indien query zelf niet correct (zie [Queries](../../../../instellen_inrichten/queries.md))
  - indien inlogger geen recht heeft om query uit te voeren
  - indien de kolom *altijd verversen* (tbportaltiles.dlaltijdrefreshen) op de tegeldefinitie uitgevinkt is.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](../../../../instellen_inrichten/portaldefinitie/portal_tegel.md)):

  -  Portaal: *dsoprojectportaal*
  -  Kolom: *Overig*
  -  Kopregel: *Geregistreerde documenten*
  -  Dynamisch tegelopschrift: *getTileContent(dso_overig_geregdocumenten,{id})*
  -  Actie: *getFlexList(SysStandardList,,{id},nil,dso_overig_geregdocumenten)*

