# Map of Franklin County transit and polling places

Data sources:

- [`./STREET_PORTION_AND_districts.CSV`](./STREET_PORTION_AND_districts.CSV) contains the authoritative list of polling places and locations, and is sourced [from Franklin County Board of Elections public data](https://electionlink.franklincountyohio.gov/portals/ElectionVault/PublicRecords.aspx).
- The geocoded list of polling place locations [`./geocoderesult.csv`](./geocoderesult.csv) was created using [the US Census batch geocoder](https://help.bdc.fcc.gov/hc/en-us/articles/5341095744283-How-to-Use-the-Census-Geocoder), after trimming unneeded fields from `STREET_PORTION_AND_districts.CSV`.
- The shapefiles in [./COTA_Fixed-Route_Lines_Current__(Public_View)](./COTA_Fixed-Route_Lines_Current__(Public_View)) and [./COTA_Stops_Current__(Public_View)](./COTA_Stops_Current__(Public_View)) are downloaded from [COTA's Open Data Portal](https://cota1974.maps.arcgis.com/home/index.html). This data download is current as of 2023-10-07 but may not reflect actual service.

Process:

1. Download the latest data.
2. Remove unneeded fields from the polling-place list by removing columns, adding a 'State' column, and running `uniq` against the data.
3. `curl --form addressFile=@polling-places-uuid-census.csv --form benchmark=Public_AR_Current https://geocoding.geo.census.gov/geocoder/locations/addressbatch --output geocoderesult.csv`
4. Convert the geocoded results to geoJSON by ... TKTK
