# Tegel Overzichtsscherm

## Trigger

De tegel is een trigger voor een detailscherm met het overzicht van de horecaonderneming van de zaak.

  * De tegel is alleen zichtbaar voor inlogger wanneer: 
    * deze aan hem/haar is toegekend 
    * de evaluatie van het *SQL statement onzichtbaar* bij de tegeldefinitie een waarde ongelijk aan 0 oplevert. 
  * Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](/docs/instellen_inrichten/portaldefinitie/portal_tegel.md)):

  * Portaal: *horecadetail*
  * Kolom: *BehandelingProces*
  * Kopregel: *Overzichtsscherm*
  * Actie: *getFlexDetail(SysStandardDetail,{id},horeca_overzichtsscherm)*
