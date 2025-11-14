# Views per tabel

## Patiënten - Analyse
- Toon: `Patiënt_ID`, `Naam`, `BSN`, aantal opnames (COUNT rollup)
- Filter: unieke patiënten

## Opnames - Overzicht
- Toon: `Opname_ID`, `Patiënt_ID`, `Opnamedatum`, `Ontslagdatum`, `Kamer`, `Verblijfsduur`, `Risicoklasse`
- Filter: actieve opnames, laatste 30 dagen ontslagen

## Behandelingen - Analyse
- Toon: `Behandelcode`, Totaal aantal uitvoeringen (COUNT)
- Filter: laatste maand

## Medicaties - Toedieningsanalyse
- Toon: `Verpleegkundige`, aantal toedieningen
- Filter: laatste maand

