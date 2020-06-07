This repo contains a script for easily downloading the data in the FBI's
[crime data explorer platform](https://crime-data-explorer.fr.cloud.gov/downloads-and-docs) and adding it to a local postgres database.

The [crime data explorer tool](https://crime-data-explorer.fr.cloud.gov/explorer/national/united-states/crime) has some interesting analytics built into it,
but leaves much to be desired.

# How to use this script

## Prerequisites
The only thing you'll need for this to work is PostgreSQL
installed as your database.

## How to run this script
1. Create a databse where you want to keep this data, I chose the
name `fbi-crime-data`
```
  ~$ createdb fbi-crime-data
```

2. Run the script with your database name configured. This will take
some time, it's downloading over 5 million reported crimes from the
FBI's database!
```
  ~$ DB_NAME=fbi-crime-data ./dl-all-2018
```

3. Explore!
```
  ~$ psql -d fbi-crime-data
  fbi-crime-data =#
```

## Notes
* This script is idempotent – you can rerun it and you won't end
  up with duplicate data
* The data is not complete – the FBI doesn't provide links for data for NC, NY, Alaska,
  California, Florida, Nevada, and Wyoming
