# Urensoorten

De tegel is een trigger voor een lijst van *Soorten uren* die gebruikt kunnen worden bij de urenregistratie.

  - De tegel is alleen zichtbaar voor inlogger wanneer:
    - deze aan hem/haar is toegekend
    - de evaluatie van het *SQL statement onzichtbaar* bij de tegeldefinitie een waarde ongelijk aan 0 oplevert
  - Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Probleem

Het dynamische opschrift op tegels is niet zichtbaar:

  - indien foutieve queryverwijzing
  - indien query zelf niet correct (zie [Queries](../../../../instellen_inrichten/queries.md))
  - indien inlogger geen recht heeft om query uit te voeren
  - indien de kolom *altijd verversen* (tbportaltiles.dlaltijdrefreshen) op de tegeldefinitie uitgevinkt is.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](../../../../instellen_inrichten/portaldefinitie/portal_tegel.md)):

  - Portaal: *beheerportaal-NIEUW*
  - Kolom: *Administratie*
  - Kopregel: *Urensoorten*
  - Dynamisch tegelopschrift:
  - Actie: *getFlexList(SysStandardList,nil,nil,G,beheer_tbsoorturen)*

