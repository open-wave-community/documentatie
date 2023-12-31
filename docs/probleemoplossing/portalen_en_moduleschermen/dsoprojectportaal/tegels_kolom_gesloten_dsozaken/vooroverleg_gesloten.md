# Vooroverleg (Gesloten)

## Trigger

De tegel is een trigger voor het lijstscherm van het *Afgesloten Vooroverleg* bij een DSO project.

  - De tegel is alleen zichtbaar voor inlogger wanneer:
    - deze aan hem/haar is toegekend
    - de evaluatie van het *SQL statement onzichtbaar* bij de tegeldefinitie een waarde ongelijk aan 0 oplevert:
      - de tegel is zichtbaar als er voor dit DSO project een afgesloten omgevingszaak (besluitdatum is gevuld) is met als DSO verzoekdoel *Vooroverleg* (verzoektype maakt hier niet uit)
  - Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Probleem

Het dynamische opschrift op tegels is niet zichtbaar:

  - indien foutieve queryverwijzing
  - indien query zelf niet correct (zie [Queries](../../../../instellen_inrichten/queries.md))
  - indien inlogger geen recht heeft om query uit te voeren
  - indien de kolom *altijd verversen* (tbportaltiles.dlaltijdrefreshen) op de tegeldefinitie uitgevinkt is.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](../../../../instellen_inrichten/portaldefinitie/portal_tegel.md)):

  -  Portaal: *dsoprojectportaal*
  -  Kolom: *Afgesloten DSO-Zaken*
  -  Kopregel: *Vooroverleg*
  -  Dynamisch tegelopschrift: getTileContent(dso_vooroverleg_gesloten,{id})
  -  Actie: *getFlexList(SysStandardList,tbdsoproject,{id},nil,dso_vooroverleg_gesloten)*
  -  Onzichtbaar indien result van de volgende select 0 is:

```sql
select case when
   (select count(*) from tbomgvergunning
    where dnkeydsoproject = {id}
    and lower(dvdsoverzoekdoel) in (''vooroverleg'', ''conceptverzoek'')
    and ddbesluitdatum is not null) >= 1
  then 1 else 0 end
```

