# Beheerportaal

## LET OP: DEPRECATED sinds 1.28
### Alternatief: de tegels op de nieuwe beheerportalen

  - **Beheerportaal-Nieuw**
  - **Zaakbeheer**
  - **Inrichtingenbeheer**

Wordt aangeroepen door de action: OpenTabPage(#beheer).

Dit portaal is bedoeld voor alle beheerinstellingen, zoals de configuratietabel, de portaldefinitie etc.

## Het scherm ziet er raar uit (al of niet met foutmelding) of reageert niet

  - er zijn geen tegels gedefinieerd onder portalname *Beheer* (Zie [Portal Definitie](../../../instellen_inrichten/portaldefinitie/README.md))
  - alle tegels zijn disabled of onzichtbaar of onzichtbaar_op_conditie
  - geen enkele tegel uit dit portal is toegekend aan een inlogger.

## Het opschrift op een of meer tegels is niet zichtbaar

  - ontbreken vaste tekst bij definitie portaltegel
  - OF fout in dynamische queryverwijzing bij tegeldefinitie:
    - indien foutieve queryverwijzing blijft tegel leeg
    - indien query zelf niet correct is, blijft tegel leeg
    - indien inlogger geen recht heeft om query uit te voeren blijft de tegel ook leeg.

## Relevante pagina's

[Beheerportaal](README.md)

  - [Tegels onder kolom Brontabellen](tegels_onder_kolom_brontabellen/README.md)
  - [Tegels onder kolom Brontabellen II](tegels_onder_kolom_brontabellen_ii/README.md)
  - [Tegels onder kolom Inrichtingen](tegels_onder_kolom_inrichtingen/README.md)
  - [Tegels onder kolom Inrichtingen II](tegels_onder_kolom_inrichtingen_ii/README.md)
  - [Tegels onder kolom Instellingen](tegels_onder_kolom_instellingen/README.md)
  - [Tegels onder kolom Instellingen II](tegels_onder_kolom_instellingen_ii/README.md)
  - [Tegels onder kolom Medewerkers](tegels_onder_kolom_medewerkers/README.md)

