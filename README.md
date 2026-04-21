# EDAN Schemas

EDAN is a suite of services and technologies that centralizes access and distribution of the Smithsonian Institution's (SI) vast holdings of metadata and file content from its collections, archives, and libraries.

EDAN schemas detail the `content` property of certain EDAN record
types. They do not describe root-level properties such as id, url, title,
or unitCode.

## Directory Structure
Schemas are organized into two directories based on data provenance.

- **`/schemas/content`** — non-primary data ingested from external systems (e.g., TMS, ArchivesSpace)
- **`/schemas/authored`** — primary data created and managed directly in EDAN

Some schemas appear in both directories because the data shape can originate from either pathway.

## Useful Links

* JSON formatting: <https://jsonlint.com>
* JSON online validator: <https://json-schema-validator.herokuapp.com>
* JSON schema maker: <https://jsonschema.net>
