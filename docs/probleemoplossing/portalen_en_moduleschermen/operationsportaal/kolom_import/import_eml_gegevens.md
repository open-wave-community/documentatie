# Import EML gegevens

Zie ook [Inlezen EML gegevens](../programmablokken/inlezen_eml.md).

## Trigger

De tegel is een trigger voor de wizard die het inlezen van EML overtredingen regelt.

- De tegel is alleen zichtbaar voor inlogger wanneer:
  - deze aan hem/haar is toegekend
  - de evaluatie van het *SQL statement onzichtbaar* bij de tegeldefinitie een waarde ongelijk aan 0 oplevert.
- Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](../../../../instellen_inrichtenn_inrichten/portaldefinitie/portal_tegel.md)):

- Portaal: *Operations*
- Kolom: *Import*
- Kopregel: *Inlezen EML gegevens*
- Actie: *startWizard(uploadmultiplefiles,-1,,no_uploadfile;inlezenemlgegevens)*
