# Migratiehandleiding Ziekenhuis De Morgenstond – Airtable Base

Deze handleiding beschrijft de gestructureerde aanpak om bestaande data vanuit Excel/Access naar de nieuwe Airtable-base te migreren. Volg de stappen in de aangegeven volgorde en voer aan het eind alle validaties uit die in de checklist staan.

## 1. Inventarisatie en voorbereiding
- Bepaal de bronnen: Exporteer relevante tabbladen/queries uit Excel/Access naar CSV-bestanden per entiteit (Patiënt, Medewerker, etc.).
- Controleer of alle noodzakelijke kolommen aanwezig zijn; gebruik de CSV-templates als leidraad.
- Maak een backup van alle ruwe exportdata.

## 2. Opschonen en normaliseren van data
- Voer een deduplicatie uit: controleer op dubbele patiënten (via BSN + voornaam + geboortedatum).
- Standaardiseer schrijfwijzen bij 'specialisatie', 'afdeling', 'medicatie' (gebruik vaste lijsten).
- Vul ontbrekende sleutels aan zoals Patiënt_ID, Medewerker_ID etc. (gebruik unieke waarden).

## 3. Importvolgorde voor referentie-integriteit
1. **Afdelingen importeren**  
   Vul eerst `afdelingen.csv` en importeer die in Airtable.
2. **Huisartsen importeren**
   Vul en importeer `huisartsen.csv`.
3. **Kamers importeren**
   Vul en importeer `kamers.csv`.
4. **Medewerkers importeren**
   Vul en importeer `medewerkers.csv` (met verwijzing naar Afdelingen).
5. **Patiënten importeren**
   Vul en importeer `patienten.csv` (met BSN en Huisarts-link).
6. **Opnames importeren**
   Vul en importeer `opnames.csv` (met correcte Patiënt/Kamer-verwijzing).
7. **Behandelingen importeren**
   Vul en importeer `behandelingen.csv` (met Opname/Medewerker-link).
8. **Medicaties importeren**
   Vul en importeer `medicaties.csv` (met Opname/Verpleegkundige-link).
9. **Kamerwisselingen importeren**
   Vul en importeer `kamerwisselingen.csv` (met Opname/Kamer-link en data).

## 4. Post-import checks & validatie
- Voer de validatiechecklist uit (zie: `migratie/validatiechecklist.md`).
- Controleer of alle linked records zijn herkend in Airtable.
- Vergelijk rapportages met de oude situatie (Exporteer aantal records per entiteit; moeten kloppen met brondocumentatie).

## 5. Specifieke migratietips
- Importeer grote CSV’s eventueel in batches als het importeren in Airtable traag is.
- Gebruik de import preview-functie om veldmapping te controleren.
- Corrigeer fouten/linked records direct in Airtable zodra die opvallen na import.
- Documenteer afwijkingen en beslissingen in het bestand `migratie/migratie_beslissingen.md` (optioneel).

## 6. Backup & afsluiting
- Maak een backup van de gereedstaande Airtable-base zodra alles geïmporteerd en gevalideerd is.
- Werk de handleiding bij met lessons learned na de eerste migratie.

