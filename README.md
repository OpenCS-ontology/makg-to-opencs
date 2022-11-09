# makg-to-opencs
Scripts and queries used to create the first version of OpenCS from MAKG.

The MAKG dataset by Michael Färber used for creating OpenCS is available on [Zenodo](https://zenodo.org/record/4617285).

## Contents
- `/queries` – SPARQL queries that should be run in sequence to transform MAKG into OpenCS (see below).
- `/concept_ids` – Python notebook for assigning new numeric concept ids for entities from MAKG.

## Reproducing the results

To reproduce the results:
- Download MAKG packages 13, 14, 15, 18 from [Zenodo](https://zenodo.org/record/4617285). Uncompress them.
- In file 14 remove lines that do not link to DBpedia (i.e., don't contain "http://dbpedia.org"). You can do this with grep.
  - The reason is that the links to other websites are 1. not necessarily to knowledge bases 2. contain invalid characters and glitch out Apache Jena.
- Load the files into Apache Jena Fuseki.
- Run queries 01–10 against the SPARQL UPDATE endpoint in Fuseki.
  - Some of these queries require a large amount of RAM. We ran them with JVM heap size set to 10 GB.
- Save the dataset to a file.
- Run the `concept_ids` script.

## License
This work is licensed under the Apache 2.0 license.

## Authors
- [Piotr Sowiński](https://github.com/Ostrzyciel)
