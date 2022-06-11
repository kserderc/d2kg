# d2kg ontology
d2kg-OWL: An Integrated Ontology for Knowledge Graph-based Representation of Government Decisions and Acts

# d2kg scope
The d2kg ontology is a unique integration of existing ontologies combined with core and controlled vocabularies developed based on EU standards. It provides a customized solution to abide by the requirements of the Greek Programme Diavgeia, extending significantly the respective Diavgeia ontology and proposing
at the same time a solution to encode government and administrative decisions/Acts that could be universally adopted to integrate public documents produced by other EU Member States, with certain adjustments contentwise.


# d2kg Visualization
The integrated ontology d2kg includes the appropriate ontologies, core and controlled vocabularies. A
 graphical UML representation of the main entities and their relationships is provided below.

![d2kg](https://user-images.githubusercontent.com/62211813/173181649-a65b2553-4c3d-4c1f-9d27-520edd325057.png)

At the level of the main ontologies and vocabularies, the ISA core vocabularies are shown in green, the ePO in
orange and the main classes of the Diavgeia ontology in grey, whereas the controlled vocabularies in blue. The
blue continuous lines show existing connections between different classes via their properties, whereas the pur-
ple non-continuous lines indicate potential new connections that can be established with the re-use of existing
properties. For instance, the property ’hasProcurementValue’ can connect a Diavgeia decision of type dvg:Award
with the class epo:Value. It is evident that the focus is on the re-use of existing classes, object and data properties
from the imported ontologies, along with additional ones for the purpose of extracting valuable information from
Diavgeia decisions and Acts. The majority of data and object properties derives from the ePO and the Diavgeia
ontology.

# Reuse of Existing Resources

The d2kg integrates entities from:

- Diavgeia ontology (DiavgeiaRedefined Project)

- ELI ontology

- Greek Administrative Geography ontology

- e-Government Core Vocabularies: Core Person Vocabulary,  Core Location Vocabulary, Core Public Organization Vocabulary

- W3C Organization Ontology

- E-procurement ontology (ePO)

# Use Cases

implementation is to exploit the knowledge gained through the information extraction process of our model. To effectively identify the needs of the end user of a Knowledge based system, whether it is a Knowledge Graph or the (underlying) ontology, one should focus on real applicable use cases. In this section we develop a set of use cases that could trigger onward the implementation.

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

# Competency Questions

This is a list of indicative Competency Questions (CQs) The CQs are expressed as SPARQL queries, where the rdf prefix indicates the namespace of the core W3C RDF vocabulary, while the ba prefix indicates the namespace of the ontology.

Use Case 1: Transparency/Accountability in public money/resources spending


CQ#| Competency Question |      SPARQL
---| ------------------- | ----------------------
CQ1| For a given organization, which are the top x economic operators/contractors that are recipients of awarded contracts (within a given time period)?|`SELECT (?Org AS ?Contractor (COUNT(distinct(?contract)) AS ?number of contracts)`<br/>`WHERE {`<br/>&nbsp;&nbsp;&nbsp;&nbsp;`?contract a dvg:Award;`<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`epo:isCreatedBy dvgo:100054492;`<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`eli:date publication ?pub date;`<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`dvg:has sponsored ?Org;`<br/>`FILTER (?pub date ≥ ”2017−01−01” ∧ ∧xsd:date)}`<br/>`group by ?Org' 'order by desc(?number of contracts) LIMIT x`
CQ2 |For a given organization, which are the awarded contracts to a specificc economic operator (within a given time period)|`SELECT distinct ?contract (?Amount AS ?Awarded Amount) ?URL ?KIMDIS`<br/>`WHERE {`<br/>&nbsp;&nbsp;&nbsp;`?contract a dvg:Award;`<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`epo:isCreatedBy dvgo:100054492;`<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`epo:hasAwardedValue ?Awarded Value;`<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`eli:date_publication ?pub date;`<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`epo:hasURL ?URL;`<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`dvg:has sponsored〈id〉`<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`d2kg:KIMDIS ?KIMDIS;〉`<br/>&nbsp;&nbsp;&nbsp;&nbsp;`?Awarded Value epo:hasOverallAmount ?OverallAmount.`<br/>&nbsp;&nbsp;&nbsp;&nbsp;`?OverallAmount epo:hasAmountValue ?Amount.`<br/>`FILTER (?pub date ≥ ”2017−01−01” ∧∧xsd:date)}`<br/>`group by ?Org' 'order by desc(?number of contracts) LIMIT x`





