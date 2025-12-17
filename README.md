# IATA Airport Codes Cheat Sheet

A lightweight, static, browser-based cheat sheet for IATA airport codes.  
The page loads airport data from an XML file and provides search, sorting, and grouping functionality.

This project is intended as a quick reference that can be bookmarked and hosted for free using GitHub Pages or any static web server.

---

## Features

- Loads airport data from a single XML file
- Search by:
  - IATA code
  - Airport name
  - Group
  - Notes
- Sort by:
  - Code
  - Airport name
  - Group
- Grouped display (e.g. UK, Channel Islands, legacy/placeholder entries)
- Pure static hosting (no backend, no database)
- Works on desktop and mobile browsers

---

## Project Structure
```text
iata-cheatsheet/
├── index.html
├── airports.xml
└── README.md
```

## Data Format (`airports.xml`)

Each airport is defined as an `<airport>` element:

```xml
<airport>
  <code>LHR</code>
  <name>London Heathrow Airport</name>
  <group>UK</group>
  <note>Optional notes</note>
</airport>
```

### Fields

* **code**
IATA airport code (may include legacy or placeholder values)

* **name**
Airport name

* **group**
Logical grouping (e.g. UK, Channel Islands, Legacy & placeholders)

* **note (optional)**
Any additional context, warnings, or legacy information

---

**Schema and validation**

- **Schema file:** `airports.xsd` (added to the project root). It declares the allowed child elements for each `<airport>` and a basic pattern for `code` values.
- **Usage:** Editors that support XML schema will pick up `airports.xsd` automatically because `airports.xml` references it. To validate from the command line you can use `xmllint`:

```bash
xmllint --noout --schema airports.xsd airports.xml
```

If no output is produced, the document is valid; errors will be printed otherwise.

