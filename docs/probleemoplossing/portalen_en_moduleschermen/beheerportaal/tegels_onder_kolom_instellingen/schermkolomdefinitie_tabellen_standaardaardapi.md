# Schermkolomdefinitie tabellen standaard api

## Trigger

De tegel is een trigger naar de lijst met *Schermkolomdefinities* voor lijst-/detailschermen waarnaar wordt verwezen vanuit de tabel *tbsysstandard* (beheertegel: *Tabellen standaardapi*). Het gaat om de set uit vwfrmscreencolumns where dnreportkey is null and lower(dvclassname) = 'sysstandard'.

- De tegel is alleen zichtbaar voor inlogger wanneer:
  - deze aan hem/haar is toegekend
  - de evaluatie van het *SQL statement onzichtbaar* bij de tegeldefinitie een waarde ongelijk aan 0 oplevert.
  - Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](../../../../instellen_inrichten/portaldefinitie/portal_tegel.md)):

- Portaal: *Beheer*
- Kolom: *Instellingen*
- Kopregel: *Schermkolomdefinitie tabellen standaard-api*
- Actie: *getFlexList(SysStandardList,nil,nil,,beheer_tbscreencolumns_tabellenstandapi)*
