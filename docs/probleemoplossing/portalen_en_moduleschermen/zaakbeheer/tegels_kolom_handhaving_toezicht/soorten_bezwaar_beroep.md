# Soorten bezwaar/beroep

## Trigger

De tegel is een trigger voor het doorkiesscherm naar naar een tabel met _Soorten bezwaar/beroep_.

- De tegel is alleen zichtbaar voor inlogger wanneer:
  - deze aan hem/haar is toegekend
  - de evaluatie van het _SQL statement onzichtbaar_ bij de tegeldefinitie een waarde ongelijk aan 0 oplevert.
- Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](../../../../instellen_inrichten/portaldefinitie/portal_tegel.md)):

- Portaal: _Zaakbeheer_
- Kolom: _Handhaving- en Toezicht_
- Kopregel: _Soorten bezwaar/beroep_
- Actie: _getFlexList(SysStandardList,nil,nil,G,beheer_tbsoortbezwaar)_
