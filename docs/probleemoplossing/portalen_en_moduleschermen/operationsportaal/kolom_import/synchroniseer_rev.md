# REV Synchronisatie

Zie [REV-synchroniseren](../programmablokken/rev_synchroniseren.md)

## Trigger

De tegel is een trigger voor de lijst van de te synchroniseren data uit het REV (register externe veiligheid)

* De tegel is alleen zichtbaar voor inlogger wanneer:
  * deze aan hem/haar is toegekend
  * de evaluatie van het *SQL statement onzichtbaar* bij de tegeldefinitie een waarde ongelijk aan 0 oplevert.
* Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](../../../../instellen_inrichtenn_inrichten/portaldefinitie/portal_tegel.md)):

* Portaal: *Operations*
* Kolom: *Import*
* Kopregel: *REV synchronisatie*
* Actie: *getFlexList(SysStandardList,nil,nil,,operations_revsynchroniseer)*
