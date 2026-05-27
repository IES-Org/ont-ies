# IES Common Ontology Files

This page provides access to the authoritative machine-readable definitions of the IES Common ontology in various RDF serialisation formats.

---

## About IES Common

The **IES Common ontology** (`ies-common.ttl`) is the authoritative source of truth for the Information Exchange Standard. All documentation, diagrams, and examples are derived from this ontology file.

The ontology is expressed as an **RDF Schema** (RDFS) with selected **OWL** constructs, following W3C standards for semantic web technologies.

---

## Available Formats

### Turtle (TTL)

**Turtle** (Terse RDF Triple Language) is a compact, human-readable format for RDF data. This is the primary format for IES Common.

**Download:** [ies-common.ttl](ies-common.ttl)

**Characteristics:**
- Human-readable and writable
- Compact syntax with prefixes
- Widely supported by RDF tools
- Preferred format for version control

**Example:**
```turtle
ies:Person a rdfs:Class ;
    rdfs:label "Person"^^xsd:string ;
    rdfs:comment "A living human being" ;
    rdfs:subClassOf ies:Entity .
```

### JSON-LD

**JSON-LD** (JSON for Linked Data) provides RDF in JSON format, ideal for web applications and RESTful APIs.

**Generation:** Use standard RDF tools to convert from Turtle to JSON-LD format.

**Recommended tools:**
- `rapper` (part of Raptor RDF library)
- `rdflib` (Python)
- `rdf4j` (Java)

**Example conversion:**
```bash
rapper -i turtle -o json-ld ies-common.ttl > ies-common.jsonld
```

### RDF/XML

**RDF/XML** is the original W3C standard serialisation format for RDF.

**Generation:** Use standard RDF tools to convert from Turtle to RDF/XML format.

**Example conversion:**
```bash
rapper -i turtle -o rdfxml ies-common.ttl > ies-common.rdf
```

### N-Triples

**N-Triples** is a line-based, plain text format for RDF graphs. Each line represents a single triple.

**Generation:** Use standard RDF tools to convert from Turtle to N-Triples format.

**Example conversion:**
```bash
rapper -i turtle -o ntriples ies-common.ttl > ies-common.nt
```

---

## Ontology Metadata

| Property | Value                                                    |
|----------|----------------------------------------------------------|
| **Title** | IES Ontology                                             |
| **Version** | 5.0.3                                                    |
| **Modified** | 2026-03-30                                               |
| **Publisher** | UK Department for Business and Trade                     |
| **Language** | en-GB (British English)                                  |
| **Licence** | MIT Licence                                              |
| **Namespace** | `http://informationexchangestandard.org/ont/ies/common/` |
| **Preferred Prefix** | `ies`                                                    |

---

## Ontology Structure

The IES Common ontology is organised into several conceptual areas:

### Core Concepts

- **Thing** - Top-level class for all IES elements
- **Element** - Physical things with spatio-temporal extent
- **Entity** - Tangible things (Person, Organisation, Device, Location)
- **State** - Temporal parts of entities
- **Event** - Activities or incidents
- **PeriodOfTime** - Temporal extents

### Classification & Typing

- **ClassOfElement** - Classes and categories
- **powertype** - Relationship for creating type hierarchies

### Relationships

- **relationship** - Top-level property for relating things
- Specialised relationships for structure, participation, location, temporal ordering

### Representation

- **Representation** - Things that represent other things
- **Name** - Names for things
- **Identifier** - Unique identifiers
- **WorkOfDocumentation** - Documents about things

### Measurement & Characteristics

- **Measure** - Quantitative properties
- **Characteristic** - Qualitative properties
- **UnitOfMeasure** - Standard measurement units

---

## Using IES Common

### In RDF Triple Stores

Load the ontology into your RDF triple store to enable IES-compliant data modelling:

**Apache Jena Fuseki:**
```bash
s-put http://localhost:3030/ies/data default ies-common.ttl
```

**GraphDB:**
```bash
# Import via GraphDB Workbench UI or use RDF4J API
```

**Stardog:**
```bash
stardog data add ies ies-common.ttl
```

### In RDF Libraries

**Python (rdflib):**
```python
from rdflib import Graph

g = Graph()
g.parse("ies-common.ttl", format="turtle")

# Query the ontology
results = g.query("""
    PREFIX ies: <http://informationexchangestandard.org/ont/ies/common/>
    PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
    
    SELECT ?class ?label ?comment
    WHERE {
        ?class a rdfs:Class .
        ?class rdfs:label ?label .
        ?class rdfs:comment ?comment .
        FILTER (STRSTARTS(STR(?class), STR(ies:)))
    }
    ORDER BY ?label
""")
```

**JavaScript (rdf-ext):**
```javascript
const rdf = require('rdf-ext')
const ParserN3 = require('@rdfjs/parser-n3')
const fs = require('fs')

const parser = new ParserN3()
const quadStream = parser.import(fs.createReadStream('ies-common.ttl'))

rdf.dataset().import(quadStream).then(dataset => {
  console.log(`Loaded ${dataset.size} triples`)
})
```

### Validation

Validate your IES-compliant data against the ontology using SHACL or other validation frameworks.

---

## Extending IES Common

IES is designed to be extended for specific domains and use cases. See the [Extending IES](../user-guides/extending-ies.md) guide for detailed instructions on:

- Finding the right level to extend from
- Using `rdfs:subClassOf` and `rdfs:subPropertyOf`
- Creating domain-specific extensions
- Maintaining backward compatibility

---

## Related Resources

- [IES Specification](ies.md) - Complete visual documentation with UML diagrams
- [User Guides](../user-guides/) - How to use and extend IES
- [Examples](../examples/) - Worked examples of IES patterns
- [Sample Data](../examples/sample-data/) - Example TTL files demonstrating IES usage
- [Glossary](../glossary.md) - Key terms and definitions

---

## Version History

For detailed information about changes between versions, see the [CHANGELOG](../../CHANGELOG.md).

---

## Support

For questions, issues, or suggestions about the IES Common ontology:

- **GitHub Issues:** Report technical issues or suggest improvements
- **Documentation:** Consult the [User Guides](../user-guides/)
- **Examples:** Review [worked examples](../examples/) for practical guidance

---

*© Crown Copyright 2020-2026 | Licensed under the MIT Licence*