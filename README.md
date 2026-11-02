# Philly-Air-Quality

An automated machine learning pipeline that forecasts next-day air quality across Philadelphia and alerts at-risk residents before unhealthy air days.

Status: in development.

## Layout

```
Philly-Air-Quality/
├── notebooks/            # Exploratory analysis
├── .gitattributes
├── .gitignore
└── README.md
```

Raw data is kept outside the repo, on an external drive:

```
Philly-Air-Quality/
├── raw/
│   ├── airnow/           # Daily monitor values, official forecasts, site metadata
│   ├── aqs_airdata/      # Verified daily and hourly PM2.5 and ozone, site lists
│   ├── cdc_places/       # Health measures by census tract
│   ├── ghcnh/            # Hourly weather for 8 stations near Philadelphia
│   └── hms_smoke/        # Daily smoke polygons
├── logs/                 # Download logs
└── scripts/              # Download scripts
```

## Data

| Data | Used for | Link |
|---|---|---|
| EPA AirData files (AQS) | Verified PM2.5 and ozone history, 2020 through latest available | [Download files](https://aqs.epa.gov/aqsweb/airdata/download_files.html) |
| AQS API (optional) | Same AQS data by query | [API docs](https://aqs.epa.gov/aqsweb/documents/data_api.html) |
| AirNow daily monitor values | Recent data not yet in AQS | [Archive](https://files.airnowtech.org/?prefix=airnow/) ([format](https://s3-us-west-1.amazonaws.com/files.airnowtech.org/airnow/docs/DailyDataFactSheet.pdf)) |
| AirNow official forecasts | Baseline to beat, 2020–present | [Archive](https://files.airnowtech.org/?prefix=airnow/) ([format](https://s3-us-west-1.amazonaws.com/files.airnowtech.org/airnow/docs/ReportingAreaFactSheet.pdf)) |
| AirNow API | Live observations and forecasts | [Request a key](https://docs.airnowapi.org/account/request/) ([endpoints](https://docs.airnowapi.org/webservices)) |
| NOAA GHCNh | Historical hourly weather | [GHCNh](https://www.ncei.noaa.gov/products/global-historical-climatology-network-hourly) |
| NWS API | Weather forecasts for live predictions | [API docs](https://www.weather.gov/documentation/services-web-api) |
| NOAA HMS smoke polygons | Smoke-day feature | [Shapefiles](https://satepsanone.nesdis.noaa.gov/pub/FIRE/web/HMS/Smoke_Polygons/Shapefile/) ([overview](https://www.ospo.noaa.gov/products/land/hms.html)) |
| CDC PLACES | Asthma prevalence by census tract | [Census tract data](https://data.cdc.gov/500-Cities-Places/PLACES-Local-Data-for-Better-Health-Census-Tract-D/cwsq-ngmh) |
| OpenAQ (stretch goal) | Neighborhood-level sensors | [API docs](https://docs.openaq.org/) |
