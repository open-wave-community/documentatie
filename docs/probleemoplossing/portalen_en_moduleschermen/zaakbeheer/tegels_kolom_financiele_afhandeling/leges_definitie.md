# Leges-definitie

## Trigger

De tegel is een trigger voor het doorkiesscherm naar _Soorten leges en hun berekening_.

- De tegel is alleen zichtbaar voor inlogger wanneer:
  - deze aan hem/haar is toegekend
  - de evaluatie van het _SQL statement onzichtbaar_ bij de tegeldefinitie een waarde ongelijk aan 0 oplevert.
- Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](../../../../instellen_inrichten/portaldefinitie/portal_tegel.md)):

- Portaal: _Zaakbeheer_
- Kolom: _Financiele Afhandeling_
- Kopregel: _Leges-definitie_
- Actie: _getFlexList(SysStandardList,nil,nil,G,beheer_tblegessoort)_
