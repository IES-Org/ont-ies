# IES Examples

Welcome to the IES Examples section. This area provides practical, worked examples demonstrating how to use IES patterns to model real-world scenarios and create IES-compliant instance data.

## About These Examples

The examples in this section are designed to help you understand how to apply IES concepts in practice. Each example includes:

- **Visual diagrams** showing the structure and relationships
- **RDF/Turtle code** demonstrating the implementation
- **Explanatory text** clarifying the modelling choices
- **Use case context** showing when to apply each pattern

## Example Categories

### Detailed Worked Examples

Comprehensive examples with diagrams and step-by-step explanations:

#### [IES Examples Documentation](ies-examples.md)

Detailed worked examples covering:

1. [**A Meeting**](ies-examples.md#a-meeting) - Event participation and timing
2. [**Observations of a Moving Aircraft**](ies-examples.md#observations-of-a-moving-aircraft) - Temporal observation patterns
3. [**Representations of an Address**](ies-examples.md#representations-of-an-address) - Multiple representations of the same information
4. [**SIM Card Swap in a Mobile Handset**](ies-examples.md#sim-card-swap-in-a-mobile-handset) - State changes and asset relationships
5. [**Assessments and Subject of Interest**](ies-examples.md#assessments-and-subject-of-interest) - Intelligence assessment patterns
6. [**Posts of Organisations**](ies-examples.md#posts-of-organisations) - Organisational structures and roles
7. [**SMS Message**](ies-examples.md#sms-message) - Communication event modelling
8. [**Voice Call**](ies-examples.md#voice-call) - Telecommunications event patterns
9. [**Movement**](ies-examples.md#movement) - Journey modelling with multiple legs

Each example includes UML diagrams, RDF triples, and detailed explanations of the modelling decisions.

### Sample Data Files

Ready-to-use RDF/Turtle files that you can load into your triple store:

#### [Sample Data Repository](sample-data/index.md)

Complete collection of `.ttl` files demonstrating:

**Core Patterns:**

- Assessment patterns with confidence levels
- Characteristics and measures
- Event participation
- Events with temporal bounds
- Identifiers and naming schemes
- Relationships between entities
- Types and classification

**Complex Patterns:**

- Communications (calls, messages)
- Event linkages and composition
- Geospatial data with GeoSPARQL
- Hospital patient journey (comprehensive example)
- Movement and travel tracking
- Periods of time
- Discontinuous states ("sometimes" patterns)
- Spatio-temporal modelling

All files are valid RDF/Turtle that can be loaded directly into any RDF triple store.

## How to Use These Examples

### For Learning

1. **Start with visualisations** - Review the [IES Examples Documentation](ies-examples.md) to see diagrams
2. **Read the explanations** - Understand the modelling decisions and patterns
3. **Study the RDF** - Examine how concepts translate to Turtle syntax
4. **Try modifications** - Adapt examples to similar scenarios

### For Implementation

1. **Identify your use case** - Find the example closest to your needs
2. **Download sample data** - Get the relevant `.ttl` file from [Sample Data](sample-data/index.md)
3. **Load and query** - Import into your RDF triple store and run SPARQL queries
4. **Adapt and extend** - Modify the pattern for your specific requirements

### For Validation

1. **Use as templates** - Copy patterns that match your use case
2. **Replace test data** - Substitute your actual data for the example data
3. **Validate structure** - Ensure your data follows the same structural patterns
4. **Test queries** - Verify you can query your data the same way

## Learning Path by Role

### For Implementers

**Goal:** Create IES-compliant data for your systems

1. Start with [Sample Data](sample-data/index.md) - explore the `.ttl` files
2. Load samples into a local triple store (Fuseki, GraphDB, Stardog)
3. Run SPARQL queries to understand the structure
4. Use [hospital.ttl](sample-data/index.md#hospital-example) as a comprehensive reference
5. Adapt patterns to your domain

**Recommended examples:**

- Event participation patterns
- Identifiers and naming
- Relationships and states

### For Information Architects

**Goal:** Design information exchanges using IES patterns

1. Review [IES Examples Documentation](ies-examples.md) for visual understanding
2. Study how different aspects (temporal, spatial, participatory) combine
3. Examine [Sample Data](sample-data/index.md) for implementation details
4. Consider extension points for domain-specific needs

**Recommended examples:**

- Assessments and Subject of Interest (intelligence patterns)
- Posts of Organisations (organisational structure)
- Movement (complex multi-part events)

### For Data Modellers

**Goal:** Map existing schemas to/from IES

1. Find examples similar to your existing data structures
2. Compare your current model to IES patterns
3. Identify mapping rules between your schema and IES
4. Use sample data as transformation templates

**Recommended examples:**

- Representations of an Address (multiple representations)
- Types and classification (taxonomies)
- SIM Card Swap (state changes)

### For Analysts and Users

**Goal:** Understand what IES data looks like and how to query it

1. Review visualisations in [IES Examples Documentation](ies-examples.md)
2. Learn basic SPARQL queries from [Sample Data](sample-data/index.md)
3. Experiment with querying the sample data
4. Understand temporal and participatory patterns

**Recommended examples:**

- A Meeting (simple event pattern)
- Voice Call (communication pattern)
- Hospital patient journey (realistic scenario)

## Example Patterns Summary

### Temporal Patterns

**When to use:** Modelling things that change over time, have duration, or occur at specific times

**Key examples:**

- Events with bounding states (start/end)
- Period of time representations
- Discontinuous states ("sometimes")
- State changes (SIM card swap)

**See:** [Period of Time](sample-data/index.md#period-of-time), [Events](sample-data/index.md#events), [Sometimes](sample-data/index.md#sometimes-discontinuous-states)

### Participation Patterns

**When to use:** Modelling entities involved in events or activities

**Key examples:**

- Meeting with attendees
- Voice call with caller/callee
- Surgery with patient and surgeons
- Journey with traveller and vehicles

**See:** [Event Participation](sample-data/index.md#event-participation), [A Meeting](ies-examples.md), [Voice Call](ies-examples.md)

### State Patterns

**When to use:** Modelling properties or conditions that hold for specific temporal extents

**Key examples:**

- Person in hospital ward
- Person as subject of interest
- Device in use
- Location occupied

**See:** [Hospital Example](sample-data/index.md#hospital-example), [SIM Card Swap](ies-examples.md)

### Relationship Patterns

**When to use:** Modelling connections between entities

**Key examples:**

- Organisational relationships (works for, reports to)
- Spatial relationships (located in, part of)
- Social relationships (family, friends)
- Structural relationships (component of, member of)

**See:** [Relationships](sample-data/index.md#relationships), [Posts of Organisations](ies-examples.md)

### Representation Patterns

**When to use:** Modelling names, identifiers, and different representations of things

**Key examples:**

- Multiple names for the same person
- Different identifier schemes
- Address representations
- Coordinate systems

**See:** [Identifiers](sample-data/index.md#identifiers), [Representations of an Address](ies-examples.md)

### Assessment Patterns

**When to use:** Modelling subjective judgements, confidence levels, and analytical assessments

**Key examples:**

- Intelligence assessments with confidence
- Risk evaluations
- Scenario analysis
- Subject of interest designation

**See:** [Assessment](sample-data/index.md#assessment), [Assessments and Subject of Interest](ies-examples.md)

### Classification Patterns

**When to use:** Creating type hierarchies and categorising entities

**Key examples:**

- PowerType relationships
- Class hierarchies
- Type-level properties
- Faceted classification

**See:** [Types and Classification](sample-data/index.md#types-and-classification)

### Geospatial Patterns

**When to use:** Modelling geographic locations and coordinates

**Key examples:**

- Latitude/longitude coordinates
- Location relationships
- Movement between locations
- Spatial queries with GeoSPARQL

**See:** [Geospatial](sample-data/index.md#geospatial), [Movement](sample-data/index.md#movement)

## Tools and Resources

### RDF Triple Stores

Load sample data into these tools to experiment:

- **Apache Jena Fuseki** - Open source, easy to set up locally
- **GraphDB** - Feature-rich with visual query builder
- **Stardog** - Enterprise-grade with reasoning support
- **Blazegraph** - High-performance graph database

### SPARQL Query Editors

Write and test queries against sample data:

- **Fuseki UI** - Built into Apache Jena Fuseki
- **GraphDB Workbench** - Visual query builder and editor
- **YASGUI** - Web-based SPARQL IDE
- **RDFox** - High-performance reasoner with query interface

### RDF Visualisation

Visualise the structure of sample data:

- **WebVOWL** - Interactive ontology visualisation
- **LodLive** - Browse RDF resources interactively
- **Gruff** - Visual RDF browser (Franz Inc.)

### Development Libraries

Programmatic access to IES data:

- **RDFLib** (Python) - Parse, query, and manipulate RDF
- **Apache Jena** (Java) - Comprehensive RDF toolkit
- **rdflib.js** (JavaScript) - RDF library for Node.js and browsers
- **Oxigraph** (Rust) - Fast RDF store and query engine

## Related Documentation

### Essential Reading

- **[User Guides](../user-guides/index.md)** - Understand IES fundamentals
- **[Instantiation Patterns](../user-guides/instantiation-patterns.md)** - Standard patterns for creating instances
- **[Extending IES](../user-guides/extending-ies.md)** - How to extend for specific needs
- **[Specification](../specification/index.md)** - Complete technical reference

### Quick References

- **[Glossary](../glossary.md)** - Key terms defined
- **[4D Ontology](../user-guides/4d-ontology.md)** - Understanding the temporal approach

## Contributing Examples

Have you developed IES examples that demonstrate useful patterns or solve common problems?

### Contribution Guidelines

1. **Ensure validity** - Your example must use valid IES patterns
2. **Add clear comments** - Include comments in Turtle files explaining the pattern
3. **Provide context** - Brief description of the use case and modelling decisions
4. **Test thoroughly** - Validate against IES Common ontology
5. **Document well** - Include diagrams if possible

### How to Contribute

1. Fork the [IES GitHub repository](https://github.com/IES-Org/ies-common)
2. Add your example with documentation
3. Ensure it follows the project structure
4. Submit a pull request with clear description

We particularly welcome examples that:

- ✅ Demonstrate domain-specific extensions
- ✅ Show integration with other standards (e.g., PROV, SKOS)
- ✅ Illustrate complex temporal or spatial reasoning
- ✅ Provide real-world use case solutions

## Getting Help

If you need assistance understanding or adapting these examples:

1. **Review the FAQ** - Many common questions are answered there
2. **Check the User Guides** - Detailed explanations of concepts
3. **Open a GitHub issue** - For specific technical questions
4. **Contact the IES team** - For broader implementation guidance

---

*© Crown Copyright 2020-2026 | Licensed under the MIT Licence*
