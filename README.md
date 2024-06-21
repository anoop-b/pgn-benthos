# PGN Processor

A simple PGN( Chess game format) ingestion using benthos.
## Pre-requisites 
- benthos
- NATS server

Place all the PGN files in the `data` folder at the root of the repository.
## Usage/Examples

```bash
benthos -c config.yaml
```
## Documentation

Benthos parses chunks until the word `[[Event` is found. It then adds back the same word to each game and sends it to the respective NATS subject as mentioned in the config. You may try experimenting with the buffer size to get the optimal speed without having to load the entire PGN file in memory.

Although there exists a lot of PGN parsers, I found this approach to be the fastest and most reliable without installing something like Apache spark.

