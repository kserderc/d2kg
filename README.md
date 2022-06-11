# d2kg ontology
d2kg-OWL: An Integrated Ontology for Knowledge Graph-based Representation of Government Decisions and Acts

# d2kg scope
The d2kg ontology is a unique integration of existing ontologies combined with core and controlled vocabularies developed based on EU standards. It provides a customized solution to abide by the requirements of the Greek Programme Diavgeia, extending significantly the respective Diavgeia ontology and proposing
at the same time a solution to encode government and administrative decisions/Acts that could be universally adopted to integrate public documents produced by other EU Member States, with certain adjustments contentwise.


# d2kg Visualization
The integrated ontology d2kg includes the appropriate ontologies, core and controlled vocabularies. A
 graphical UML representation of the main entities and their relationships is provided in Figur below.

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

# Competency Questions

This is a list of indicative Competency Questions (CQs) The CQs are expressed as SPARQL queries, where the rdf prefix indicates the namespace of the core W3C RDF vocabulary, while the ba prefix indicates the namespace of the ontology.

Use Case 1: Transparency/Accountability in public money/resources spending


CQ# | Competency Question | SPARQL
--- | ------------------- | ------
-CQ1 |  For a given organization, which are the top x economic operators/contractors that are recipients of awarded contracts (within a given time period)? | `SELECT (?Org AS ?Contractor) (COUNT(distinct(?contract)) AS ?number of contracts)`<br/>`WHERE {`<br/>&nbsp;&nbsp;&nbsp;&nbsp;`?contract a dvg:Award;`<br/>&nbsp;&nbsp;&nbsp;&nbsp;`epo:isCreatedBy dvgo:100054492;`<br/>&nbsp;&nbsp;&nbsp;&nbsp;`?eli:date publication ?pub date;` `<br/>&nbsp;&nbsp;&nbsp;&nbsp;`FILTER (?pub date ≥ ”2017 − 01 − 01” ∧ ∧xsd : date)`}<br/>&nbsp;&nbsp;&nbsp;&nbsp;` group by ?Org order by desc(?number of contracts) LIMIT x}`<br/>`}`








