# REV Json Mallen

## Trigger

De tegel is een trigger voor tonen van het overzicht van de codetabel voor de *REV Json Mallen*. Voor de definitie van de lijst zie beheertabel *tabellen standaardapi* (tbsysstandardtable.dvcode = *beheer_tbrevjsonmallen)*.

- De tegel is alleen zichtbaar voor inlogger wanneer:
    *deze aan hem/haar is toegekend
  - de evaluatie van het *SQL statement onzichtbaar* bij de tegeldefinitie een waarde ongelijk aan 0 oplevert.
- Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](../../../../instellen_inrichten/portaldefinitie/portal_tegel.md)):

- Portaal: *Beheer*
- Kolom: *Inrichtingen*
- Kopregel: *REV Json Mallen*
- Actie: *getFlexList(SysStandardList,nil,nil,G,beheer_tbrevjsonmallen)*
