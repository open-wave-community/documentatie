# Inrichting bedrijfsoort

## Trigger

De tegel is een trigger voor tonen van het overzicht van mogelijkheden waarop een inrichting kan worden ingedeeld naar *Bedrijfsoort*.

- De tegel is alleen zichtbaar voor inlogger wanneer:
  - deze aan hem/haar is toegekend
  - de evaluatie van het *SQL statement onzichtbaar* bij de tegeldefinitie een waarde ongelijk aan 0 oplevert.
- Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](../../../../instellen_inrichten/portaldefinitie/portal_tegel.md)):

- Portaal: *Inrichtingenbeheer*
- Kolom: *Algemeen*
- Kopregel: *Inrichting bedrijfsoort*
- Actie: *getFlexList(SysStandardList,nil,nil,G,beheer_tbmilbedrijfsoort)*
