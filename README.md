# overview

Static site using Vega for charting.

This depends on:

* CSVs in Google Drive
* converting those CSVs to a Google Sheet (for some reason I don't remember)

# potential impl

* dump tables from Postgres read replica
```sh
pg_dump --data-only --column-inserts --dbname=odoo-read-replica --table=foo > foo.sql
pg_dump --data-only --column-inserts --dbname=odoo-read-replica --table=bar > bar.sql
```
* ingest into SQLite
```sh
sqlite3 agg.sqlite < foo.sql
sqlite3 agg.sqlite < bar.sql
```
* run joins and export to CSV
```sh
sqlite-utils agg.sqlite "super big join here" --csv > bi.csv
```
* upload CSV to Google Drive, publish through sheets

