# IPPC-categorieen

## Trigger

De tegel is een trigger voor de view van mogelijke *IPPC-coderingen* (Integrated Pollution Prevention and Control) bij een inrichting.

- De tegel is alleen zichtbaar voor inlogger wanneer:
  - deze aan hem/haar is toegekend
  - de evaluatie van het *SQL statement onzichtbaar* bij de tegeldefinitie een waarde ongelijk aan 0 oplevert.
- Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](../../../../instellen_inrichten/portaldefinitie/portal_tegel.md)):

- Portaal: *Inrichtingenbeheer*
- Kolom: *Algemeen*
- Vast opschrift: *IPPC-categorieen*
- Actie: *getFlexList(SysStandardList,,,G,beheer_tbmilippccat)*
