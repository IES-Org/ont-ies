# Changelog
All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog][keep-change-log]
and this project adheres to [Semantic Versioning][semver].

## [4.3.3] - 2025-03-28
1. Replaced (unresolvable) `sparx:guid` property with `dcterms:identifier`

## [4.3.2] - 2025-03-13
1. Add missing ies:powertype properties to the ontology
2. Correct the domain of ies:assessed to ies:Assessment

## [4.3.1] - 2025-03-03
1. License change from Apache 2 to MIT

## [4.3.0] - 2024-12-16
- Changes resulting from project engagements
1. Added Stuff and Count pattern, including addition of:
- Stuff class
- FiniteClassOfElement class
- finiteMembershipCount attribute
- pluriverse as an instance of Element
- Added example use
2. Added Replaceable Parts pattern, including addition of:
- ReplaceablePart class
- InstalledState class as a superclass of InPost (non-breaking)
- Added example use
3. Changes to Payloads and Groups pattern:
- (Bug fix) Added rdfs:subClassOf relation between SecurityLabel and rdfs:Resource
- (Bug fix) Added rdfs:subClassOf relation between ExchangedPayload and rdfs:Resource 4. Changes to Posts and Roles pattern:
- Removal of hasRole, Role and OrganisationRole (breaking change). Instead use ReplaceablePart/InPost example
now provided in the same pattern
- Update to definition of InPost now that is also a InstalledState
- Corrected relationship between inPost and Post from isPartOf to isStateOf 5. Changes to Assessment pattern:
- Addition of Assessment as a new superclass of AssessToBeTrue (non-breaking) 6. Changes to Location pattern:
- regionCountry, addressRegion deleted. Use inLocation instead
- isCentroidOf corrected from being a subProperty of relationship to inLocation
- MapGridArea no longer an Asset as well as a Location
- RadioCoverageArea no longer an Asset as well as a Location 7. Changes to Where and When pattern:
- happensIn, takesplaceIn deleted. Use inLocation instead. 8. Changes to Asset pattern
- storedIn deleted. Use inLocation instead.
9. Changes to Communications Device pattern:
- Removal of installedSoftware, replaced with InstanceOfSoftware which can be associated as being installed using
isPartOf.
- Removed ModelOfDevice and ClassOfDevice. Instantiations of ModelOfDevice to be done instead using
subClassOf Device.
- Linked Device to PartNumber using isIdentifiedBy 10. Changes to Period of Time pattern:
- ParticularPeriod URI pattern now mandated to be non-punctuated encoding (20070118T153000Z). This avoids
the use of escape characters in the URI. NOTE: the literal for iso8601PeriodRepresentation remains punctuated.
- ParticularPeriod mandated to be in UTC / Zulu time
- Period of Time diagram changed to reflect changes to URI encoding
- Updates to all examples to include new encoding 11. Changes to Disposition pattern:
- Correction to allHaveDisposition rdfs:Domain - fixed to ClassOfElement not Element
12. Changes to Amount of Money pattern:
- Currency identifier correct to ISO4217Code not ISO639-3Code (country code)
13. Changes to Online and Communication patterns covering Message. Message used to inherit from both OnlineEvent and Communication which didn't make sense considering SMS is a subtype of Message. Changes included:
- Deleted subclass relation between Message and OnlineContentEvent
- Added OnlineMessage class with the definition of "A Message that was sent Online."
- Added OnlineMessage to the OnlineEvent diagram
- Made OnlineMessage a subclass of OnlineContentEvent and Message
- Added Communication class to OnlineEvent diagram
- Changed Message definition from "A Communication or OnlineContentEvent where a message is sent" to "A
Communication where a message is sent"
14. IES 4.2 had ClassOfElements and subProperties of rdf:type which encouraged extending the IES classes via ClassOfElements hierarchy rather than the Elements hierarchy. IES 4.3 prunes some of classes (breaking changes) to discourage this behaviour and encourage one approach of extending IES. This approach is documented in "Extending IES4 2024-03-v1.0 O.pdf". Pruned classes and properties include:
- From Authorisation pattern - AuthorisationEventClass deleted – just use subclasses of AuthorisationRequest or
GrantOfAuthority. Also requestedActivity, grantedActivityType and allAuthorisedAgainst deleted
- From Operational pattern - ClassOfOperationalEvent, ClassOfCriminalActivity and typicallyTargets
- From Criminal pattern - Deleted of special forms of rdf:type, typeOfCriminality. Also deleted OffenceCode.
- From Financial Account pattern - Deleted special forms of rdf:type, financialAccountType
ClassOfFinancialAccount
- From Organisation pattern - Deleted ClassOfResponsibleActor
- From Identity Document pattern - Deleted special form of rdf:type, visaType. Also deleted ClassOfTravelVisa.
- From PaymentArtefact pattern - cardType and ClassOfPaymentArtefact. Just extend PaymentArtifact
- From Business pattern - deleted transferType and ClassOfMoneyTransfer. Instead just extend TravelBooking
- From Online pattern - deleted onlineServiceType and ClassOfOnlineService. Instead just extend OnlineService.
Also deleted ClassOfWebResource.
- From Travel Booking - deleted bookingType and ClassOfTravelBooking
- From Communications Account - deleted ClassOfAccount 15. Other changes:
- ExchangedItem changed to Thing. Its definition has also been changed.
- VersionNumber - update to definition to apply to anything that is identifiable
- currencyDenomination no longer a subProperty of relationship and rdf:type. Its now just a subtype of rdf:type
only.
- isParticipantStateIn deleted. Just use isParticipantIn.
- Removed all references of PersonOrOrganisation. All updated to ResponsibleActor
- Marriage no longer a subClassOf LawEnforcement
- Latitude and Longitude specified to be xsd:decimal literals
- hasTheme no longer domain as Investigation, Communication and Meeting. Now that of only Event
- Updated comment for RecurringPeriod. Changed mention of recurringFrom and recurringUntil to startsIn and
endsIn respectively within the definition of RecurringPeriod. Also corrected the mention of
recurrentPeriodRepresentation from recurrentPeriod in the definition of RecurringPeriod.
- Inclusion of missing powertype relations between Elements and ClassOfElements

## [4.2.0] 
- Changes resulting from project engagements
- Possible Worlds Model Added - placeholder for dealing with modal logic. This will grow over time. Shown on
assessments page.
- TerroristOrganisation now a subtype of OrganisationState to allow for different parties viewing and organisation
as being terrorist at different times. This also allows the assessments model to be used.
- CriminalOrganisation added - subtype of OrganisationState, working in a similar way to TerroristOrganisation
- LawEnforcementOrganisation added - subype of Organisation.
- ClassOfOperation added at request of Home Office Vivace. This enables them to manage multiple taxonomies
of criminal investigations in used throughout the UK and international partners
- Authorisation model added at request of HO Vivace - provides a high-level framework for things like warrants
and other types of authorisations.
- EventState added
- make and serialNumber now properties of Asset rather than Device
- staysAt added to show where a Person stays as opposed to where they legally reside.
- VersionOfDocument added
- NetworkInterface added
- RadioMast and CellularBaseStation added
- RadioCoverageArea added
- MapGridArea and OSGridReference added (requested by Police / Home Office)
- Easting and Northing added (requested by Police / Home Office)
- nephewOrNieceOf and cousinOf added
- Team and Department added to organisation model
- ClassOfOrganisation added (requested by Police / Home Office)
- OrganisationIdentifier added (requested by Police / Home Office)
- Accent added (requested by Police / Home Office)
- DocumentSection added (requested by Police / Home Office)
- AuthorisationDocument and RequestDocument added (requested by Police / Home Office)
- EncodedData and JsonData added (requested by Police / Home Office)
- "model" property removed - now use rdf:type

## [v4.1.0]
- Changes resulting from project engagements
- Device - classes replace attributes - make property now points to Organisation, installedSoftware replaces operatingSystem, model now relates to ModelOfDevice
- Currency model revised to use classes, and link to ISO standard ID and country
- TelephoneCountryCode revised to uses classes and link to Country
- Documents - DocumentFormat added as class, title changed to subclass of Name, publicationDate now an
objectProperty to ParticularPeriod
- DataObject - DataKey becomes an identifier and ObjectName a Name
- IdentityDocument - dates changed to objectProperties pointing at ParticularPeriod. idGender now an
objectProperty. visaType now an objectProperty
- Person - Gender now a Class
- Communication / Online Event - there were two classes for Message - Message and Messaging. Messaging has
been removed.
- vehicleColour now changed to objectProperty (hasColour) and moved up to AssetState
- GeoRepresentation, ISO19125-WKT and GeoJSON added (see Location page)
- Language is now a class and hasLanguageProficiency links a PersonState to their LanguageProficiency - also
inLanguage property added to Representation, and called-out the proficiency as a class in its own right
- PaymentArtefact - branding now relationship to Organisation, cardType now relationship to a Class,
areaOfCoverage now relationship to Location
- AgreementName added - now using naming pattern
- Business - transferType now an objectProperty (relationship)
- CriminalActivity - type of offence now managed as a class, and the offenceCode identifies the Class
- PartNumber now identifier on ModelOfDevice
- serviceIdentifier now TravelServiceIdentifier
- Observation pattern added
- Actor and ResponsibleActor replace PersonOrOrganisation
- serviceType now onlineServiceType and is now an objectProperty
- ClassOfFinancialAccount added. JointAccount added
- bookingMethod now implemented as ClassOfTravelBooking
- paymentMethod (TravelBooking) now replaced using the Trade model
- Rights and Reservations added
- Interest - now modelled as states so that attributes can be attached.
- altitude - now uses the measures and characteristics model
- PointOnEarthSurface, Latitude, Longitude and isCentroidOf added, replacing the old geoIdentity which was a
hangover from IES3 and made no sense in 4.
- hasHeight (person) now uses characteristics and measures model - now PersonHeight
- hasTheme (Investigation, Communication, etc.) added to cover those things that are of interest post-event or
thematically - e.g. the thing being investigated is not involved formally
- Definition for IPAddress still mentioned attribute qualifiers (from v3 of IES) for dealing with IPv4 and IPv6. These
are now subtype of IPAddress
- A very large number of definitions were incomplete, wrong or just missing. These are now fixed
- GeoPoint added - supertype of PointOnEarthSurface - this allows for points above or below the surface of the
earth
- PassengerName, SeatNumber and BoardingCardNumber are now identifiers and names of Passenger
- countryOfRegistration and countryWhereRegistered merged
- A basic model for characteristics, measures and units of measure has been added as the current reliance on
strings and fixed units was seen to be inadequate by users
- PartOfFacility and RoomNumber added
- AssessToBeTrue and PossibleWorld added - straw-man models for working with probabilistic data and scenarios
- Disposition - Capability and Tendency added - way to deal with dispositional properties
- payLoadContents relationship added - provides way to hold more than one payload per file

## [v4.0.0]
- FIRST OFFICIAL RELEASE - Changes resulting from initial release and trial implementations
- Rename iso3166-1Alpha-3 to iso3166_1Alpha_3 - hyphens may cause issues with some programming languages (e.g. Python)
- Rename UN-LOCODE to UN_LOCODE - hyphens may cause issues with some programming languages (e.g. Python)
- Addition of SubjectOfInterest - required for every inter-agency data exchange trial implementation
- Addition of isPrimaryForOrganisation - added to cover things like primary names, primary SOIs, etc. within
context of an organisation
- "venue" attribute on Ticket changed to "venueStatedOnTicket" to make it clear this may not be the final venue of
the event
- Attendance added as subtype of Presence for when the Entity present is a Person (particularly useful with
unidentified people)
- Duration added - this was an oversight. It had been discussed and was supposed to have been added, but
slipped through the net.
- Reversed the direction of all the representation relationships (names, IDs, etc.) as the existing direction was
counter-intuitive in RDF TTL and JSON-LD
- vehicleIdentificationNumber had not been changed to an Identifier before initial release. This was an oversight.
Now corrected.
- bookingReference had not been changed to an Identifier before initial release. This was an oversight. Now
corrected.
- Added knownAssociate to the Social diagram
- isTeacherOf added to Professional diagram
- worksWith reinstated (was taken out in v4, but there are cases where it can't be replaced by organisation and
employedBy)
- PeriodOfTime was causing problems in initial implementations around how to query it. This has now been fixed
with the explicit addition of ArbitraryPeriod and the rationalisation of the attributes used.
- Added OnlineArtefactInEvent to cover when OnlineArtefacts participate in online events
- Added Cookie as an OnlineArtefact and also a relationship called cookieOnDevice
- Changed a lot of IDs and Names in the Online diagram that were attributes into Names and Identifiers.
- URI is now all upper-case
- Added subtypes of CommunicationsAccount - e.g. TelephoneAccount, EmailAccount, etc.
- Added hostedOn relating a WebResourceState to the OnlineService that hosts it
- WholeLifeState removed. Was never needed and was a hangover from early IES 4 development work.
- holderOfAccount direction changed and renamed to holdsAccount
- ClassOfState added to enable Roles
- Roles and Posts added
- OnlineAccountState added to cope with changing screen names, passwords

## v4 Beta 2
- Released December 2018 to wider community for review, including some implementation trials

## v4 Beta 1
- Released September 2018 to IES team for internal review


[keep-change-log]: https://keepachangelog.com/en/1.0.0/
[semver]: https://semver.org/spec/v2.0.0.html
[Unreleased]: https://github.com/IES-Org/repository/compare/v0.1.0...HEAD
[0.1.0]: https://github.com/IES-Org/repository/releases/tag/v0.1.0
