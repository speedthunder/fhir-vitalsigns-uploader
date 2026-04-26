# Vital Signs FHIR Uploader

[![Live Demo](https://img.shields.io/badge/Live%20Demo-GitHub%20Pages-2b6cb0?style=for-the-badge&logo=github)](https://speedthunder.github.io/fhir-vitalsigns-uploader/FHIR_Vitalsigns.html)
[![FHIR R4](https://img.shields.io/badge/FHIR-R4-e53e3e?style=for-the-badge)](https://hl7.org/fhir/R4/)
[![HTML](https://img.shields.io/badge/HTML-Pure%20Frontend-dd6b20?style=for-the-badge&logo=html5)](https://github.com/speedthunder/fhir-vitalsigns-uploader/blob/main/FHIR_Vitalsigns.html)

A lightweight, zero-dependency web tool for uploading and querying **Vital Signs FHIR Observations** — built as part of a Vital Signs Micro Implementation Guide (Micro IG) project.

---

## Screenshot

> _Upload Panel_

![screenshot-upload](https://raw.githubusercontent.com/speedthunder/fhir-vitalsigns-uploader/main/docs/screenshot-upload.png)

> _Query Panel_

![screenshot-query](https://raw.githubusercontent.com/speedthunder/fhir-vitalsigns-uploader/main/docs/screenshot-query.png)

---

## Features

- **Upload** FHIR Observations for three vital sign types
- **Query** existing records with filter and count controls
- Real-time upload log with timestamps
- Validates input range per vital sign type
- Responsive card layout — works on mobile

---

## Supported Vital Signs

| Vital Sign | LOINC Code | Unit |
|-----------|-----------|------|
| Body Temperature 體溫 | `8310-5` | Cel |
| Heart Rate 心率 | `8867-4` | /min |
| Oxygen Saturation 脈搏血氧 | `59408-5` | % |

---

## Quick Start

No installation needed. Open the file directly in any modern browser:

```bash
# Clone
git clone https://github.com/speedthunder/fhir-vitalsigns-uploader.git

# Open
open FHIR_Vitalsigns.html
```

Or use the **[Live Demo](https://speedthunder.github.io/fhir-vitalsigns-uploader/FHIR_Vitalsigns.html)** — no setup required.

---

## FHIR Resource Structure

Each uploaded entry is a FHIR `Observation` resource:

```json
{
  "resourceType": "Observation",
  "status": "final",
  "category": [{ "coding": [{ "code": "vital-signs" }] }],
  "code": {
    "coding": [{ "system": "http://loinc.org", "code": "8310-5" }]
  },
  "subject": { "reference": "Patient/90252386" },
  "effectiveDateTime": "2026-04-26T10:00:00Z",
  "valueQuantity": {
    "value": 36.8,
    "unit": "攝氏度",
    "system": "http://unitsofmeasure.org",
    "code": "Cel"
  }
}
```

**Server:** `https://hapi.fhir.org/baseR4/` (public sandbox)  
**Patient ID:** `90252386`

---

## Tech Stack

| Layer | Technology |
|-------|-----------|
| Frontend | Vanilla HTML / CSS / JavaScript |
| API | FHIR R4 REST (`application/fhir+json`) |
| Terminology | LOINC · UCUM |
| Hosting | GitHub Pages |

---

## References

- [HL7 FHIR R4 — Observation](https://hl7.org/fhir/R4/observation.html)
- [HAPI FHIR Public Test Server](https://hapi.fhir.org/)
- [LOINC Vital Signs Panel (85353-1)](https://loinc.org/85353-1/)
