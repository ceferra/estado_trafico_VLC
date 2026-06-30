# estado_trafico_VLC — Traffic state by road segment (València)

Historical archive of the **traffic state (congestion level) by road segment**
for València, from the municipal open-data portal (now decommissioned). This is
the categorical congestion variable, complementary to the numeric intensity of
`traffic_VLC`.

## Source

- **Publisher:** València City Council — *mapas.valencia.es* portal
  (`lanzadera/opendata/Tra-estado-trafico/JSON`).
- Decommissioned service; this repository is the backup copy of the history.

## Period

- **2146 days** between **2015-02-06** and **2024-10-24**.

## Repository layout

- One ZIP file per day: `DD-MM-YYYY.zip`, holding the JSON snapshots of that day.
- One commit ("new day") per day, dated with the real date of the data.

## Format and fields

Each JSON is a **GeoJSON `FeatureCollection`** in projection **EPSG:25830**
(UTM zone 30N, ETRS89). Each *Feature* is a road segment (`LineString`
geometry) with these properties:

| Field           | Meaning                                                      |
|-----------------|--------------------------------------------------------------|
| `idtramo`       | Road-segment identifier.                                     |
| `denominacion`  | Segment name / description.                                  |
| `estado`        | Traffic state (categorical congestion code).                |

### `estado` codes (València municipal convention)

| Value | Meaning            |
|-------|--------------------|
| 0     | Free-flowing       |
| 1     | Dense              |
| 2     | Congested          |
| 3     | Blocked            |
| 4     | No data            |

> Higher values indicate more congestion. The exact mapping may vary depending
> on the version of the original service.
