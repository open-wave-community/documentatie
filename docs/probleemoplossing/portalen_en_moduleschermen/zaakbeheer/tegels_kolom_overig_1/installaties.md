# Installaties

## Trigger

De tegel is een trigger voor een lijst met mogelijke *Brandweer-installaties*.

* De tegel is alleen zichtbaar voor inlogger wanneer:
  * deze aan hem/haar is toegekend
  * de evaluatie van het *SQL statement onzichtbaar* bij de tegeldefinitie een waarde ongelijk aan 0 oplevert.
* Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](/docs/instellen_inrichten/portaldefinitie/portal_tegel.md)):

* Portaal: *Zaakbeheer*
* Kolom: *Overig 1*
* Kopregel: *Installaties*
* Actie: *getFlexList(SysStandardList,nil,nil,G,beheer_tbbwinstallaties)*