# IES Common Changelog

All notable changes to the IES Common ontology module are documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/)
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [5.0.0] - 2025-11-29 — Major release

### Changed
- Changed namespace URI to `http://informationexchange.org/ont/ies/common/`

## [4.4.0] - 2025-11-29

### Added
- Added GeoSPARQL extension to Location pattern

## [4.3.3] - 2025-03-28

### Fixed
- Replaced (unresolvable) `sparx:guid` property with `dcterms:identifier`

## [4.3.2] - 2025-02-13

### Fixed
- Add missing `ies:powertype` properties to the ontology
- Correct the domain of `ies:assessed` to `ies:Assessment`

## [4.3.1] - 2025-03-03

### Changed
- License change from Apache 2 to MIT

## [4.3.0] - 2024-12-16 — Changes resulting from project engagements

### Added
- Stuff and Count pattern, including:
  - `Stuff` class
  - `FiniteClassOfElement` class
  - `finiteMembershipCount` attribute
  - `pluriverse` as an instance of Element
  - Example usage
- Replaceable Parts pattern, including:
  - `ReplaceablePart` class
  - `InstalledState` class as a superclass of `InPost` (non-breaking)
  - Example usage
- `Assessment` as a new superclass of `AssessToBeTrue` (non-breaking)

### Changed
- `ParticularPeriod` URI pattern now mandated to be non-punctuated encoding (20070118T153000Z)
- `ParticularPeriod` mandated to be in UTC / Zulu time
- Updated comment for `RecurringPeriod`
- `ExchangedItem` changed to `Thing` with updated definition
- `VersionNumber` definition updated to apply to anything identifiable
- `currencyDenomination` no longer a subProperty of `relationship` and `rdf:type`
- `hasTheme` domain changed from Investigation, Communication and Meeting to Event only
- Removed all references of `PersonOrOrganisation` (updated to `ResponsibleActor`)
- `Marriage` no longer a subClassOf `LawEnforcement`
- Latitude and Longitude specified to be `xsd:decimal` literals

### Fixed
- `regionCountry`, `addressRegion` deleted (use `inLocation` instead)
- `isCentroidOf` corrected from being a subProperty of `relationship` to `inLocation`
- `MapGridArea` no longer an Asset as well as a Location
- `RadioCoverageArea` no longer an Asset as well as a Location
- `happensIn`, `takesPlaceIn` deleted (use `inLocation` instead)
- `storedIn` deleted (use `inLocation` instead)
- Correction to `allHaveDisposition` `rdfs:Domain` - fixed to `ClassOfElement` not `Element`
- Currency identifier corrected to `ISO4217Code` not `ISO639-3Code`
- Message definition corrected
- Inclusion of missing powertype relations between Elements and ClassOfElements

### Removed
- `installedSoftware` (replaced with `InstanceOfSoftware`)
- `ModelOfDevice` and `ClassOfDevice`
- `isParticipantStateIn` (just use `isParticipantIn`)
- Various ClassOfElement extensions and special forms of `rdf:type` to encourage Element-based extensions

## [4.2.0]

### Added
- Possible Worlds Model (placeholder for modal logic)
- `CriminalOrganisation` - subtype of `OrganisationState`
- `LawEnforcementOrganisation` - subtype of Organisation
- `ClassOfOperation` for managing operation taxonomies
- Authorisation model framework
- `EventState`, `staysAt`, `VersionOfDocument`, `NetworkInterface`
- `RadioMast`, `CellularBaseStation`, `RadioCoverageArea`
- `MapGridArea`, `OSGridReference`, `Easting`, `Northing`
- `nephewOrNieceOf`, `cousinOf`
- `Team`, `Department`, `ClassOfOrganisation`, `OrganisationIdentifier`
- `Accent`, `DocumentSection`
- `AuthorisationDocument`, `RequestDocument`
- `EncodedData`, `JsonData`

### Changed
- `TerroristOrganisation` now a subtype of `OrganisationState`
- `make` and `serialNumber` now properties of Asset rather than Device
- Removed "model" property (now use `rdf:type`)

## [4.1.0]

### Added
- Observation pattern
- Rights and Reservations
- `AssessToBeTrue` and `PossibleWorld` models
- Disposition: Capability and Tendency
- `payLoadContents` relationship
- `GeoRepresentation`, `ISO19125-WKT`, `GeoJSON`
- `GeoPoint` supertype of `PointOnEarthSurface`

### Changed
- Device classes replace attributes
- Currency model revised to use classes
- Documents: `DocumentFormat` added, dates use objectProperties
- Person: Gender now a Class
- `Actor` and `ResponsibleActor` replace `PersonOrOrganisation`
- Characteristics and measures model added

## [4.0.0] — First official release

### Added
- `SubjectOfInterest` for inter-agency data exchange
- `isPrimaryForOrganisation`
- `Attendance` subtype of `Presence`
- `Duration`
- `OnlineArtefactInEvent`, `Cookie`, `cookieOnDevice`
- Subtypes of `CommunicationsAccount`
- `hostedOn` relationship
- `ClassOfState`, Roles and Posts
- `OnlineAccountState`

### Changed
- Renamed `iso3166-1Alpha-3` to `iso3166_1Alpha_3`
- Renamed `UN-LOCODE` to `UN_LOCODE`
- Reversed direction of all representation relationships
- `PeriodOfTime` fixed with `ArbitraryPeriod`
- URI now all upper-case

### Fixed
- `vehicleIdentificationNumber` changed to Identifier
- `bookingReference` changed to Identifier
- Various IDs and Names in Online diagram changed to Names and Identifiers

### Removed
- `WholeLifeState`

---

*© Crown Copyright 2020-2025*
