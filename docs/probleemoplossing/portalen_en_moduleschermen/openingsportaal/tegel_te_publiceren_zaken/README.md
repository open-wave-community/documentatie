# Tegel Te publiceren zaken (DROP)

## Trigger

De tegel is een trigger voor het openen van de [Lijst te publiceren zaken](tegel_te_publiceren_zaken/lijst_te_publiceren_zaken.md) van waaruit DROP-publicaties kunnen worden verstuurd. Zie: [Drop](../../../../instellen_inrichten/drop.md).

  - De tegel is alleen zichtbaar voor inlogger wanneer:
    - deze aan hem/haar is toegekend
    - de evaluatie van het *SQL statement onzichtbaar* bij de tegeldefinitie een waarde ongelijk aan 0 oplevert.
  - Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Probleem

Het dynamische opschrift op tegels is niet zichtbaar, maar wel gedefinieerd:

  - indien foutieve queryverwijzing
  - indien query zelf niet correct (zie [Queries](../../../../instellen_inrichten/queries.md))
  - indien inlogger geen recht heeft om query uit te voeren
  - indien de kolom *altijd verversen* (tbportaltiles.dlaltijdrefreshen) op de tegeldefinitie uitgevinkt is.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](../../../../instellen_inrichten/portaldefinitie/portal_tegel.md)):

  - Portaal: *Opening*
  - Kolom: *Beheer*
  - Kopregel:
  - Vast Opschrift:*Te publiceren zaken (DROP)*
  - Dynamisch tegelopschrift:
  - Actie: *getFlexList(SysStandardList,nil,nil,G,opening_drop)*

