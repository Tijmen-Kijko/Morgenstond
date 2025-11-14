# Validatie Checklist – Airtable Migratie

Gebruik deze checklist na elke grote import- of migratiestap. Loop alle punten na vóórdat je live gaat.

## Algemeen
- [ ] Zijn er geen importfouten of warnings gemeld door Airtable?
- [ ] Zijn alle referentietabellen (Afdelingen, Huisartsen, Kamers) als eerste gevuld?

## Tabellen & Relaties
- [ ] Komen de aantallen records per tabel overeen met de aantallen in de oorspronkelijke brondata?
- [ ] Zijn alle `*_ID`-velden uniek in de betreffende tabellen?
- [ ] Zijn er geen lege verplichte velden (zoals BSN, Opnamedatum, Registratienummer)?
- [ ] Zijn alle linked records herkend door Airtable (geen @missing links)?

## Duplicaten & Consistentie
- [ ] Zijn dubbele patiënten opgespoord en opgelost? (Controleer op BSN, naam en geboortedatum)
- [ ] Zijn medewerkers, afdelingen en specialisaties consequent geschreven?
- [ ] Zijn medicijnnamen genormaliseerd (zelfde spelling/dosering voor dezelfde middelen)?

## Data-integriteit & rapportages
- [ ] Werken alle basisformules in Airtable (zoals Verblijfsduur en Risicoklasse in Opnames)?
- [ ] Kloppen de aantallen opnames per patiënt en behandelingen per code met de oude registratie?
- [ ] Kun je per kamer zien wanneer wie daar verbleef?
- [ ] Is de volledige medicatiegeschiedenis per patiënt via linked views zichtbaar?
- [ ] Zijn de views/filter-rapportages voor de 8 kernvragen gevuld en kloppen de getallen?

## Post-migratie checks
- [ ] Exporteer per tabel een rapport en vergelijk met de oude situatie (eventueel steekproefsgewijs).
- [ ] Controleer bij actieve opnames dat de status ("Actieve opname") gevuld wordt bij missende ontslagdatum.
- [ ] Is het dashboard per medewerker en per afdeling gevuld met juiste rollen en samengevoegde info?

---

## Extra aanbevelingen
- Maak na succesvolle validatie een backup/export van de volledige base.
- Leg afwijkingen/fixbeslissingen vast in een apart migratie-logboek.
