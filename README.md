# EDAN Schemas

EDAN is a suite of services and technologies that centralizes access and distribution of the Smithsonian Institution's (SI) vast holdings of metadata and file content from its collections, archives, and libraries.

## What an EDAN Record Looks Like

An EDAN record has two layers:

- A root record envelope containing fields such as id, title, unitCode, type, url, content, hash, docSignature, timestamp, version, and publicSearch.
- A content object whose structure depends on the record type.

The shared root record properties live in [core.json](core/core.json).

## How the Content Model Works

Many EDAN content schemas organize metadata into a compact set of top-level buckets rather than a single flat object. An ideal example is [edanmdm.json](schemas/content/edanmdm.json).

These buckets separate metadata by purpose:

* **descriptiveNonRepeating** : core descriptive data that is usually singular or canonical for the record.
* **indexedStructured** : normalized values intended for faceting, filtering, sorting, and structured search.
* **freetext** : display-oriented text grouped under dynamic field names, usually as arrays of label/content objects.
* **descriptiveOptional** : additional descriptive data that is not required for the core identity of the record.

This separation is important because the same concept may appear in more than one bucket for different reasons. For example, a place, name, or date may appear:

* in **freetext** for labeled display text,
* in **indexedStructured** for faceting and search,
* in **descriptiveNonRepeating** when it is part of the record’s canonical description.

That design allows EDAN to preserve source metadata while also supporting a wide array of search and presentation needs.


## Common Top-Level Content Buckets

### descriptiveNonRepeating

This section contains the record’s core descriptive fields. In the edanmdm schema it includes fields such as title_sort, title, data_source, record_ID, unit_code, record_link, guid, metadata_usage, and online_media. It's often used for canonical titles, record links or GUIDs, core media summaries, and unit and source attribution. 

### indexedStructured

This section contains normalized metadata fields typically used for faceting and structured search. In edanmdm it includes fields such as date, topic, object_type, place, scientific_name, taxonomic fields, geoLocation, and online_media_type. It's often used for search facets, place hierarchies, structured dates, and sort-oriented values.


### freetext

This section contains dynamically named freetext fields. In edanmdm, freetext ensures that any field name may appear, and each field maps to an array of objects containing at least label and content.Typically, freetext is used for human-readable display text, repeated labeled statements, and source text that doesn't fit an obvious or fixed field cleanly.

In the [example record](edan_examples/edanmdm.json), freetext includes keys such as date, name, notes, place, publisher, dataSource, identifier, objectType, and physicalDescription.

### descriptiveOptional
This section contains additional descriptive information that is useful but not always required. In edanmdm it is minimal, but other schemas use it more heavily. Sometimes it's used for supplemental notes and optional display metadata.

## Directory Structure

Schemas are organized into two directories based on data provenance.

- **`/schemas/content`** — non-primary data ingested from external systems (e.g., TMS, ArchivesSpace)
- **`/schemas/authored`** — primary data created and managed directly in EDAN

Some schemas appear in both directories because the data shape can originate from either pathway.

## Useful Links

* JSON formatting: [https://jsonlint.com](https://jsonlint.com)
* JSON online validator: [https://json-schema-validator.herokuapp.com](https://json-schema-validator.herokuapp.com)
* JSON schema maker: [https://jsonschema.net](https://jsonschema.net)