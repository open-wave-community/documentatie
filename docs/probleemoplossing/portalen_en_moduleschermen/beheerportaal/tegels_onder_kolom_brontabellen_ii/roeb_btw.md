# ROEB BTW

## Trigger

De tegel is een trigger voor het tonen van de lijst met *ROEB -btw-percentages* (zie ook [Roeb berekening vastg. kosten](../../../../instellen_inrichten/roeb_berekening_vastg._kosten.md)).

- De tegel is alleen zichtbaar voor inlogger wanneer:
  - deze aan hem/haar is toegekend
  - de evaluatie van het *SQL statement onzichtbaar* bij de tegeldefinitie een waarde ongelijk aan 0 oplevert.
- Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](../../../../instellen_inrichten/portaldefinitie/portal_tegel.md)):

- Portaal: *Beheer*
- Kolom: *Brontabellen II*
- Kopregel: *ROEB BTW*
- Actie: *getFlexList(SysStandardList,nil,nil,nil,beheer_tbroebbtw)*
