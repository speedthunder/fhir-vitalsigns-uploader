# Vital Signs FHIR Uploader

A single-page frontend tool for uploading and querying **Vital Signs FHIR Observations** against a public HAPI FHIR R4 server.  
Built as part of a **Vital Signs Micro Implementation Guide (Micro IG)** course assignment.

## Live Demo

[**Open the App →**](https://speedthunder.github.io/fhir-vitalsigns-uploader/FHIR_Vitalsigns.html)

## Features

| Feature | Detail |
|---------|--------|
| Upload Observations | Body Temperature, Heart Rate, Oxygen Saturation |
| LOINC Codes | 8310-5 / 8867-4 / 59408-5 |
| FHIR Server | `https://hapi.fhir.org/baseR4/` (public sandbox) |
| Patient ID | `90252386` |
| Query | Fetch and display existing Observations with filters |
| Pure Frontend | No build step — open directly in any browser |

## Supported Vital Signs

| Vital Sign | LOINC | UCUM Unit |
|-----------|-------|-----------|
| 體溫 Body Temperature | 8310-5 | `Cel` |
| 心率 Heart Rate | 8867-4 | `/min` |
| 脈搏血氧 Oxygen Saturation | 59408-5 | `%` |

## Usage

### Run Locally

Just open `FHIR_Vitalsigns.html` in any modern browser — no server or build tool required.

### FHIR Resource Structure

Each uploaded Observation follows this structure:

```json
{
  "resourceType": "Observation",
  "status": "final",
  "category": [{ "coding": [{ "code": "vital-signs" }] }],
  "code": { "coding": [{ "system": "http://loinc.org", "code": "8310-5" }] },
  "subject": { "reference": "Patient/90252386" },
  "effectiveDateTime": "2026-04-26T10:00:00Z",
  "valueQuantity": { "value": 36.8, "unit": "攝氏度", "system": "http://unitsofmeasure.org", "code": "Cel" }
}
```

## Files

| File | Description |
|------|-------------|
| `FHIR_Vitalsigns.html` | Main app — upload & query Vital Signs |
| `fhir-explorer.html` | FHIR resource explorer (supplementary) |
| `element.csv` | Micro IG element definitions |
| `valueSet.csv` | Micro IG value set definitions |

## Tech Stack

- Vanilla HTML / CSS / JavaScript (ES2020+)
- FHIR R4 REST API (`application/fhir+json`)
- LOINC & UCUM terminology

## References

- [HL7 FHIR R4 Observation](https://hl7.org/fhir/R4/observation.html)
- [HAPI FHIR Public Test Server](https://hapi.fhir.org/)
- [LOINC Vital Signs Panel](https://loinc.org/85353-1/)
