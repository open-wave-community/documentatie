# Sectie Aanmaakmappen

Hieronder de instellingen uit de [configuratietabel](README.md) configuratietabel (tbinitialisatie) van de _Sectie: Aanmaakmappen_ gerangschikt op item. Deze instellingen zijn alleen van belang indien gebruik gemaakt wordt van de fileserver of van een DMS via CMIS voor het opslaan en ophalen van documenten.

- Fileserver indien _Sectie: Documenten en Item: ophalenviafileserver_ is aangevinkt.\
- DMS via CMIS indien _Sectie: Documenten en Item: ophalenviadms_ is aangevinkt en kolom _Tekst_ van _Sectie: KoppelingDOCNAARDMS Item: methode_ de waarde 'CMIS 1.0' heeft.

## Items Configuratietabel

| Item          | Kolom  | Beschrijving                                                                                |
|---------------|--------|---------------------------------------------------------------------------------------------|
| `Bouw_`       | Getal1 | Het `_` in de itemnaam kan vrij gevuld worden met waarden als _basis_ of _nagekomen_ of _adviezen_, zolang de itemnaam maar begint met _Bouw_. Er kunnen dus meerdere regels zijn waarvan de itemnaam begint met _Bouw_. |
|               |        | Indien in _Getal1_ een '4' voorkomt dus bijvoorbeeld 4 of 14 of 43, dan beschouwt het programma de kolom _Tekst_ (en bij CMIS de kolom _Info_): |
|               |        | Als een map (en ook alle bestaande submappen daarachter) waarnaartoe geüpload kan worden vanuit het detailscherm van een bouw/sloopzaak, mits de instelling _Sectie: Documenten en Item: Autorisatiemappen_ NIET is aangevinkt |
|               |        | Als een map (en ook alle submappen daarachter) waarvandaan documenten kunnen worden opgehaald met de documentenknop op het portalscherm en in het detailscherm van een een bouw/sloopzaak, mits de instelling _Sectie: Documenten en Item: Autorisatiemappen_ NIET is aangevinkt |
|               |        | Als een map die wordt aangemaakt automatisch bij het creëren van een nieuwe bouw/sloopzaak mits de instelling _Sectie: Documenten Item: AutomAanmaakFileservermappen_ aangevinkt is, behalve als de _Tekst_ een '%substring%' %adviesnr%' of `%inspnr%` of `%bezwaarnr%` bevat |
|               |        | Indien in _Getal1_ een '1' voorkomt (dus bijvoorbeeld 1 of 12 of 31) of een '2' of een '5', dan beschouwt het programma de kolom _Tekst_ (en bij CMIS de kolom _Info_): |
|               |        | Als een map (en ook alle bestaande submappen daarachter) waarnaartoe geüpload kan worden vanuit het advies (1)- c.q. inspectie(2)- c.q. bezwaarberoepscherm(5) van een bouw/sloopzaak, mits de instelling _Sectie: Documenten en Item: Autorisatiemappen_ NIET is aangevinkt |
|               |        | Als een map (en ook alle submappen daarachter) waarvandaan documenten kunnen worden opgehaald met de documentenknop in het advies- c.q. inspectie- c.q. bezwaarberoepscherm van een een bouw/sloopzaak, mits de instelling _Sectie: Documenten en Item: Autorisatiemappen_ NIET is aangevinkt |
|               |        | Als een map die wordt aangemaakt automatisch bij het creëren van een nieuwe bouw/sloopzaak mits de instelling _Sectie: Documenten Item: AutomAanmaakFileservermappen_ aangevinkt is, behalve als de _Tekst_ een `%bezwaarnr%` `%adviesnr%` of `%inspnr%` of `%bezwaarnr%` bevat |
|               | Getal2 | Indien de instelling _Sectie: Documenten en Item: SpecialeUploadMappen_ aangevinkt is, dan geldt de extra restrictie bij het uploaden van documenten vanuit een bouw/sloop zaak dat het programma alleen kijkt naar de mappen (de kolom _Tekst_) waarin een '2' voorkomt in _Getal2_ (dus bijvoorbeeld _Getal2_ = 2 of 21) |
|               | Tekst  | Een map op de fileshare waarnaartoe kan worden geüpload of gedownload conform de instellingen bij _Getal1_ en _Getal2_ vanuit bouw/sloopzaken. De map moet een submap zijn van de documentroot (_Sectie: Documenten Item: documentroot_). In de map kunnen variabelen zijn opgenomen, die tijdens de up-of download worden vervangen: |
|               |        | `%zaakjaar%` door het jaar (jjjj) van de begindatum zaak, advies, bezwaarberoep of inspectie |
|               |        | `%zaakjaar%` door de jaarmaand (jjjjmm) van de begindatum zaak, advies, bezwaarberoep of inspectie |
|               |        | `%zaaknr%` met de wavezaakcode van de bouwsloopzaak                                         |
|               |        | `%inspnr%` met de wavezaakcode van de inspectiekaart (dus alleen als _Getal1_ een 2 bevat)  |
|               |        | `%adviesnr%` met de wavezaakcode van de advieskaart (dus alleen als _Getal1_ een 1 bevat)   |
|               |        | `%bezwaarnr%` met de wavezaakcode van de bezwaarberoepkaart (dus alleen als _Getal1_ een 5 bevat) |
|               | Info   | Een map op in het DMS die via CMIS benaderd kan worden waarnaartoe kan worden geüpload of gedownload conform de instellingen bij _Getal1_ en _Getal2_ vanuit bouw/sloopzaken. In de map kunnen variabelen zijn opgenomen, die tijdens de up-of download worden vervangen: |
|               |        | `%zaakjaar%` door het jaar (jjjj) van de begindatum zaak, advies, bezwaarberoep of inspectie |
|               |        | `%zaakjaar%` door de jaarmaand (jjjjmm) van de begindatum zaak, advies, bezwaarberoep of inspectie |
|               |        | `%zaaknr%` met de wavezaakcode van de bouwsloopzaak                                         |
|               |        | `%inspnr%` met de wavezaakcode van de inspectiekaart (dus alleen als _Getal1_ een 2 bevat)  |
|               |        | `%adviesnr%` met de wavezaakcode van de advieskaart (dus alleen als _Getal1_ een 1 bevat)   |
|               |        | `%bezwaarnr%` met de wavezaakcode van de bezwaarberoepkaart (dus alleen als _Getal1_ een 5 bevat) |
| `Handhaving_` | Getal1 | Het `_` in de itemnaam kan vrij gevuld worden met waarden als _basis_ of _nagekomen_ of _adviezen_, zolang de itemnaam maar begint met _Handhaving_. Er kunnen dus meerdere regels zijn waarvan de itemnaam begint met `Handhaving_`. |
|               |        | Indien in _Getal1_ een '4' voorkomt dus bijvoorbeeld 4 of 14 of 43, dan beschouwt het programma de kolom _Tekst_ (en bij CMIS de kolom _Info_): |
|               |        | Als een map (en ook alle bestaande submappen daarachter) waarnaartoe geüpload kan worden vanuit het detailscherm van een handhavingszaak, mits de instelling _Sectie: Documenten en item: Autorisatiemappen_ NIET is aangevinkt |
|               |        | Als een map (en ook alle submappen daarachter) waarvandaan documenten kunnen worden opgehaald met de documentenknop op het portalscherm en in het detailscherm van een een handhavingszaak, mits de instelling _Sectie: Documenten en Item: Autorisatiemappen_ NIET is aangevinkt |
|               |        | Als een map die wordt aangemaakt automatisch bij het creëren van een nieuwe handhavingszaak mits de instelling _Sectie: Documenten Item: AutomAanmaakFileservermappen_ aangevinkt is , behalve als de _Tekst_ een substring `%adviesnr%` of `%inspnr%` of `%bezwaarnr%` bevat |
|               |        | Indien in _Getal1_ een '1' voorkomt (dus bijvoorbeeld 1 of 12 of 31) of een '2' of een '5', dan beschouwt het programma de kolom _Tekst_ (en bij CMIS de kolom _Info_): |
|               |        | Als een map (en ook alle bestaande submappen daarachter) waarnaartoe geüpload kan worden vanuit het advies (1)- c.q. inspectie(2)- c.q. bezwaarberoepscherm(5) van een handhavingszaak, mits de instelling _Sectie: Documenten en item: Autorisatiemappen_ NIET is aangevinkt |
|               |        | Als een map (en ook alle submappen daarachter) waarvandaan documenten kunnen worden opgehaald met de documentenknop in het advies- c.q. inspectie- c.q. bezwaarberoepscherm van een een handhavingszaak, mits de instelling _Sectie: Documenten en Item: Autorisatiemappen_ NIET is aangevinkt |
|               |        | Als een map die wordt aangemaakt automatisch bij het creëren van een nieuwe handhavingszaak mits de instelling _Sectie: Documenten Item: AutomAanmaakFileservermappen_ aangevinkt is, behalve als de _Tekst_ een substring `%adviesnr%` of `%inspnr%` of `%bezwaarnr%` bevat |
|               | Getal2 | Indien de instelling _Sectie: Documenten en Item: SpecialeUploadMappen_ aangevinkt is, dan geldt de extra restrictie bij het uploaden van documenten vanuit een handhavingszaak dat het programma alleen kijkt naar de mappen (de kolom _Tekst_) waarin een '2' voorkomt in _Getal2_ (dus bijvoorbeeld _Getal2_ = 2 of 21) |
|               | Tekst  | Een map op de fileshare waarnaartoe kan worden geüpload of gedownload conform de instellingen bij _Getal1_ en _Getal2_ vanuit handhavingszaken. De map moet een submap zijn van de documentroot (_Sectie: Documenten Item: documentroot_). In de map kunnen variabelen zijn opgenomen, die tijdens de up-of download worden vervangen: |
|               |        | `%zaakjaar%` door het jaar (jjjj) van de begindatum zaak, advies, bezwaarberoep of inspectie |
|               |        | `%zaakjaar%` door de jaarmaand (jjjjmm) van de begindatum zaak, advies, bezwaarberoep of inspectie |
|               |        | `%zaaknr%` met de wavezaakcode van de handhavingszaak                                       |
|               |        | `%inspnr%` met de wavezaakcode van de inspectiekaart dus alleen als _Getal1_ een 2 bevat    |
|               |        | `%adviesnr%` met de wavezaakcode van de advieskaart (dus alleen als _Getal1_ een 1 bevat)   |
|               |        | `%bezwaarnr%` met de wavezaakcode van de bezwaarberoepkaart (dus alleen als _Getal1_ een 5 bevat) |
|               | Info   | Een map op in het DMS die via CMIS benaderd kan worden waarnaartoe kan worden geüpload of gedownload conform de instellingen bij _Getal1_ en _Getal2_ vanuit handhavingszaken. In de map kunnen variabelen zijn opgenomen, die tijdens de up-of download worden vervangen: |
|               |        | `%zaakjaar%` door het jaar (jjjj) van de begindatum zaak, advies, bezwaarberoep of inspectie |
|               |        | `%zaakjaar%` door de jaarmaand (jjjjmm) van de begindatum zaak, advies, bezwaarberoep of inspectie |
|               |        | `%zaaknr%` met de wavezaakcode van de handhavingszaak                                       |
|               |        | `%inspnr%` met de wavezaakcode van de inspectiekaart dus alleen als _Getal1_ een 2 bevat    |
|               |        | `%adviesnr%` met de wavezaakcode van de advieskaart (dus alleen als _Getal1_ een 1 bevat)   |
|               |        | `%bezwaarnr%` met de wavezaakcode van de bezwaarberoepkaart (dus alleen als _Getal1_ een 5 bevat) |
| `Horeca_`     | Getal1 | Het `_` in de itemnaam kan vrij gevuld worden met waarden als _basis_ of _nagekomen_ of _adviezen_, zolang de itemnaam maar begint met _Horeca_. Er kunnen dus meerdere regels zijn waarvan de itemnaam begint met _Horeca_ |
|               |        | Indien in _Getal1_ een '4' voorkomt dus bijvoorbeeld 4 of 14 of 43, dan beschouwt het programma de kolom _Tekst_ (en bij CMIS de kolom _Info_): |
|               |        | Als een map (en ook alle bestaande submappen daarachter) waarnaartoe geüpload kan worden vanuit het detailscherm van een horecazaak, mits de instelling _Sectie: Documenten en Item: Autorisatiemappen_ NIET is aangevinkt |
|               |        | Als een map (en ook alle submappen daarachter) waarvandaan documenten kunnen worden opgehaald met de documentenknop op het portalscherm en in het detailscherm van een een horecazaak, mits de instelling _Sectie: Documenten en Item: Autorisatiemappen_ NIET is aangevinkt |
|               |        | Als een map die wordt aangemaakt automatisch bij het creëren van een nieuwe horecazaak mits de instelling _Sectie: Documenten Item: AutomAanmaakFileservermappen_ aangevinkt is, behalve als de _Tekst_ een substring `%adviesnr%` of `%inspnr%` of `%bezwaarnr%` bevat |
|               |        | Indien in _Getal1_ een '1' voorkomt (dus bijvoorbeeld 1 of 12 of 31) of een '2' of een '5', dan beschouwt het programma de kolom _Tekst_ (en bij CMIS de kolom _Info_): |
|               |        | Als een map (en ook alle bestaande submappen daarachter) waarnaartoe geüpload kan worden vanuit het advies (1)- c.q. inspectie(2)- c.q. bezwaarberoepscherm(5) van een horecazaak, mits de instelling _Sectie: Documenten en Item: Autorisatiemappen_ NIET is aangevinkt |
|               |        | Als een map (en ook alle submappen daarachter) waarvandaan documenten kunnen worden opgehaald met de documentenknop in het advies- c.q. inspectie- c.q. bezwaarberoepscherm van een een horecazaak, mits de instelling _Sectie: Documenten en Item: Autorisatiemappen_ NIET is aangevinkt |
|               |        | Als een map die wordt aangemaakt automatisch bij het creëren van een nieuwe horecazaak mits de instelling _Sectie: Documenten Item: AutomAanmaakFileservermappen_ aangevinkt is , behalve als de _Tekst_ een substring `%adviesnr%` of `%inspnr%` of `%bezwaarnr%` bevat |
|               | Getal2 | Indien de instelling _Sectie: Documenten en Item: SpecialeUploadMappen_ aangevinkt is, dan geldt de extra restrictie bij het uploaden van documenten vanuit een horecazaak dat het programma alleen kijkt naar de mappen (de kolom _Tekst_) waarin een '2' voorkomt in _Getal2_ (dus bijvoorbeeld _Getal2_ = 2 of 21) |
|               | Tekst  | Een map op de fileshare waarnaartoe kan worden geüpload of gedownload conform de instellingen bij _Getal1_ en _Getal2_ vanuit horecazaken. De map moet een submap zijn van de documentroot (_Sectie: Documenten Item: documentroot_). In de map kunnen variabelen zijn opgenomen, die tijdens de up-of download worden vervangen: |
|               |        | `%zaakjaar%` door het jaar (jjjj) van de begindatum zaak, advies, bezwaarberoep of inspectie |
|               |        | `%zaakjaar%` door de jaarmaand (jjjjmm) van de begindatum zaak, advies, bezwaarberoep of inspectie |
|               |        | `%zaaknr%` met de wavezaakcode van de horecazaak                                            |
|               |        | `%inspnr%` met de wavezaakcode van de inspectiekaart dus alleen als _Getal1_ een 2 bevat    |
|               |        | `%adviesnr%` met de wavezaakcode van de advieskaart (dus alleen als _Getal1_ een 1 bevat)   |
|               |        | `%bezwaarnr%` met de wavezaakcode van de bezwaarberoepkaart (dus alleen als _Getal1_ een 5 bevat) |
|               | Info   | Een map op in het DMS die via CMIS benaderd kan worden waarnaartoe kan worden geüpload of gedownload conform de instellingen bij _Getal1_ en _Getal2_ vanuit horecazaken. In de map kunnen variabelen zijn opgenomen, die tijdens de up-of download worden vervangen: |
|               |        | `%zaakjaar%` door het jaar (jjjj) van de begindatum zaak, advies, bezwaarberoep of inspectie |
|               |        | `%zaakjaar%` door de jaarmaand (jjjjmm) van de begindatum zaak, advies, bezwaarberoep of inspectie |
|               |        | `%zaaknr%` met de wavezaakcode van de horecazaak                                            |
|               |        | `%inspnr%` met de wavezaakcode van de inspectiekaart (dus alleen als _Getal1_ een 2 bevat)  |
|               |        | `%adviesnr%` met de wavezaakcode van de advieskaart (dus alleen als _Getal1_ een 1 bevat)   |
|               |        | `%bezwaarnr%` met de wavezaakcode van de bezwaarberoepkaart (dus alleen als _Getal1_ een 5 bevat) |
| `Info_`       | Getal1 | Het `_` in de itemnaam kan vrij gevuld worden met waarden als _basis_ of _nagekomen_ of _adviezen_, zolang de itemnaam maar begint met _Info_. Er kunnen dus meerdere regels zijn waarvan de itemnaam begint met _Info_ |
|               |        | Indien in _Getal1_ een '4' voorkomt dus bijvoorbeeld 4 of 14 of 43, dan beschouwt het programma de kolom _Tekst_ (en bij CMIS de kolom _Info_): |
|               |        | Als een map (en ook alle bestaande submappen daarachter) waarnaartoe geüpload kan worden vanuit het detailscherm van een infoaanvraag, mits de instelling _Sectie: Documenten en Item: Autorisatiemappen_ NIET is aangevinkt |
|               |        | Als een map (en ook alle submappen daarachter) waarvandaan documenten kunnen worden opgehaald met de documentenknop op het portalscherm en in het detailscherm van een een infoaanvraag, mits de instelling _Sectie: Documenten en Item: Autorisatiemappen_ NIET is aangevinkt |
|               |        | Als een map die wordt aangemaakt automatisch bij het creëren van een nieuwe infoaanvraag mits de instelling _Sectie: Documenten Item: AutomAanmaakFileservermappen_ aangevinkt is, behalve als de _Tekst_ een substring `%adviesnr%` of `%inspnr%` of `%bezwaarnr%` bevat |
|               |        | Indien in _Getal1_ een '1' voorkomt (dus bijvoorbeeld 1 of 12 of 31), dan beschouwt het programma de kolom _Tekst_ (en bij CMIS de kolom _Info_): |
|               |        | Als een map (en ook alle bestaande submappen daarachter) waarnaartoe geüpload kan worden vanuit het adviesscherm(5) van een infoaanvraagzaak, mits de instelling _Sectie: Documenten en Item: Autorisatiemappen_ NIET is aangevinkt |
|               |        | Als een map (en ook alle submappen daarachter) waarvandaan documenten kunnen worden opgehaald met de documentenknop in het adviesscherm van een een infoaanvraag, mits de instelling _Sectie: Documenten en Item: Autorisatiemappen_ NIET is aangevinkt |
|               |        | Als een map die wordt aangemaakt automatisch bij het creëren van een nieuwe infoaanvraagzaak mits de instelling _Sectie: Documenten Item: AutomAanmaakFileservermappen_ aangevinkt is, behalve als de _Tekst_ een substring `%adviesnr%` of `%inspnr%` of `%bezwaarnr%` bevat |
|               | Getal2 | Indien de instelling _Sectie: Documenten en Item: SpecialeUploadMappen_ aangevinkt is, dan geldt de extra restrictie bij het uploaden van documenten vanuit een infoaanvraag dat het programma alleen kijkt naar de mappen (de kolom _Tekst_) waarin een '2' voorkomt in _Getal2_ (dus bijvoorbeeld _Getal2_ = 2 of 21) |
|               | Tekst  | Een map op de fileshare waarnaartoe kan worden geüpload of gedownload conform de instellingen bij _Getal1_ en _Getal2_ vanuit infoaanvragen. De map moet een submap zijn van de documentroot (_Sectie: Documenten Item: documentroot_). In de map kunnen variabelen zijn opgenomen, die tijdens de up-of download worden vervangen: |
|               |        | `%zaakjaar%` door het jaar (jjjj) van de begindatum zaak of advies                          |
|               |        | `%zaakjaar%` door de jaarmaand (jjjjmm) van de begindatum zaak of advies                    |
|               |        | `%zaaknr%` met de wavezaakcode van de infoaanvraag `%adviesnr%` met de wavezaakcode van de advieskaart dus alleen als _Getal1_ een 1 bevat |
|               | Info   | Een map op in het DMS die via CMIS benaderd kan worden waarnaartoe kan worden geüpload of gedownload conform de instellingen bij _Getal1_ en _Getal2_ vanuit infoaanvragen. In de map kunnen variabelen zijn opgenomen, die tijdens de up-of download worden vervangen: |
|               |        | `%zaakjaar%` door het jaar (jjjj) van de begindatum zaak of advies                          |
|               |        | `%zaakjaar%` door de jaarmaand (jjjjmm) van de begindatum zaak of advies                    |
|               |        | `%zaaknr%` met de wavezaakcode van de infoaanvraag                                          |
|               |        | `%adviesnr%` met de wavezaakcode van de advieskaart (dus alleen als _Getal1_ een 1 bevat)   |
| Inrichting`*` | Getal1 | Het `*` in de itemnaam kan vrij gevuld worden met waarden als _basis_ of _archief_ of _rapporten_, zolang de itemnaam maar begint met _Inrichting_. Er kunnen dus meerdere regels zijn waarvan de itemnaam begint met _Inrichting_ |
|               |        | Indien in _Getal1_ een '4' voorkomt (dus bijvoorbeeld 4 of 14 of 43), dan beschouwt het programma de kolom _Tekst_ (en bij CMIS de kolom _Info_): |
|               |        | Als een map (en ook alle bestaande submappen daarachter) waarnaartoe geüpload kan worden vanuit het detailscherm van een inrichting, mits de instelling _Sectie: Documenten en Item: Autorisatiemappen_ NIET is aangevinkt |
|               |        | Als een map (en ook alle submappen daarachter) waarvandaan documenten kunnen worden opgehaald met de documentenknop op het portalscherm en in het detailscherm van een een inrichting, mits de instelling _Sectie: Documenten en Item: Autorisatiemappen_ NIET is aangevinkt |
|               |        | Als een map die wordt aangemaakt automatisch bij het creëren van een nieuwe inrichting mits de instelling _Sectie: Documenten Item: AutomAanmaakFileservermappen_ aangevinkt is , behalve als de _Tekst_ een substring `%adviesnr%` of `%inspnr%` of `%bezwaarnr%` bevat |
|               |        | Indien in _Getal1_ een '2' voorkomt (dus bijvoorbeeld 2 of 12 of 23), dan beschouwt het programma de kolom _Tekst_ (en bij CMIS de kolom _Info_): |
|               |        | Als een map (en ook alle bestaande submappen daarachter) waarnaartoe geüpload kan worden vanuit het inspectiescherm van een inrichting, mits de instelling _Sectie: Documenten en Item: Autorisatiemappen_ NIET is aangevinkt |
|               |        | Als een map (en ook alle submappen daarachter) waarvandaan documenten kunnen worden opgehaald met de documentenknop in het inspectiescherm van een een inrichting, mits de instelling _Sectie: Documenten en Item: Autorisatiemappen_ NIET is aangevinkt |
|               |        | Als een map die wordt aangemaakt automatisch bij het creëren van een nieuwe inrichting mits de instelling _Sectie: Documenten Item: AutomAanmaakFileservermappen_ aangevinkt is, behalve als de _Tekst_ een substring `%adviesnr%` of `%inspnr%` of `%bezwaarnr%` bevat |
|               | Getal2 | Indien de instelling _Sectie: Documenten en Item: SpecialeUploadMappen_ aangevinkt is, dan geldt de extra restrictie bij het uploaden van documenten vanuit een inrichting dat het programma alleen kijkt naar de mappen (de kolom _Tekst_) waarin een '2' voorkomt in _Getal2_ (dus bijvoorbeeld _Getal2_ = 2 of 21) |
|               | Tekst  | Een map op de fileshare waarnaartoe kan worden geüpload of gedownload conform de instellingen bij _Getal1_ en _Getal2_ vanuit inrichtingen. De map moet een submap zijn van de documentroot (_Sectie: Documenten Item: documentroot_). In de map kunnen variabelen zijn opgenomen, die tijdens de up-of download worden vervangen: |
|               |        | `%zaakjaar%` door het jaar (jjjj) van de begindatum inspectie (dus alleen als _Getal1_ een 2 bevat) |
|               |        | `%zaakjaar%` door de jaarmaand (jjjjmm) van de begindatum inspectie (dus alleen als _Getal1_ een 2 bevat) |
|               |        | `%zaaknr%` met de wavezaakcode van de inrichting                                            |
|               |        | `%inspnr%` met de wavezaakcode van de inspectiekaart (dus alleen als _Getal1_ een 2 bevat)  |
|               | Info   | Een map op in het DMS die via CMIS benaderd kan worden waarnaartoe kan worden geüpload of gedownload conform de instellingen bij _Getal1_ en _Getal2_ vanuit inrichtingen. In de map kunnen variabelen zijn opgenomen, die tijdens de up-of download worden vervangen: |
|               |        | `%zaakjaar%` door het jaar (jjjj) van de begindatum inspectie (dus alleen als _Getal1_ een 2 bevat) |
|               |        | `%zaakjaar%` door de jaarmaand (jjjjmm) van de begindatum inspectie (dus alleen als _Getal1_ een 2 bevat) |
|               |        | `%zaaknr%` met de wavezaakcode van de inrichting                                            |
| `MilGebr_`    | Getal1 | Het `_` in de itemnaam kan vrij gevuld worden met waarden als \_basis_of _nagekomen_ of _adviezen_, zolang de itemnaam maar begint met `MilGebr_`. Er kunnen dus meerdere regels zijn waarvan de itemnaam begint met `MilGebr_`. |
|               |        | Indien in _Getal1_ een '4' voorkomt (dus bijvoorbeeld 4 of 14 of 43), dan beschouwt het programma de kolom _Tekst_ (en bij CMIS de kolom _Info_): |
|               |        | Als een map (en ook alle bestaande submappen daarachter) waarnaartoe geüpload kan worden vanuit het detailscherm van een milieu/gebruikzaak, mits de instelling _Sectie: Documenten en Item: Autorisatiemappen_ NIET is aangevinkt |
|               |        | Als een map (en ook alle submappen daarachter) waarvandaan documenten kunnen worden opgehaald met de documentenknop op het portalscherm en in het detailscherm van een een milieu/gebruik zaak, mits de instelling _Sectie: Documenten en Item: Autorisatiemappen_ NIET is aangevinkt |
|               |        | Als een map die wordt aangemaakt automatisch bij het creëren van een nieuwe milieu/gebruik zaak mits de instelling _Sectie: Documenten Item: AutomAanmaakFileservermappen_ aangevinkt is , behalve als de _Tekst_ een substring `%adviesnr%` of `%inspnr%` of `%bezwaarnr%` bevat |
|               |        | Indien in _Getal1_ een '1' voorkomt (dus bijvoorbeeld 1 of 12 of 31) of een '5', dan beschouwt het programma de kolom _Tekst_ (en bij CMIS de kolom _Info_): |
|               |        | Als een map (en ook alle bestaande submappen daarachter) waarnaartoe geüpload kan worden vanuit het advies (1)- c.q. bezwaarberoepscherm(5) van een milieu/gebruik zaak, mits de instelling _Sectie: Documenten en Item: Autorisatiemappen_ NIET is aangevinkt |
|               |        | Als een map (en ook alle submappen daarachter) waarvandaan documenten kunnen worden opgehaald met de documentenknop in het advies- c.q. bezwaarberoepscherm van een een milieu/gebruikzaak, mits de instelling _Sectie: Documenten en Item: Autorisatiemappen_ NIET is aangevinkt |
|               |        | Als een map die wordt aangemaakt automatisch bij het creëren van een nieuwe milieu/gebruik zaak mits de instelling _Sectie: Documenten Item: AutomAanmaakFileservermappen_ aangevinkt is, behalve als de _Tekst_ een substring `%adviesnr%` of `%inspnr%` of `%bezwaarnr%` bevat |
|               | Getal2 | Indien de instelling _Sectie: Documenten en Item: SpecialeUploadMappen_ aangevinkt is, dan geldt de extra restrictie bij het uploaden van documenten vanuit een milieu/gebruik zaak dat het programma alleen kijkt naar de mappen (de kolom _Tekst_) waarin een '2' voorkomt in _Getal2_ (dus bijvoorbeeld _Getal2_ = 2 of 21) |
|               | Tekst  | Een map op de fileshare waarnaartoe kan worden geüpload of gedownload conform de instellingen bij _Getal1_ en _Getal2_ vanuit milieu/gebruik zaken. De map moet een submap zijn van de documentroot (_Sectie: Documenten Item: documentroot_). In de map kunnen variabelen zijn opgenomen, die tijdens de up-of download worden vervangen: |
|               |        | `%zaakjaar%` door het jaar (jjjj) van de begindatum zaak, advies of bezwaarberoep           |
|               |        | `%zaakjaar%` door de jaarmaand (jjjjmm) van de begindatum zaak, advies of bezwaarberoep     |
|               |        | `%zaaknr%` met de wavezaakcode van de milieu/gebruik zaak                                   |
|               |        | `%adviesnr%` met de wavezaakcode van de advieskaart (dus alleen als _Getal1_ een 1 bevat)   |
|               |        | `%bezwaarnr%` met de wavezaakcode van de bezwaarberoepkaart (dus alleen als _Getal1_ een 5 bevat) |
|               | Info   | Een map op in het DMS die via CMIS benaderd kan worden waarnaartoe kan worden geüpload of gedownload conform de instellingen bij _Getal1_ en _Getal2_ vanuit milieu/gebruik zaken. In de map kunnen variabelen zijn opgenomen, die tijdens de up-of download worden vervangen: |
|               |        | `%zaakjaar%` door het jaar (jjjj) van de begindatum zaak, advies of bezwaarberoep           |
|               |        | `%zaakjaar%` door de jaarmaand (jjjjmm) van de begindatum zaak, advies of bezwaarberoep     |
|               |        | `%zaaknr%` met de wavezaakcode van de milieu/gebruik zaak                                   |
|               |        | `%adviesnr%` met de wavezaakcode van de advieskaart (dus alleen als _Getal1_ een 1 bevat)   |
|               |        | `%bezwaarnr%` met de wavezaakcode van de bezwaarberoepkaart (dus alleen als _Getal1_ een 5 bevat) |
| Omgeving`*`   | Getal1 | Het `*` in de itemnaam kan vrij gevuld worden met waarden als _basis_ of _nagekomen_ of _adviezen_, zolang de itemnaam maar begint met _Omgeving_. Er kunnen dus meerdere regels zijn waarvan de itemnaam begint met _Omgeving_ |
|               |        | Indien in _Getal1_ een '4' voorkomt (dus bijvoorbeeld 4 of 14 of 43), dan beschouwt het programma de kolom _Tekst_ (en bij CMIS de kolom _Info_): |
|               |        | Als een map (en ook alle bestaande submappen daarachter) waarnaartoe geüpload kan worden vanuit het detailscherm van een omgevingszaak, mits de instelling _Sectie: Documenten en Item: Autorisatiemappen_ NIET is aangevinkt |
|               |        | Als een map (en ook alle submappen daarachter) waarvandaan documenten kunnen worden opgehaald met de documentenknop op het portalscherm en in het detailscherm van een een omgevingszaak, mits de instelling _Sectie: Documenten en Item: Autorisatiemappen_ NIET is aangevinkt |
|               |        | Als een map die wordt aangemaakt automatisch bij het creëren van een nieuwe omgevingszaak mits de instelling _Sectie: Documenten Item: AutomAanmaakFileservermappen_ aangevinkt is, behalve als de _Tekst_ een substring `%adviesnr%` of `%inspnr%` of `%bezwaarnr%` bevat |
|               |        | Indien in _Getal1_ een '1' voorkomt (dus bijvoorbeeld 1 of 12 of 31) of een '2' of een '5', dan beschouwt het programma de kolom _Tekst_ (en bij CMIS de kolom _Info_): |
|               |        | Als een map (en ook alle bestaande submappen daarachter) waarnaartoe geüpload kan worden vanuit het advies (1)- c.q. inspectie(2)- c.q. bezwaarberoepscherm(5) van een omgevingszaak, mits de instelling _Sectie: Documenten en Item: Autorisatiemappen_ NIET is aangevinkt |
|               |        | Als een map (en ook alle submappen daarachter) waarvandaan documenten kunnen worden opgehaald met de documentenknop in het advies- c.q. inspectie- c.q. bezwaarberoepscherm van een een omgevingszaak, mits de instelling _Sectie: Documenten en Item: Autorisatiemappen_ NIET is aangevinkt |
|               |        | Als een map die wordt aangemaakt automatisch bij het creëren van een nieuwe omgevingszaak mits de instelling _Sectie: Documenten Item: AutomAanmaakFileservermappen_ aangevinkt is, behalve als de _Tekst_ een substring `%adviesnr%` of `%inspnr%` of `%bezwaarnr%` bevat |
|               | Getal2 | Indien de instelling _Sectie: Documenten en Item: SpecialeUploadMappen_ aangevinkt is, dan geldt de extra restrictie bij het uploaden van documenten vanuit een omgevingszaak dat het programma alleen kijkt naar de mappen (de kolom _Tekst_) waarin een '2' voorkomt in _Getal2_ (dus bijvoorbeeld _Getal2_ = 2 of 21) Indien _Getal2_ = 1 dan is dit de map waarop het automatisch proces van plaatsen OLO-bijlagen op de fileshare terechtkomt (er mag maar één map zijn met _Getal2_ =1) |
|               | Tekst  | Een map op de fileshare waarnaartoe kan worden geüpload of gedownload conform de instellingen bij _Getal1_ en _Getal2_ vanuit omgevingszaken. De map moet een submap zijn van de documentroot (_Sectie: Documenten Item: documentroot_). In de map kunnen variabelen zijn opgenomen, die tijdens de up-of download worden vervangen: |
|               |        | `%zaakjaar%` door het jaar (jjjj) van de begindatum zaak, advies, bezwaarberoep of inspectie |
|               |        | `%zaakjaar%` door de jaarmaand (jjjjmm) van de begindatum zaak, advies, bezwaarberoep of inspectie |
|               |        | `%zaaknr%` met de wavezaakcode van de omgevingszaak                                         |
|               |        | `%inspnr%` met de wavezaakcode van de inspectiekaart (dus alleen als _Getal1_ een 2 bevat)  |
|               |        | `%adviesnr%` met de wavezaakcode van de advieskaart (dus alleen als _Getal1_ een 1 bevat)   |
|               |        | `%bezwaarnr%` met de wavezaakcode van de bezwaarberoepkaart (dus alleen als _Getal1_ een 5 bevat) |
|               | Info   | Een map op in het DMS die via CMIS benaderd kan worden waarnaartoe kan worden geüpload of gedownload conform de instellingen bij _Getal1_ en _Getal2_ vanuit omgevingszaken. In de map kunnen variabelen zijn opgenomen, die tijdens de up-of download worden vervangen: |
|               |        | `%zaakjaar%` door het jaar (jjjj) van de begindatum zaak, advies, bezwaarberoep of inspectie |
|               |        | `%zaakjaar%` door de jaarmaand (jjjjmm) van de begindatum zaak, advies, bezwaarberoep of inspectie |
|               |        | `%zaaknr%` met de wavezaakcode van de omgevingszaak                                         |
|               |        | `%inspnr%` met de wavezaakcode van de inspectiekaart (dus alleen als _Getal1_ een 2 bevat)  |
|               |        | `%adviesnr%` met de wavezaakcode van de advieskaart (dus alleen als _Getal1_ een 1 bevat)   |
|               |        | `%bezwaarnr%` met de wavezaakcode van de bezwaarberoepkaart (dus alleen als _Getal1_ een 5 bevat) |
| Overige `*`   | Getal1 | Het `*` in de itemnaam kan vrij gevuld worden met waarden als _basis_ of _nagekomen_ of _adviezen_, zolang de itemnaam maar begint met _Overige_. Er kunnen dus meerdere regels zijn waarvan de itemnaam begint met _Overige_ |
|               |        | Indien in _Getal1_ een '4' voorkomt (dus bijvoorbeeld 4 of 14 of 43), dan beschouwt het programma de kolom _Tekst_ (en bij CMIS de kolom _Info_): |
|               |        | Als een map (en ook alle bestaande submappen daarachter) waarnaartoe geüpload kan worden vanuit het detailscherm van een APV/Overige-zaak, mits de instelling _Sectie: Documenten en Item: Autorisatiemappen_ NIET is aangevinkt |
|               |        | Als een map (en ook alle submappen daarachter) waarvandaan documenten kunnen worden opgehaald met de documentenknop op het portalscherm en in het detailscherm van een een APV/Overige-zaak, mits de instelling _Sectie: Documenten en Item: Autorisatiemappen_ NIET is aangevinkt |
|               |        | Als een map die wordt aangemaakt automatisch bij het creëren van een nieuwe bouw/sloopzaak mits de instelling _Sectie: Documenten Item: AutomAanmaakFileservermappen_ aangevinkt is , behalve als de _Tekst_ een substring `%adviesnr%` of `%inspnr%` of `%bezwaarnr%` bevat |
|               |        | Indien in _Getal1_ een '1' voorkomt (dus bijvoorbeeld 1 of 12 of 31) of een '2' of een '5', dan beschouwt het programma de kolom _Tekst_ (en bij CMIS de kolom _Info_): |
|               |        | Als een map (en ook alle bestaande submappen daarachter) waarnaartoe geüpload kan worden vanuit het advies (1)- c.q. inspectie(2)- c.q. bezwaarberoepscherm(5) van een APV/Overige-zaak, mits de instelling _Sectie: Documenten en Item: Autorisatiemappen_ NIET is aangevinkt |
|               |        | Als een map (en ook alle submappen daarachter) waarvandaan documenten kunnen worden opgehaald met de documentenknop in het advies- c.q. inspectie- c.q. bezwaarberoepscherm van een een APV/Overige-zaak, mits de instelling _Sectie: Documenten en Item: Autorisatiemappen_ NIET is aangevinkt |
|               |        | Als een map die wordt aangemaakt automatisch bij het creëren van een nieuwe APV/Overige-zaak mits de instelling _Sectie: Documenten Item: AutomAanmaakFileservermappen_ aangevinkt is , behalve als de _Tekst_ een substring `%adviesnr%` of `%inspnr%` of `%bezwaarnr%` bevat |
|               | Getal2 | Indien de instelling _Sectie: Documenten en Item: SpecialeUploadMappen_ aangevinkt is, dan geldt de extra restrictie bij het uploaden van documenten vanuit een APV/Overige-zaak dat het programma alleen kijkt naar de mappen (de kolom _Tekst_) waarin een '2' voorkomt in _Getal2_ (dus bijvoorbeeld _Getal2_ = 2 of 21) |
|               | Tekst  | Een map op de fileshare waarnaartoe kan worden geüpload of gedownload conform de instellingen bij _Getal1_ en _Getal2_ vanuit APV/Overige-zaken. De map moet een submap zijn van de documentroot (_Sectie: Documenten Item: documentroot_). In de map kunnen variabelen zijn opgenomen, die tijdens de up-of download worden vervangen: |
|               |        | `%zaakjaar%` door het jaar (jjjj) van de begindatum zaak, advies, bezwaarberoep of inspectie |
|               |        | `%zaakjaar%` door de jaarmaand (jjjjmm) van de begindatum zaak, advies, bezwaarberoep of inspectie |
|               |        | `%zaaknr%` met de wavezaakcode van de APV/Overige-zaak                                      |
|               |        | `%inspnr%` met de wavezaakcode van de inspectiekaart (dus alleen als _Getal1_ een 2 bevat)  |
|               |        | `%adviesnr%` met de wavezaakcode van de advieskaart (dus alleen als _Getal1_ een 1 bevat)   |
|               |        | `%bezwaarnr%` met de wavezaakcode van de bezwaarberoepkaart (dus alleen als _Getal1_ een 5 bevat) |
|               | Info   | Een map op in het DMS die via CMIS benaderd kan worden waarnaartoe kan worden geüpload of gedownload conform de instellingen bij _Getal1_ en _Getal2_ vanuit APV/Overige-zaken. In de map kunnen variabelen zijn opgenomen, die tijdens de up-of download worden vervangen: |
|               |        | `%zaakjaar%` door het jaar (jjjj) van de begindatum zaak, advies, bezwaarberoep of inspectie |
|               |        | `%zaakjaar%` door de jaarmaand (jjjjmm) van de begindatum zaak, advies, bezwaarberoep of inspectie |
|               |        | `%zaaknr%` met de wavezaakcode van de APV/Overige-zaak                                      |
|               |        | `%inspnr%` met de wavezaakcode van de inspectiekaart (dus alleen als _Getal1_ een 2 bevat)  |
|               |        | `%adviesnr%` met de wavezaakcode van de advieskaart (dus alleen als _Getal1_ een 1 bevat)   |
|               |        | `%bezwaarnr%` met de wavezaakcode van de bezwaarberoepkaart (dus alleen als _Getal1_ een 5 bevat) |
