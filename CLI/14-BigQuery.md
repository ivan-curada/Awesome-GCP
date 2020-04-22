# BigQuery

https://cloud.google.com/bigquery/docs/bq-command-line-tool

## Create Dataset

```cli
bq mk [DATASET_NAME]
```

## List Dataset

``` cli
bq ls
```

## List Data Table

```cli
bq ls [DATASET_NAME]
```

## Show Data TAble Information

``` cli
bq show [DATASET_NAME].[TABLE_NAME]
```

## Load Data to BigQuery Table

<https://cloud.google.com/bigquery/docs/loading-data-cloud-storage-csv>

- add schema is included

```cli
bq load --skip_leading_rows [1] [DATASET_NAME][.[TABLE_NAME] [CSV_FILENAME] [HEADER]:[datatype],[HEADER]:[datatype]
```

### Schema Auto-Detect

<https://cloud.google.com/bigquery/docs/schema-detect>

```cli
bq --location=location load \
--autodetect \
--source_format=format \
dataset.table \
path_to_source
```

- location is the name of your location. The --location flag is optional. For example, if you are using BigQuery in the Tokyo region, set the flag's value to asia-northeast1. You can set a default value for the location using the .bigqueryrc file.
- format is either NEWLINE_DELIMITED_JSON or CSV.
- dataset is the dataset that contains the table into which you're loading data.
- table is the name of the table into which you're loading data.
- path_to_source is the location of the CSV or JSON file.
