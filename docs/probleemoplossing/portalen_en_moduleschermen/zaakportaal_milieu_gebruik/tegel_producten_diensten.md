# Tegel Producten/Diensten

## Trigger

De tegel is een trigger voor het lijstscherm van _Producten/Diensten_ bij een Milieu/Gebruikszaak (zie: [Producten Klanten en Werkpakketten](../../../instellen_inrichten/producten_klanten_werkpakketten.md)).

- De tegel is alleen zichtbaar voor inlogger wanneer:
  - deze aan hem/haar is toegekend
  - de evaluatie van het _SQL statement onzichtbaar_ bij de tegeldefinitie een waarde ongelijk aan 0 oplevert. In dit geval betekent dat dat de instelling _Sectie: Product/Dienst Item: Milieu/Gebruik_ aangevinkt moet zijn en dat _Getal1_ de waarde 1 heeft (zie hieronder bij SQL-conditie).
- Een tegel is disabled indien zo aangevinkt bij de tegeldefinitie.

## Probleem

Het dynamische opschrift op tegels is niet zichtbaar:

- indien foutieve queryverwijzing (codering _milieugebruik_producten/Diensten_)
- indien query zelf niet correct (zie [Queries](../../../instellen_inrichten/queries.md))
- indien inlogger geen recht heeft om query uit te voeren.

## Tegeldefinitie

De tegel is standaard als volgt gedefinieerd ([Portal Tegeldefinitie](../../../instellen_inrichten/portaldefinitie/portal_tegel.md)):

- Portaal: _milieugebruikdetail_
- Kolom: _Overig_
- Kopregel: _Producten/diensten_
- Dynamisch tegelopschrift: _getTileContent(milieugebruik_producten/diensten,{id})_
- Actie: _getFlexList(SysStandardList,tbmilvergunningen,{id},nil,milieugebruik_producten/diensten)_
- SQL:

```sql
select case when d1logic = 'T' and dfnumber1 = 1 then 1 else 0 end
  from tbinitialisatie
  where upper(dvsectie) = 'PRODUCT/DIENST'
  and UPPER(dvitem) = 'MILIEU/GEBRUIK'
```

## Bijzonderheden

De kolommen **Werkpakket** en **Klant** zijn alleen muteerbaar indien de instelling _Sectie: Product/Dienst Item: Milieu/Gebruik_ aangevinkt is waarbij **Getal2** ongelijk is aan 1. Indien deze instelling namelijk wel de waarde 1 heeft, dan zijn deze kolommen in de bovenliggende detailkaart van de milieu/gebruik zaak te vullen in het blok **Klant/Wkpt**. Die waardes worden dan vanzelf overgenomen in tbzaakproducten.

De kolom **Product** is vrijelijk te kiezen uit de gedefinieerde producten bij het betreffende zaaktype (beheer: Zaaktypes milieu/gebruik).

Echter wanneer:

- de combinatie klant/werkpakket voorkomt in de beheertabel _Combinaties product/klant/werkpakket_ (tbprodwkpklant)
- en de kolom _Info_ van de instelling _Sectie: Product/Dienst Item: Milieu/Gebruik_ heeft de waarde 'ODR'

kan bij het nieuw opvoeren van een zaakproduct alleen gekozen worden uit de deze rijen van tbprodwkpklant.
