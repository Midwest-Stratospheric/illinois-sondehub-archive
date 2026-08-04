# Illinois SondeHub Archive

**Maintained by [Midwest Stratospheric Data Systems](https://www.midwestsds.com)**  
Casey, Illinois · NASA GLOBE GO-4VW9B · Open atmospheric data

Daily archive of public SondeHub telemetry focused on the **Illinois / Casey IL region**.  
This repository supports the [MSDS Atmospheric Explorer](https://www.midwestsds.com/atmospheric-explorer.html) and open research into vertical atmospheric profiles, wind, and near-space conditions over the Midwest.

## Coverage Area

Approximate bounding box used for filtering:

| Corner | Latitude | Longitude |
|--------|----------|-----------|
| Southwest | 36.9°N | −91.5°W |
| Northeast | 42.6°N | −87.0°W |

Centered on **Casey, Illinois** (39.2992°N, 87.9925°W) and covering the majority of Illinois plus near-border activity.

## Data Sources

- **SondeHub** / **SondeHub Amateur** — [api.v2.sondehub.org](https://api.v2.sondehub.org)  
  Public radiosonde and amateur high-altitude balloon telemetry (CC BY-SA 2.0).
- Filtered client-side for the Illinois bounding box and for callsigns of interest (KE9CFY, X2Griffon / MSDS payloads when active).

## Repository Layout

```
├── latest/
│   └── illinois.json          # Most recent snapshot (updated daily)
├── daily/
│   └── YYYY-MM-DD.json        # One file per day
├── scripts/
│   └── fetch_illinois.py      # Optional local / Action helper
├── .github/workflows/
│   └── daily-sondehub.yml     # Scheduled GitHub Action
└── LICENSE
```

### `latest/illinois.json` schema (simplified)

```json
{
  "generated_at": "2026-08-04T15:00:00Z",
  "region": "Illinois / Casey IL",
  "bbox": { "lat_min": 36.9, "lat_max": 42.6, "lon_min": -91.5, "lon_max": -87.0 },
  "source": "https://api.v2.sondehub.org",
  "active_count": 0,
  "payloads": [],
  "notes": "No active Illinois-area flights at collection time"
}
```

## Automation

A GitHub Action runs daily (≈ 12:00 UTC) to:

1. Query SondeHub Amateur + radiosonde endpoints
2. Filter positions inside the Illinois bounding box
3. Write `latest/illinois.json` and a dated file under `daily/`
4. Commit the update

## Credits & Attribution

- **SondeHub / Project Horus** — telemetry database and API  
  https://sondehub.org · https://github.com/projecthorus/sondehub-infra  
  Data licensed **Creative Commons BY-SA 2.0**
- **Midwest Stratospheric Data Systems (MSDS)** — curation, regional filtering, Atmospheric Explorer integration  
  https://www.midwestsds.com · Casey, Illinois
- Amateur radio community receivers that upload to SondeHub

When using this archive please attribute both **SondeHub** and **Midwest Stratospheric Data Systems**.

## Related MSDS Repositories

- [msds-data](https://github.com/Midwest-Stratospheric/msds-data) — MSDS flight + ground weather releases
- [International-Ground-Data-Repository](https://github.com/Midwest-Stratospheric/International-Ground-Data-Repository) — broader upper-air aggregation

---

© 2026 Midwest Stratospheric Data Systems  
Open data for atmospheric science, education, and citizen science.
