# Medewerkers (alle)

## Trigger

De tegel is een trigger voor een lijst met *Alle medewerkers*, zie [Medewerkers](../../../../instellen_inrichten/medewerkers.md).

* De tegel is alleen zichtbaar voor inlogger wanneer:
  * deze aan hem/haar is toegekend
  * de evaluatie van het *SQL statement onzichtbaar* bij de tegeldefinitie een waarde ongelijk aan 0 oplevert.
* Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](../../../../instellen_inrichten/portaldefinitie/portal_tegel.md)):

* Portaal: [Beheerportaal](../../portalen_en_moduleschermen/beheerportaal.md)
* Kolom: [Tegels onder kolom Medewerkers](tegels_onder_kolom_medewerkers/README.md)
* Kopregel: *Medewerkers (alle)*
* Actie: *getFlexList(TBMEDEWERKERS,nil,nil,1,nil)*
