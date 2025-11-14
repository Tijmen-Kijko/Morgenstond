# Automatiseringen
- **Nieuwe Opname**: Trigger bij nieuw record in 'Opnames' → maak lege 'Behandelingen' en 'Medicaties'-records aangemaakt (optioneel via script).
- **Ontslagdatum ingevuld**: Trigger bij veldwijziging 'Ontslagdatum' in 'Opnames' → herbereken automatisch 'Verblijfsduur' en update 'Risicoklasse'.
- **Validaties**: Waarschuw bij dubbele BSN of ontbrekende verplichte velden.

## Formulesuggesties (Airtable)
- `Verblijfsduur`: `DATETIME_DIFF({Ontslagdatum}, {Opnamedatum}, 'days')`
- `Risicoklasse`:

```
IF(
	IS_BLANK({Ontslagdatum}),
	"Actieve opname",
	IF({Verblijfsduur} <= 2, "Laag risico",
		IF({Verblijfsduur} <= 6, "Middel risico", "Hoog risico")
	)
)
```

### Toelichting en opties
- Nieuwe Opname: kan met een eenvoudige Airtable Automation die bij 'when record created' twee lege gerelateerde records toevoegt in 'Behandelingen' en 'Medicaties'. Voor complexere logica kun je een script-run gebruiken (JavaScript in Airtable scripting action).
- Ontslagdatum ingevuld: gebruik een 'when record updated' trigger op het veld `Ontslagdatum`. In de actie kun je een 'Update record' uitvoeren met berekende waarden of een script dat extra controles uitvoert.
- Validaties: implementeer checks in een 'when record updated' automation of via een scheduled script dat dubbele BSN's zoekt en een bericht/waarschuwing (e-mail of Slack) stuurt.

Wil je dat ik voorbeeldscripts opzet (Airtable Scripting) of voorbeeld-Automations exporteer? Ik kan ook de formules als velden toevoegen in het JSON template.

