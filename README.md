# Philly-Air-Quality

A statistical analysis of Philadelphia air quality from 2020 to 2026: what it looks like, when and where it is worst, what drives it, who is most affected, and whether bad days can be seen coming. The findings will be published as a Tableau Public dashboard and a written report. This project uses six years of monitor, weather, smoke and health data to put those days in context.

Status: in development.

## Approach

1. **Clean** five public data sources into one documented, quality-checked dataset.
2. **Model** it as a star schema in DuckDB.
3. **Analyze** it with descriptive and inferential statistics: seasonality, trends, monitor comparisons, weather regression, smoke-event analysis, a bad-day prediction model compared with the official forecast, and an equity analysis.
4. **Visualize** the results in a Tableau Public dashboard.


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
| AirNow daily monitor values | Recent data not yet in AQS | [Archive](https://files.airnowtech.org/?prefix=airnow/) ([format](https://s3-us-west-1.amazonaws.com/files.airnowtech.org/airnow/docs/DailyDataFactSheet.pdf)) |
| AirNow official forecasts | What forecasters predicted, compared with what happened | [Archive](https://files.airnowtech.org/?prefix=airnow/) ([format](https://s3-us-west-1.amazonaws.com/files.airnowtech.org/airnow/docs/ReportingAreaFactSheet.pdf)) |
| NOAA GHCNh | Historical hourly weather | [GHCNh](https://www.ncei.noaa.gov/products/global-historical-climatology-network-hourly) |
| NOAA HMS smoke polygons | Which days had smoke overhead | [Shapefiles](https://satepsanone.nesdis.noaa.gov/pub/FIRE/web/HMS/Smoke_Polygons/Shapefile/) ([overview](https://www.ospo.noaa.gov/products/land/hms.html)) |
| CDC PLACES | Asthma prevalence by census tract | [Census tract data](https://data.cdc.gov/500-Cities-Places/PLACES-Local-Data-for-Better-Health-Census-Tract-D/cwsq-ngmh) |

## Stretch goals

- A live AWS pipeline (Lambda, DynamoDB, SNS, EventBridge) managed with Terraform, for daily forecasts and email alerts, using the [AirNow API](https://docs.airnowapi.org/webservices) and [NWS API](https://www.weather.gov/documentation/services-web-api)
- dbt for the modeling layer
- Neighborhood-level detail from [OpenAQ](https://docs.openaq.org/) low-cost sensors
