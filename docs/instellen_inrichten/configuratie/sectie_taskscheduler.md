# Sectie Taskscheduler

Hieronder de instellingen uit de tabel tbinitialisatie van de _Sectie: Taskscheduler_ gerangschikt op item.

## Items Configuratietabel

| Item                      | Kolom  | Omschrijving                                                                    |
|---------------------------|--------|---------------------------------------------------------------------------------|
| AantalBenBezigHerstelUren | Getal1 | Wanneer een taak uit de taskscheduler langer dan het hier opegegeven aantal uren (defaultwaarde is 12) de status _ben bezig_ heeft (waardoor alle andere taken on hold worden gezet) zal OpenWave automatisch de taak afsluiten en zo weer vrijgeven. Ook _getal1_ van de instelling _sectie: Operations en item: `<de naam van de taak>`_ wordt op null gezet (mits de datum van die instelling ook langer dan het opgegeven aantal uren geleden is). Alleen indien expliciet de waarde 0 is opgegeven voor _AantalBenBezigHerstelUren_ geeft OpenWQave de taak NIET automatisch vrij. |
| TijdDatumLaatsteAanroep   | Datum  | Elke keer dat openwave kijkt of er een taak misschien uitgevoerd moet worden, wordt dat tijdstip automatsich in deze instelling opgeslagen. Deze informatie wordt gebruikt voor de tegel Versie-informatie (servicecentrum portaal): daar is een regel opgenomen met item Taskscheduler die aangeeft wanneer de taskscheduler voor het laatst is uitgevoerd en dus aangeroepen door de Cronjob. |
|                           |
