# Werkpaketten

## Trigger

De tegel is een trigger voor een lijst van *Werkpakketten* die een verfijning vormen op de producten/diensten.

* De tegel is alleen zichtbaar voor inlogger wanneer:
  * deze aan hem/haar is toegekend
  * de evaluatie van het *SQL statement onzichtbaar* bij de tegeldefinitie een waarde ongelijk aan 0 oplevert.
* Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](../../../../instellen_inrichten/portaldefinitie/portal_tegel.md)):

* Portaal: *Beheer*
* Kolom: *Brontabellen*
* Kopregel: *Werkpakketten*
* Actie: *getFlexList(SysStandardList,nil,nil,,beheer_tbproductwerkpakketten)*