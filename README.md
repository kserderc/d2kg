# d2kg ontology
d2kg-OWL: An Integrated Ontology for Knowledge Graph-based Representation of Government Decisions and Acts

##  d2kg scope
The d2kg ontology is a unique integration of existing ontologies combined with core and controlled vocabularies developed based on EU standards. It provides a customized solution to abide by the requirements of the Greek Programme Diavgeia, extending significantly the respective Diavgeia ontology and proposing
at the same time a solution to encode government and administrative decisions/Acts that could be universally adopted to integrate public documents produced by other EU Member States, with certain adjustments contentwise.


##  d2kg Visualization
The integrated ontology d2kg includes the appropriate ontologies, core and controlled vocabularies. A graphical UML representation of the main entities and their relationships is provided below.

![d2kg](https://user-images.githubusercontent.com/62211813/173181649-a65b2553-4c3d-4c1f-9d27-520edd325057.png)

At the level of the main ontologies and vocabularies, the ISA core vocabularies are shown in green, the ePO in orange and the main classes of the Diavgeia ontology in grey, whereas the controlled vocabularies in blue. The blue continuous lines show existing connections between different classes via their properties, whereas the purple non-continuous lines indicate potential new connections that can be established with the re-use of existing
properties. For instance, the property ’hasProcurementValue’ can connect a Diavgeia decision of type dvg:Award with the class epo:Value. It is evident that the focus is on the re-use of existing classes, object and data properties from the imported ontologies, along with additional ones for the purpose of extracting valuable information from Diavgeia decisions and Acts. The majority of data and object properties derives from the ePO and the Diavgeia
ontology.

##  Reuse of Existing Resources

The d2kg integrates entities from:

- Diavgeia ontology (DiavgeiaRedefined Project)

- ELI ontology

- Greek Administrative Geography ontology

- e-Government Core Vocabularies: Core Person Vocabulary,  Core Location Vocabulary, Core Public Organization Vocabulary

- W3C Organization Ontology

- E-procurement ontology (ePO)

## d2kg Classes

The ontology is built on re-used classes of the imported individual ontologies, as well as additional ones. We will describe the commonly deployed per ontology below. 

### Diavgeia ontology

Overall, all classes of Di@vgeia are integrated in the newly developed ontology. These are extensively analysed in the corresponding repository of the DiavgeiaRedefined Project https://github.com/ThemisB/diavgeiaRedefined/tree/master/rdf. 

The basic ones are listed below:

• LegalResource: the core Class representing the Decisions and Acts of Diavgeia based on their formal classification according to the Diavgeia Programme;

• Expense: the most common entity used to represent financial transactions4; it is used by the following decision types following the notation of the Di@vgeia Ontology: Award, Contract, DeclarationSummary, DonationGrant, ExpenditureApproval, OwnershipTransferOfAssets, WorkAssignmentSupplyServicesStudies, PaymentFinalisation, GeneralSpecialSecretaryMonocraticBody.

All the above involve a financial aspect (relevant to monetary transaction) which implies the need for a separate class to encode accompanying data such as the involved parties, amount etc.

### ePO ontology

A summarization of the main entities (ref: https://github.com/OP-TED/ePO/tree/v2.0.1/v2.0.1):

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

(ref: https://joinup.ec.europa.eu/collection/semantic-interoperability-community-semic/solution/e-government-core-vocabularies/release/27052019)

Core Public Organization vocabulary

• Contact Point: A class representing a point of contact for the organization. The Core Public Organization Vocabulary denes properties for telephone number, e-mail address and opening hours although it is noteworthy that the class is based on schema.org’s Contact Point class that has additional properties that some implementations may find useful;

• Public Organization: a Class that represents the Organization. One Organization may comprise several sub-organizations and any organization may have one or more organizational units. Each of these is described using the same properties and relationships; In the context of this implementation, we use this class for Decisions/Acts issued by Public Administration (this could be interchangeably used with the class Organization of the Organization Ontology in a wider context; In the RDF release of the CPOV, hasUnit is bound to org:hasUnit and unitOf is bound to org:unitOf).

Core Person vocabulary

• Person: An individual person who may be dead or alive, but not imaginary. It is that restriction that makes person: Person a sub class of both foaf:Person and schema:Person which both cover imaginary characters as well as real people.


Core Location vocabulary

• Address: the Address class is defined in the Location Core Vocabulary. Its properties are closely bound to the INSPIRE data model for addresses. In particular, it separates out building names and numbers from the name of the thoroughfare. this is in contrast to VCard which conflates them into ’street address.’ The Location Core Vocabulary does,however, borrow the fullAddress property from VCard as a means of providing the full text of the address as a literal;

• Location: dcterms:Location class fully represents the ISA Programme Location Core Vocabulary class of Location.


## d2kg Object properties

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

• isSignedBy: identies the Signer/inverse of ’is signatory part of’.

Organization ontology

• hasSubOrganization: to represent hierarchical structures within an Organization, im- portant to identify the organizational units issuing a decision;
• holds: Indicates a Post held by some Agent/inverse of ’heldBy’;

• postIn: Indicates the Organization in which the Post exists.

## e-Government Core Vocabularies

Core Location ontology

• location: The location property links any resource to the Location Class. Asserting thelocation relationship implies only that the domain has some connection to a Location in time or space. It does not imply that the resource is necessarily at that location at the time when the assertion is made.

##  New Object Properties

Apart from the integrated properties from standard ontologies it is noteworthy to create new ones to meet requirements not covered by existing properties. The necessity for these new properties comes from the specific type of data that can be retrieved from Diavgeia Decisions/Acts and constitute an initial set that can be further extended depending on the specificities of Di@vgeia Decisions/Acts. ey mostly represent relationships between an Organization
and another entity (Organization or Individual/Person).

• appointedIn: expresses the relationship between the Staff/Personnel and the Post where the person/individual is appointed in an organization;

• awardsTo: represents the property relationship between the Funding organization and the recipient organization/inverse of ’isAwardedBy’;

• grantsTo: used to dene the relationship between an Organization Sponsor and the Sponsored Organization inverse of ’receivesGrantsBy’;



##  Use Cases

To effectively identify the needs of the end user of a Knowledge based system, whether it is a Knowledge Graph or the (underlying) ontology, one should focus on real applicable use cases. In this section we develop a set of use cases applicable to knowledge extraction.

Use Case 1: Transparency/Accountability in public money/resources spending

Accountability for the allocation of public money or -in general resources- at national and EU level is the driving force to develop tools for monitoring the money flow. A characteristic use case is to identify the recipient organizations-economic operators of public money. Di@vgeia, as the main repository for decisions related to the procurement procedures in Greece, is an important source of information. The related Di@vgeia Decisions/Acts can help us iden-
tify the recipient contractors, the volume of awarded budget, the frequency of awarded contracts to specific economic operators so as to establish potential patterns in the awards or even suspicion of preferential treatment.

Use Case 2: Publicity in public spending

A use case focusing mostly on the publicity requirements related to the pre-award phase. It is necessary and legally binding in most cases through established procedures at EU and national level that contracting authorities-public organizations announce and publish the calls for tender to economic operators, citizens and third parties. A Knowledge Graph can provide an alternatively source of information for involved parties to collectively gather important info. 
Essential piece of information consists of type of procurement procedure, i.e. open/closed tender, selection and award criteria to be fulfilled by the candidates, a potential break down in tender lots, if applicable. It is also of primary importance that public organizations can be timely and effectively reached to provide feedback on procedural issues. Thererefore, Contact Points information should be available in all possible means of communication (email/telephone/postal address/contact persons) and in this sense modelled by an underlying system (ontology).

Use Case 3: Efficiency of the decision-making processes 

In decision-making processes knowledge is the foremost element that contributes to productive results. If we are interested in financial transactions, we could further orientate our search accordingly.

Thus, to obtain an overview of public resources allocation one could be oriented towards cumulative information. To elaborate on critical financial information, the available data can be further broken down to actual budget categories so as to identify where public money is spent, i.e. to which kind of goods, works, equipment, consumables, services etc. This can be done through retrieving related Di@vgeia Award Decisions in order to identify the type of
procurement via the Common Procurement Vocabulary (CPV) values.
In the same manner, one could be interested in specific information concerning PersonnelAppointment procedures by Public Organizations. In this respect, data on the type/category of personnel appointed or the frequency of appointments for a specific public organization could be of interest to the citizens.
Moreover, one could have a specific interest in specific geographic area for certain decisions; for public land usage for instance. This could be related to location based information included in decisions/acts.
In terms of its internal functioning, an organization could collect data on average number of specific figures for types of decisions for statistical reasons and in order to assess certain units (average number of contracts or contracts’ duration)

##  Competency Questions

This is a list of indicative Competency Questions (CQs) The CQs are expressed as SPARQL queries, where the rdf prefix indicates the namespace of the core W3C RDF vocabulary, while the ba prefix indicates the namespace of the ontology.



UC#| Competency Question |      SPARQL
---| ------------------- | ----------------------
UC1| CQ1: For a given organization, which are the top x economic operators/contractors that are recipients of awarded contracts (within a given time period)?|`SELECT (?Org AS ?Contractor (COUNT(distinct(?contract)) AS ?number of contracts)`<br/>`where {`<br/>&nbsp;&nbsp;&nbsp;&nbsp;`?contract a dvg:Award;`<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`epo:isCreatedBy dvgo:100054492;`<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`eli:date publication ?pub date;`<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`dvg:has sponsored ?Org;`<br/>`FILTER (?pub date ≥ ”2017−01−01” ∧ ∧xsd:date)}`<br/>`group by ?Org`<br/>` order by desc(?number of contracts) LIMIT x`
UC2| CQ3: Which is the full information for the Contact Point for a decision/act (the designated organizational units/person)?|`SELECT distinct ?doc ?URL ?full_name ?Email ?Telephone`<br/>`where {`<br/>&nbsp;&nbsp;&nbsp;`?doc;`<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`epo:isCreatedBy dvgo:100054492;`<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`epo:hasURL ?URL;`<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`eli:responsibility_of_agent ?Contact_Point.`<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`?Contact_Point epo:hasFullName ?full_name;`<br/>&nbsp;&nbsp;&nbsp;&nbsp;`epo:hasEmail ?Email;`<br/>&nbsp;&nbsp;&nbsp;&nbsp;`epo:hasTelephone ?Telephone.`<br/>
UC3| CCQ3: For a given organization, what is the number of persons appointed (within a given period of time)?|`SELECT (COUNT(distinct(?doc)) AS ?number_docs) ?Staff_Category ?Staff ?Post `<br/>`where {`<br/>&nbsp;&nbsp;&nbsp;`?doc a dvg:Appointment;`<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`eeli:date_publication ?pub_date;`<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`d2kg:staff ?Staff;`<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`?Staff d2kg:staffCategory ?Staff_Category;`<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`d2kg:AppointedIn ?Post;`<br/>&nbsp;&nbsp;&nbsp;&nbsp;`person:birthName ?birthName;`<br/>&nbsp;&nbsp;&nbsp;&nbsp;`epo:appointedBy dvgo:99221922;`<br/>`FILTER (?pub date ⩾ ”2015 − 01 − 01” ∧∧xsd : date)`<br/>`group by ?Staff_Category ?Staff ?Post'<br/> order by desc(?number_docs)`





