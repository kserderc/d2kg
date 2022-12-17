# d2kg ontology

**d2kg: An Integrated Ontology for Knowledge Graph-based Representation of Government Decisions and Acts**

##  d2kg scope
The d2kg ontology is a unique integration of existing ontologies combined with core and controlled vocabularies developed based on EU standards. It provides a customized solution to abide by the requirements of the Greek Programme Diavgeia, extending significantly the respective Diavgeia ontology and proposing
at the same time a solution to encode government and administrative decisions/acts that could be universally adopted to integrate public documents produced by other EU Member States, with certain adjustments contentwise.

##  d2kg Visualization
The integrated ontology d2kg includes the appropriate ontologies, core and controlled vocabularies. A graphical UML representation of the main entities and their relationships is provided below.

![d2kg](https://user-images.githubusercontent.com/62211813/208238319-27de2df2-03d1-46f5-b14b-b75973f07bf9.png)


At the level of the main ontologies and vocabularies, the ISA core vocabularies are shown in green, the ePO in orange and the main classes of the Diavgeia ontology in grey, whereas the controlled vocabularies in blue. The blue continuous lines show existing connections between different classes via their properties, whereas the purple non-continuous lines indicate potential new connections that can be established with the re-use of existing
properties. For instance, the property ’hasProcurementValue’ can connect a Diavgeia decision of type dvg:Award with the class epo:Value. It is evident that the focus is on the re-use of existing classes, object and data properties from the imported ontologies, along with additional ones for the purpose of extracting valuable information from Diavgeia decisions and Acts. The majority of data and object properties derives from the ePO and the Diavgeia
ontology.

##  Reuse of Existing Resources

The d2kg integrates entities from:

- Diavgeia ontology (DiavgeiaRedefined Project) (https://github.com/ThemisB/diavgeiaRedefined/tree/master/rdf)

- ELI ontology (https://eur-lex.europa.eu/eli-register/about.html)

- Greek Administrative Geography ontology (https://pergamos.lib.uoa.gr/uoa/dl/frontend/file/lib/default/data/1324504/theFile)

- e-Government Core Vocabularies: Core Person Vocabulary,  Core Location Vocabulary, Core Public Organization Vocabulary (https://ec.europa.eu/isa2/solutions/core-vocabularies_en/)

- W3C Organization Ontology (https://www.w3.org/TR/vocab-org/)

- E-procurement ontology (ePO) (https://github.com/OP-TED/ePO)

## d2kg Classes

The ontology is built on re-used classes of the imported individual ontologies, as well as additional ones. We will describe the commonly deployed per ontology below. 

### Diavgeia ontology

Overall, all classes of Diavgeia are integrated in the newly developed ontology. These are extensively analysed in the corresponding repository of the DiavgeiaRedefined Project (https://github.com/ThemisB/diavgeiaRedefined/tree/master/rdf). 

The basic ones are listed below:

• LegalResource: the core Class representing the Decisions and Acts of Diavgeia based on their formal classification according to the Diavgeia Programme;

• Expense: the most common entity used to represent financial transactions; it is used by the following decision types following the notation of the Diavgeia Ontology: Award, Contract, DeclarationSummary, DonationGrant, ExpenditureApproval, OwnershipTransferOfAssets, WorkAssignmentSupplyServicesStudies, PaymentFinalisation, GeneralSpecialSecretaryMonocraticBody.

All the above involve a financial aspect (relevant to monetary transaction) which implies the need for a separate class to encode accompanying data such as the involved parties, amount etc.

### ePO ontology

A summarization of the main entities (https://github.com/OP-TED/ePO/tree/v2.0.1/v2.0.1):

• Agent: A person, an organization, or a system that act in procurement or have the power to act in procurement; This is the respective class from the FOAF ontology, as integrated in ePO;

• Amount: to represent amounts related to procurement procedures;;

• ContactPoint: Details used to reach an organisation: a role, email address, telephone number, etc. This is the respective class from schema.org integrated in the ePO. It can prove very useful in the current implementation, as the Decisions/Acts normally have a Contact Person (Point) to be reached by the citizens;

• Contract: A voluntary, deliberate, and legally binding agreement between two or more competent parties; This class can be employed for contractual agreements among different organizations or between organizations and individuals;

• Fund: A financial resource used to support the procurement. In the context of EU, funds can be divided into programmes, actions and projects. Examples of EU funds are: the European Structural and Investment Funds, European Social Fund (ESF), the Connecting Europe Facility (CEF) programme, or the ISA2 programme and its actions. Funds may change between the lot and the contract, for example in the case of an emergency crisis, a contract mayfinanced by a budget that was not foreseen in the call;

• Lot: A qualitative, quantitative or strategic subdivision of the goods, services or works to be procured, allowing the award of one or more contracts; It refers to a common term used in public procurement.

• Period: A time interval or a duration, usually consisting of a start and an end date;

• Purpose: the description of the objectives related to a procurement;

• Tender: Information submitted by the economic operator to specify its offer regarding one or more lots or the whole procedure, in response to the call for tender;

• Tender Lot: Part of the tender that applies to the related lot;

• Value: Value of an asset, normally expressed as Amount.

### e-Government Core Vocabularies

(https://joinup.ec.europa.eu/collection/semantic-interoperability-community-semic/solution/e-government-core-vocabularies/release/27052019)

Core Public Organization vocabulary

• Contact Point: A class representing a point of contact for the organization. The Core Public Organization Vocabulary denes properties for telephone number, e-mail address and opening hours although it is noteworthy that the class is based on schema.org’s Contact Point class that has additional properties that some implementations may find useful;

• Public Organization: a class that represents the Organization. One Organization may comprise several sub-organizations and any organization may have one or more organizational units. Each of these is described using the same properties and relationships; In the context of this implementation, we use this class for Decisions/Acts issued by Public Administration (this could be interchangeably used with the class Organization of the Organization Ontology in a wider context; In the RDF release of the CPOV, hasUnit is bound to org:hasUnit and unitOf is bound to org:unitOf).

#### Core Person vocabulary

• Person: An individual person who may be dead or alive, but not imaginary. It is that restriction that makes person: Person a sub class of both foaf:Person and schema:Person which both cover imaginary characters as well as real people.


#### Core Location vocabulary

• Address: the Address class is defined in the Location Core Vocabulary. Its properties are closely bound to the INSPIRE data model for addresses. In particular, it separates out building names and numbers from the name of the thoroughfare. this is in contrast to VCard which conflates them into ’street address.’ The Location Core Vocabulary does,however, borrow the fullAddress property from VCard as a means of providing the full text of the address as a literal;

• Location: dcterms:Location class fully represents the ISA Programme Location Core Vocabulary class of Location.

## d2kg object properties

The most important object properties per ontology introduced are:

### Diavgeia ontology

• has expense: has expense links a certain decision type with an Expense;

• has expense with kae: links one of the corresponding Decision types (CommisionWarrant, Undertaking) with an Class ExpenseWithKae;

• signed by: signed by links a Legal Resource (decision type) with a Signer; there is an equivalent property in ePO ontology as well.

### ePO ontology

• actsOnBehalfOf: to identify usually the Signer, the person who has is legally designated to represent an organization/ inverse of ’delegatesAncillaryActivitiesOn’;

• appointedBy: can be used in acts related to appointment of new staff to organizations/inverse of ’appoints’;

• funds: represents the relationship between the Funding source (source of funding,i.e. European or National Budget) and the recipient organization. Funds may change between the lot and the contract, for example in the case of an emergency crisis, a contract maybe financed by a budget that was not foreseen in the call/inverse of ’is funded by’;

• hasAwardCriterionType: the determining criterion for awarding the tender to a candidate contractor (lowest price, cost, quality); important to be communicated to candidate contractors.

• hasDuration: the duration of a contract;

• hasProcurementValue: used in the context of Contractual binding agreements; It refers to the initially set value at the time the tender is announced. At contract time, this procurement value may be different from the Procurement Value of a Lot or a Procedure that was announced. Associated with the Class Value

• hasAwardedEstimatedValue: can be used when a procurement procedure is launched, e.g. a tender, to notify on the estimated value, available amount of the contract to be procured (this can be higher than the actual contracted amount on the basis of received contractors’ quotations);

• hasAwardedValue: the value of the procurement provided by the Award Decision, i.e. the actual value awarded to the contractor when the procurement is concluded;

• hasSelectionCriterionType: serving as the property to highlight the legal requirements for a contractor to take part in the procurement;

• hasOpeningPlace: it provides information on the location where the quotations are opened and evaluated; the place where the tenders will be publicly opened. Important for the sake of transparency to be widely communicated, since candidate contractors can be present during the opening of the tenders (range: Address);

• hasOverallAmount: relates the classes Value and Amount to link the generic concept of Value with a corresponding Amount when the asset is expressed as monetary value;

• hasMainActivityType: provides the main activities of the buyers/ the purchasing bodies/associated with contracting authorities;

• hasMainClassification: provides the Common Procurement Vocabulary (CPV) values/can substitute/be used interchangeably with the data property dvg:cpv of the Di@vgeia ontology;

• hasLegalBasis: the legal acts relevant (used normally as reference in the decisions/acts) for a given public procurement procedure;

• hasPostalAddress: the postal address predicate connecting the entity Location with theclass Address (to further be used to encode the actual address as data property of the Address Class);

• hasProcedureType: related to the activities leading to the conclusion of public contracts used in public procurement according to the legislation- identifies the type of procedure: ’Open’, ’Competitive Dialogue’, ’Closed’ etc.;

• isCreatedBy: to identify the Issuing Organization (creator) of a Document (Decision/Act in this context);

• includes: refers to tender lots under a tender/inverse of property ’isIncludedIn’;

• isSignedBy: identifies the Signer/inverse of ’is signatory part of’.

### Organization ontology

• hasSubOrganization: to represent hierarchical structures within an Organization, im- portant to identify the organizational units issuing a decision;
• holds: Indicates a Post held by some Agent/inverse of ’heldBy’;

• postIn: Indicates the Organization in which the Post exists.

###  e-Government Core Vocabularies

#### Core Location ontology

• location: The location property links any resource to the Location Class. Asserting thelocation relationship implies only that the domain has some connection to a Location in time or space. It does not imply that the resource is necessarily at that location at the time when the assertion is made.

###  New object Properties

Apart from the integrated properties from standard ontologies it is noteworthy to create new ones to meet requirements not covered by existing properties. The necessity for these new properties comes from the specific type of data that can be retrieved from Diavgeia Decisions/Acts and constitute an initial set that can be further extended depending on the specificities of Di@vgeia Decisions/Acts. They mostly represent relationships between an Organization
and another entity (Organization or Individual/Person).

• appointedIn: expresses the relationship between the Staff/Personnel and the Post where the person/individual is appointed in an organization;

• awardsTo: represents the property relationship between the Funding organization and the recipient organization/inverse of ’isAwardedBy’;

• grantsTo: used to define the relationship between an Organization Sponsor and the Sponsored Organization inverse of ’receivesGrantsBy’;

• receivesGrantOf: defines the type of asset (e.g. amount) one Organization receives;

• staff: represents the Personnel of an Organization; relates an Organization to the Per-sonnel in Appointment Decisions;

• transfer: represents ”We transfer(assets, building)” textual pattern used in Diavgeia docs. It can be used for transfers of assets between entities.

## d2kg data properties

The most characteristic data properties deployed are listed per ontology (with their range inparentheses).

Di@vgeia ontology Most of the data properties of Di@vgeia are imported. A set of the com-monly used are referred below:

• afm: Tax Registration Number/VAT registration number (xsd:string);

• afm type: Tax Registration Number type;

• iun: the internet uploading number, unique identifier for Diavgeia docs (xsd:string);

• fek number: the number of the Government gazette (xsd:string).

### ePO ontology

• amountValue: The numeric value of the amount, including decimals (xsd:decimal);

• hasAwardDecisionDate: The official date of the award decision (xsd:date);

• hasBirthFamilyName: the birth family name of a person (rdfs:Literal);
 
• hasEndDate: The date on which this period ends(xsd:date);

• hasEntryintoForceDate: The date on which the contract enters into force; it is is generally the date on which the fulfillment of the contract begins (xsd:date);

• hasFullName: the full name of a person (rdfs:Literal);

• hasGivenName: the given name of a person (rdfs:Literal);

• hasOpeningDateTime: Date and time for the opening of tenders (xsd:dateTime);

• hasPublicationDate: The date when a record is made publicly available (xsd:date);

• hasReceiptDeadline: The time limit for receiving submissions. This is the deadline by which the buyer must receive submissions (e.g. tenders, requests to participate, clarifications, etc.) and is not the time at which the information is submitted by the economic operator (xsd:dateTime);

• hasReceiptExpressionsDeadline: Time limit for receipt of expressions of interest(xsd:dateTime);

• hasStartDate: The date on which this period begins(xsd:date);

• hasTitle: A short self-descriptive name of the instance of the concept(rdfs:Literal);

• hasUrl: The identifier of a resource (xsd:anyURI);

• hasVATPercentage: VAT percentage (xsd:decimal).

### Organization vocabulary

• birthName: the complete birth name of a person (rdfs:Literal);

• location: Gives a location description for a person within the organization, for example a Mail Stop for internal posting purposes; integrated, but of use only in specific conditions, as apparent by its definition (rdfs:Literal).

### e-Government Core Vocabularies

#### Core Location vocabulary

• addressArea: The name or names of a geographic area or locality that groups a number of addressable objects for addressing purposes, without being an administrative unit. This would typically be part of a city, a neighbourhood or village. The domain of locn:addressArea is locn:Address (rdfs:Literal);

• fullAddress: The complete address written as a string, with or without formating. The domain of locn:fullAddress is locn:Address (rdfs:Literal);

• postCode: The post code (a.k.a postal code, zip code etc.). Post codes are common elements in many countries’ postal address systems. The domain of locn:postCode isblocn:Address (rdfs:Literal).

###  New data properties

It has been judged appropriate to introduce specific data properties as well to accommodate valuable and sometimes critical information encoded in certain decisions, as follows:

• kIMDIS: This stands for the central electronic register of public contracts reference (ΚΗΜ∆ΗΣ ́ in Greek) (rdfs:Literal);

• staffCategory: The Staff Category of the personnel (rdfs:Literal);

• staffRank: The Staff Rank of the personnel (data range: corresponding to four different ranks: Α, Β, Γ, ∆ );

• SAE: This property corresponds to the Decision Type issued for taking over financial commitments at the expense of the Public Investments Program budget ( ΣΑΕ ́ in Greek) (rdfs:Literal);

## d2kg Controlled Vocabularies

Apart from the appropriate classes, object and data Properties, it is significant to introduce re-usability with regards to the terms used by the actual data incorporated via instances. This possible through the the integration of controlled vocabularies ensuring a standardized approach concerning the terms that correspond to predefined values for the properties we deploy.

### EU vocabularies

The developed ontology introduces the publicly available arrangements in different formats as presented in the sub-sections that follow.

### Authority tables

The Authority tables (https://op.europa.eu/en/web/eu-vocabularies/authority-tables) is the structure that provides the consistent information which is relevant for our implementation. Authority tables are used to harmonise and standardise the codes and associated labels used in various environments (web platforms, systems and applications) and to facilitate data exchanges between the institutions involved in decision-making process and more.

#### Selection criterion type

In the domain of public procurement, selection criteria are normally based on a specific legal framework. This table (https://op.europa.eu/en/web/eu-vocabularies/dataset/-/resource?uri=http://publications.europa.eu/resource/dataset/selection-criterion) provides the list of conditions that are concerned for evaluation purposes in terms of the criteria that the candidate contractos should fulfil.

####  Award criterion type

In public procurement, it is important to make available in a standardized manner the awardcriteria types. This is normally part of the relevant decisions concluding the procedures and announcing formally the results. It conforms to the) transparency requirements with regard to public resources allocation as it concerns not only the selected contractors, but the ones not chosen following a procurement procedure, and the wider public. This is made possible through the authority table (https://op.europa.eu/en/web/eu-vocabularies/dataset/-/resource?uri=http://publications.europa.eu/resource/dataset/award-criterion-type with the list of rules to be taken into account for the award decisions. The initial values are those foreseen in the public procurement directives of 2014 (Directives 2014/23/EU, 2014/24/EU and 2014/25/EU) (https://eur-lex.europa.eu/oj/direct-access.html).

#### EU Programme

The EU Programme Authority Table (AT) (https://op.europa.eu/en/web/eu-vocabularies/dataset/-/resource?uri=http://publications.europa.eu/resource/dataset/eu-programme) is a controlled vocabulary providing the list of programmes created and coordinated by the European Union and financially supported by the European Union or, in a few cases, by the contributions from the Member States. It has been developed specifically for the EU Budget as open linked data project. It indicates the authority code and start-use date of each concept and gives labels in all official EU languages. It provides useful insights when used in the context of an ontology to identify sources of funding for instance.

#### Main Activity

A list of values (https://op.europa.eu/en/web/eu-vocabularies/dataset/-/resource?uri=http://publications.europa.eu/resource/dataset/main-activity) to classify the main activities of the buyers. The codes associated with contracting authorities are derived from the top level of the Classification of the functions of the government (COFOG) from the United Nations Statistics Division (https://ec.europa.eu/eurostat/statistics-explained/index.php?title=Glossary:Classification_of_the_functions_of_government_(COFOG)). The codes associated with contracting entities are derived from sectors explicitly falling within the sectoral directive (2014/25/EU Art. 8 - Art. 14) (https://op.europa.eu/en/web/eu-vocabularies/concept/-/resource?uri=http://publications.europa.eu/resource/authority/legal-basis/32014L0025l)

#### Procurement Procedure type

This set (https://op.europa.eu/en/web/eu-vocabularies/dataset/-/resource?uri=http://publications.europa.eu/resource/dataset/procurement-procedure-type) identifies the procurement type selected (open, close, competitive dialogue etc), providing significant information on the procedure requirements to the candidate contractors.

### Taxonomies

A taxonomy (https://op.europa.eu/en/web/eu-vocabularies/taxonomies) is a controlled vocabulary in which all the terms belong to a single hierarchical structure and have parent/child or broader/narrower relationships to other terms, sometimes referred to as a ‘tree’.

### CPV

To make public procurement more transparent and efficient, in 1993 the European Commission drafted the Common Procurement Vocabulary (CPV) (https://op.europa.eu/en/web/eu-vocabularies/dataset/-/resource?uri=http://publications.europa.eu/resource/dataset/cpv).

##  Use Cases

To effectively identify the needs of the end user of a Knowledge based system, whether it is a Knowledge Graph or the (underlying) ontology, one should focus on real applicable use cases. In this section we develop a set of use cases applicable to knowledge extraction.

**Use Case 1: Transparency/Accountability in public money/resources spending**

Accountability for the allocation of public money or -in general resources- at national and EU level is the driving force to develop tools for monitoring the money flow. A characteristic use case is to identify the recipient organizations-economic operators of public money. Di@vgeia, as the main repository for decisions related to the procurement procedures in Greece, is an important source of information. The related Di@vgeia Decisions/Acts can help us iden-
tify the recipient contractors, the volume of awarded budget, the frequency of awarded contracts to specific economic operators so as to establish potential patterns in the awards or even suspicion of preferential treatment.

**Use Case 2: Publicity in public spending**

A use case focusing mostly on the publicity requirements related to the pre-award phase. It is necessary and legally binding in most cases through established procedures at EU and national level that contracting authorities-public organizations announce and publish the calls for tender to economic operators, citizens and third parties. A Knowledge Graph can provide an alternatively source of information for involved parties to collectively gather important info. 
Essential piece of information consists of type of procurement procedure, i.e. open/closed tender, selection and award criteria to be fulfilled by the candidates, a potential break down in tender lots, if applicable. It is also of primary importance that public organizations can be timely and effectively reached to provide feedback on procedural issues. Thererefore, Contact Points information should be available in all possible means of communication (email/telephone/postal address/contact persons) and in this sense modelled by an underlying system (ontology).

**Use Case 3: Efficiency of the decision-making processes** 

In decision-making processes knowledge is the foremost element that contributes to productive results. If we are interested in financial transactions, we could further orientate our search accordingly.

Thus, to obtain an overview of public resources allocation one could be oriented towards cumulative information. To elaborate on critical financial information, the available data can be further broken down to actual budget categories so as to identify where public money is spent, i.e. to which kind of goods, works, equipment, consumables, services etc. This can be done through retrieving related Di@vgeia Award Decisions in order to identify the type of
procurement via the Common Procurement Vocabulary (CPV) values.
In the same manner, one could be interested in specific information concerning PersonnelAppointment procedures by Public Organizations. In this respect, data on the type/category of personnel appointed or the frequency of appointments for a specific public organization could be of interest to the citizens.
Moreover, one could have a specific interest in specific geographic area for certain decisions; for public land usage for instance. This could be related to location based information included in decisions/acts.
In terms of its internal functioning, an organization could collect data on average number of specific figures for types of decisions for statistical reasons and in order to assess certain units (average number of contracts or contracts’ duration)

##  Competency Questions

This is a list of certain indicative Competency Questions (CQs) per Use Case (UC) expressed as SPARQL queries, where the rdf prefix indicates the namespace of the core W3C RDF vocabulary, while the d2kg prefix indicates the namespace of the new ontology.


UC#| Competency Question |      SPARQL
---| ------------------- | ----------------------
UC1| CQ1: For a given organization, which are the top x economic operators/contractors that are recipients of awarded contracts (within a given time period)?|`SELECT (?Org AS ?Contractor (COUNT(distinct(?contract)) AS ?number_of_contracts)`<br/>`where {`<br/>&nbsp;&nbsp;&nbsp;&nbsp;`?contract a dvg:Award;`<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`epo:isCreatedBy dvgo:100054492;`<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`eli:date_publication ?pub date;`<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`dvg:has sponsored ?Org;`<br/>`FILTER (?pub_date ≥ ”2017−01−01” ∧∧xsd:date)}`<br/>`group by ?Org`<br/>` order by desc(?number_of_contracts) LIMIT x`
UC2| CQ3: Which is the full information for the Contact Point for a decision/act (the designated organizational units/person)?|`SELECT distinct ?doc ?URL ?full_name ?Email ?Telephone`<br/>`where {`<br/>&nbsp;&nbsp;&nbsp;`?doc;`<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`epo:isCreatedBy dvgo:100054492;`<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`epo:hasURL ?URL;`<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`eli:responsibility_of_agent ?Contact_Point.`<br/>&nbsp;&nbsp;&nbsp;&nbsp;`?Contact_Point epo:hasFullName ?full_name;`<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`epo:hasEmail ?Email;`<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`epo:hasTelephone ?Telephone.`<br/>
UC3| CQ3: For a given organization, what is the number of persons appointed (within a given period of time)?|`SELECT (COUNT(distinct(?doc)) AS ?number_docs) ?Staff_Category ?Staff ?Post `<br/>`where {`<br/>&nbsp;&nbsp;&nbsp;`?doc a dvg:Appointment;`<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`eli:date_publication ?pub_date;`<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`d2kg:staff ?Staff;`<br/>&nbsp;&nbsp;&nbsp;&nbsp;`?Staff d2kg:staffCategory ?Staff_Category;`<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`d2kg:appointedIn ?Post;`<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`person:birthName ?birthName;`<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`epo:appointedBy dvgo:99221922;`<br/>`FILTER (?pub_date ⩾ ”2015−01−01” ∧∧xsd:date)`<br/>`group by ?Staff_Category ?Staff ?Post`<br/>`order by desc(?number_docs)`


## A Knowledge Graph representation for the Greek Programme Diavgeia

The applicability of the developed d2kg ontology can be demonstrated via Knowledge Graphs to visualize actual government decisions and acts. The developed ontology allows to produce data visualization via a Semantic Graph Database which is compliant with W3C Standards. The Diavgeia typical reference document, derived from the newly developed ontology, can be visualized in the form of a Knowledge Graph via Ontotext GraphDB. 

![Fig_ex](https://user-images.githubusercontent.com/62211813/206919294-2aa7aba5-b684-41aa-b3e0-5c47d6a7205f.png)

We can identify all core elements of this sample decision (properties with their labels). Indicatively:
- the corresponding decision id (iun): ΄6ΤΚΕ46ΜΤΛΡ-ΙΓΕ΄ in the center;
- the decision type: ’Appointment’- in purple on the left hand side;
- the Organization which creates/issues the decision and appoints the Person, right next to the decision id in red:
the ’HELLENIC MINISTRY OF DEVELOPMENT AND INVESTMENTS’( ΥΠΟΥΡΓΕΙΟ ΑΝΑΠΤΥΞΗΣ ΚΑΙ ΕΠΕΝ.
in Greek). The object property labeled ’is created by’ is used to identify the issuing Organization;
- the Organizational Units with their hierarchical structural relationship of the Ministry in the right hand side in
red: ΓΕΝ. Δ/ΝΣΗ ΔΙΟΙΚΗΤΙΚΩΝ ΥΠΗΡΕ., ΔΙΕΥΘΥΝΣΗ ΔΙΑΧΕΙΡΙΣΗΣ & ΑΝΑΠΤ., ΤΜΗΜΑ ΚΙΝΗΤΙΚΟΤΗΤΑΣ
ΥΠΑΛΛ in greek;
- the Person appointed Andrikopoulou Charikleia (Ανδριϰοπούλου Χαρίϰλεια in greek) in red just below the
decision id on the left side.
