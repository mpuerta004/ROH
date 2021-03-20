| ![](RackMultipart20210319-4-78hqcd_html_aa5ff5100fffb202.png) | ![](RackMultipart20210319-4-78hqcd_html_6bee33aab9ac9973.png)
FONDO EUROPEO DE DESARROLLO REGIONAL (FEDER)_ **Una manera de hacer Europa** _ |
 | ![](RackMultipart20210319-4-78hqcd_html_995201747b0f1c8.gif) |
| --- | --- | --- | --- |

![](RackMultipart20210319-4-78hqcd_html_d703f8b3839e5f78.png)Bilbao, Marzo de 2021

##
**# Ontology documentation**

# Contents

[**1.**** Ontological design** 2](#_Toc67045325)

[**1.1.** Conceptual diagram of ontology ROH 4](#_Toc67045326)

[**1.2.** Modules in ROH network of ontologies 5](#_Toc67045327)

[**1.3.** Entity Project 6](#_Toc67045328)

[**1.4.** Entity Person 9](#_Toc67045329)

[**1.5.** Organization entity 13](#_Toc67045330)

[**1.6.** Funding entity 17](#_Toc67045331)

[**1.7.** Research Object Entity 20](#_Toc67045332)

[**1.8.** Activity entity 25](#_Toc67045333)

[**1.9.** Other entities in ROH 28](#_Toc67045334)

[**Bibliography** 29](#_Toc67045335)

1.
## **Ontological design**

This section is going to break down from minor to major detail the design of the ROH ontology network. Starting in section 1 with a high-level diagram, the most important entities will be shown. Then, the main entities modelled are broken down (sections 1.3 to 1.8). Before, the following table shows a summary of the reused ontologies together with their respective user licenses. All reused ontologies have been evaluated for compatibility with their import and extension.

| prefix | Ontology names | License | Ontology website |
| --- | --- | --- | --- |
| **bibo** | Bibliographic Ontology | Creative Commons Attribution 1.0 Generic (CC BY 1.0) | [http://purl.org/ontology/bibo](http://purl.org/ontology/bibo) |
| **foaf** | FOAF (Friend of a Friend) Vocabulary Specification | Creative Commons Attribution License 1.0 | [http://xmlns.com/foaf/0.1](http://xmlns.com/foaf/0.1) |
| **geonames** | Geonames ontology | Creative Commons Attribution License 3.0 | [http://www.geonames.org/ontology#](http://www.geonames.org/ontology) |
| **obo** | Open Biological and Biomedical Ontology (OBO) | Creative Commons Attribution License 4.0 | [http://purl.obolibrary.org/obo/](http://purl.obolibrary.org/obo/) |
| **obo-bfo** | OBO Foundry, Basic Formal Ontology | Creative Commons Attribution License 4.0 | http://www.obofoundry.org/ontology/bfo.html |
| **obo-ero** | OBO Foundry, eagle-i Research Resource Ontology (ERO) | Creative Commons Attribution License 4.0 | https://open.catalyst.harvard.edu/wiki/display/eaglei/Ontology |
| **obo-iao** | OBO Foundry, Information Artifact Ontology | Creative Commons Attribution License 4.0 | https://github.com/information-artifact-ontology/IAO/ |
| **obo-ro** | OBO Foundry, Relations Ontology | Creative Commons Attribution License 4.0 | http://www.obofoundry.org/ontology/ro.html
 |
| **rdfs** | RDF Schema | Creative Commons Attribution License 4.0 | [http://www.w3.org/2000/01/rdf-schema#](http://www.w3.org/2000/01/rdf-schema) |
| **roh** | Red de Ontologías Hercules | Creative Commons Attribution License 4.0 | [http://purl.org/roh](http://purl.org/roh) |
| **skos** | SKOS Simple Knowledge Organization System RDF Schema | Creative Commons Attribution License 4.0 | [http://www.w3.org/2004/02/skos/core#](http://www.w3.org/2004/02/skos/core) |
| **terms** | DCMI Metadata Terms | Creative Commons Attribution License 4.0 | https://www.dublincore.org/specifications/dublin-core/dcmi-terms/ |
| **vcard** | vCard Ontology - for describing People and Organizations | Creative Commons Attribution License 4.0 | [https://www.w3.org/2006/vcard/ns#](https://www.w3.org/2006/vcard/ns) |
| **vivo** | VIVO Ontology for Researcher Discovery | Creative Commons Attribution License 4.0 | [http://vivoweb.org/ontology/core#](http://vivoweb.org/ontology/core) |

  1.
## Conceptual diagram of ontology ROH

Figura 1shows the main entities modelled in the Hercules Ontology Network (HON in English, ROH-Red de Ontologías Hércules in Spanish). Note that in the diagram, the arrows with a filled tip denote kinship (inheritance) relationships while the arrows that end in a non-filled tip indicate that there is an Object Property relationship between these entities. Finally, the dashed arrows reflect the fact that several entities in ROH have geographic (class Geonames:Feature) and temporal (class vivo:DateTimeInterval) constraints.

![](RackMultipart20210319-4-78hqcd_html_5608441eeb4d47d5.jpg)

**Figura 1**. High level diagram of ROH –Red de Ontologías Hércules.

  1.
## Modules in ROH network of ontologies

The following table lists all ontologies created, which combine entities defined specifically in our core ontology under prefix roh with those reused from other well-known and extensively adopted ontologies. Notice that ROH network of ontologies is divided into 2 main parts as depicted in the following figure:

- The generic ontology, **core module** , contains the most important entities and properties to model information in the academic domain. It contains the central part of the network of ontologies. It covers the academic domain, being agnostic to the country or the research organization whose information wants to be modelled with.
- A set of **vertical modules** which include, on one hand, specializations of some academic concepts for a given country domain. For instance, the figure Associate Professor in the Spanish academic domain would be encountered in the vertical module university-HR-es and is assigned the URI http://purl.org/roh/university-hr/es#ProfesorTitularDeUniversidad. On the other hand, these vertical modules, include controlled vocabularies, according to SKOS ontology, for different important areas in the academic domain, namely, geographical locations (geopolitical) , knowledge areas (including concepts for scientific-domains, subject-areas or unesco-codes), classification of project types (project-classification), resource positions in universities (university-HR for Spain, UK or Portugal), controlled vocabulary with all universities in Spain (university-structure) or some extensions for the Spanish university system (extensions-es).

![](RackMultipart20210319-4-78hqcd_html_c7b1682738a75b43.jpg)

**Figura**  **2**. Hierarchical module structure of ROH network of ontologies.

  1.
## Entity Project

The main ROH entity is vivo:Project (see Figura 3), a new entity defined within ROH. In ROH, a Project models a collaborative activity in business and science that often involves research or design and is carefully planned to achieve a particular goal. Its configuration is inspired by the swrc:Project and takes into account the data properties of the cerif:Project and vivo:Project. It comprises all those properties and adds some new ones, for example, roh:projectStatus, roh:modality or roh:title.

It includes the Data Properties roh:identifier, vivo:abbreviation, vivo:description, roh:title, vivo:freeTextKeyword, roh:modality, roh:foreseenJustificationDate, roh:projectObjective and roh:needsEthicalValidation .

An vivo:Project includes a property roh:hasKnowledgeArea with allows to associate a project with different instances of knowledge areas, e.g. instances of skos:Concept belonging to roh:UNESCOKnowledgeArea controlled vocabulary or concept scheme. Besides, it allows a project also to be classified (roh:hasProjectCategorization) according the project categories defined in hierarchy defined under the concept scheme roh:ProjectClassification, e.g. http://purl.org/roh/project-classification#Horizon2020. Likewise a project might be associated to the recruitment of a new human resource, in that case roh:hasHRClassification allows to link a project with a roh:HumenResourceClassification. A project may go through different stages, i.e. roh:projectStatus during its lifetime, e.g. roh:Open, roh:ProposalSubmitted, roh:Rejected or roh:Closed.

Besides, an instance of a vivo:Project is associated to the following entities through object properties:

- roh:Activity is roh:participatedBy a project, describes what activities a project participates in.
- skos:Concept is linked through roh:knowledgeAreaOf to a project, indicating the topics/concepts a project deals with. A project may be classified according to distinct taxonomies (concept schemes) for roh:ProjectClassification and roh:HRClassification (human resources).
- roh:Dossier through relationship vivo:relates binds a set of documents, including the proposal, evaluation document, reports and so on with a vivo:Project. A dossier is an administrative file collection in which all assets related to a Project are stored, including the Research Proposal, approval documents, viability plans and so on associated to a project are stored.
- roh:Fundingroh:supports a vivo:Project, where funding terms:hasPartroh:FundingAmount. A roh:FundingAmountroh:grantsfoaf:Organization and describes the details about the funding associated to a project, in what period and what organization it funds. A roh:FundingSource is roh:promotedBy a vivo:FundingProgram which is roh:promotedBy a vivo:FundingOrganization.foaf:Organization, where different organizations may play different obo-bfo:Rolesin a project, e.g. vivo:MemberRole or vivo:AdministratorRole. Notice that the object property vivo:relates allows to link a foaf:Agent, being it either an Organization or a Person, with an obo-bfo:Role.
- roh:Justification through relationship vivo:relates binds justifications with a vivo:Project.
- foaf:Person, where an person may play different obo-bfo:Roles, e.g. vivo:PrincipalInvestigatorRole or vivo:ResearcherRole.
- vivo:ProjectContract subtype of vivo:Contract, a project may be associated to a contract through relationship roh:hasContract.
- roh:ProjectExpense is roh:spentBy a project, details allows to associate a project with its expenses.
- roh:ResearchObject, where a project roh:produces several roh:ResearchObject, where some results of a project might be for example of types bibo:Journal, obo-iao:JournalArticle, or roh:PhDThesis.

Notice that a vivo:Project may also be part (vivo:hasPart) of another project, e.g. child of a parent project. Besides, every instance of a vivo:Project is time bound by being associated with an instance of vivo:DateTimeInterval and geographically bound to an instance of gn:Feature (through relationship (gn:locatedIn).

The following table shows the object and data properties associated to vivo:Project:

![](RackMultipart20210319-4-78hqcd_html_96da58563b38bd03.jpg)

![](RackMultipart20210319-4-78hqcd_html_28eaa363347c971f.png)

**Figura**  **3**. Ontological diagram for entity Project.

  1.
## Entity Person

In ROH, there is a foaf:Person entity (see Figura 4) that inherits from foaf:Agent. The specialization of this entity imported from the VIVO ontology already adds some DataType properties of the research domain, but in ROH we also incorporate roh:taxID, roh:ORCID, vivo:researcherId or vivo:scopusId (all of them are subtypes of vivo:identifier, a given person may use or several alternatives of those identifiers) and also several object specific properties of the research domain as &quot;has a Role&quot; (roh:hasRole) in an Organization, &quot;has a CurriculumVitae&quot; (roh:hasCV), &quot;has some Accreditations&quot; (roh:hasAccreditation), &quot;has an Employment Contract&quot; (roh:hasContract), &quot;has some Knowledge Areas&quot; (roh:hasKnowledgeArea) or &quot;has some Roles&quot; (roh:hasRole) in Projects or participates through &quot;bibo:authorList&quot; with Research Objects of subclass bibo:Document. A person can &quot;have different roles&quot; in the Project over time. As a subclass of foaf:Agent inherits some additional object properties such as roh:hasAccreditation or roh:hasContactInfo.

As mentioned above, foaf:Person in ROH is based on FOAF (Friend of a Friend [2], following patterns used in VIVO. That explains why it includes some of the basic FOAF properties such as foaf:name, foaf:nickname, foaf:title, foaf:mbox (note that this in fact an object property), foaf:img (note that this in fact an object property), vivo:description, foaf:firstName and foaf:surname. However, it considers all attributes and links defined in CERIF through the cfPers entity. foaf:Person incorporates the following data properties declared as attributes in cfPers, especially: identifier (vivo:identifier but preferably roh:ORCID), roh:birthdate, foaf:gender, foaf:homepage (note that this in fact an object property), roh:researchLine, vivo:freeTextKeyword. Some important CERIF relationships that have also been adopted: Curriculum Vitae (roh:hasCV) which links foaf:Person with roh:CurriculumVitae, Event (roh:Activity) and Indicator (roh:Accreditation).

Besides, an instance of a foaf:Person is associated to the following entities through object properties:

- roh:AuthorMetric, where a researcher may have associated metric values such as h-index or i10 index.
- roh:AcademicSubject, where a researcher teaches different subjects.
- vivo:AwardedDegree, where a researcher vivo:relates with an roh:AcademicDegree
- roh:Accreditation, where a researcher roh:hasAccreditation of different types, e.g. roh:ResearchAccreditation or roh:AcademicAccreditation.
- roh:Activity, where a researcher roh:participates in diverse activities, e.g. vivo:InvitedTalk or bibo:Conference.
- skos:Concept is linked through roh:knowledgeAreaOf to a person, indicating the different knowledge areas (roh:KnowledgeArea) a researcher is specialized on.
- roh:CurriculumVitae, where a researcher roh:hasCV which includes data type properties like roh:cites, roh:factorH or roh:summary
- bibo:Document, where a researcher through bibo:authorList is participating in a bibo:Document as one of its authors.
- vcard:Individual, where a researcher obo:hasContactInfo described through ontology vcard.
- vivo:Position, where a researcher roh:hasPosition usually in an organization linking it to any of the vivo:Position subclasess like vivo:FacultyAdministrativePosition or vivo:FacultyPosition.
- vivo:PersonExpense, where a researcher may contribute with several expenses for its research activities.
- roh:ResearchObject, where a researcher is the roh:correspondingAuthor of different subtypes of roh:ResearchObject, e.g. obo-iao:JournalArticle, vivo:ConferencePaper or bibo:Proceedings.
- roh:Role, where a foaf:Agent may roh:hasRole like vivo:ResearcherRole or vivo:TeacherRole either in a vivo:Project or a foaf:Organization.
- roh:PersonContract, where a researcher roh:hasContract described according to the attributes corresponding to parent class vivo:Contract.
- bibo:Thesis, where a researcher is roh:supervisorOf of a bibo:Thesis, concretely, any of its subtypes subclasess like roh:MasterThesis or roh:PhDThesis.

The following table fully describes the object and data properties defined within the foaf:Person entity in ROH.

![](RackMultipart20210319-4-78hqcd_html_9915246da8a68bb9.jpg)

![](RackMultipart20210319-4-78hqcd_html_d1f13845f349dc9c.gif)

**Figura 4**. Ontological Diagram for entity Person.

  1.
## Organization entity

An Organization in ROH (see Figura 5) is a foaf:Organization which carries out several vivo:Project. It is a child of foaf:Agent. Some organization can emit roh:Acreditation (e.g. ANECA or CENAI in Spain), those belonging to subclass roh:AccreditationIssuer, or award degrees (vivo:AwardedDegree), those of subclass vivo:University. An Organization may receive several roh:FundingAmount, corresponding to a roh:Funding, obtained through a roh:FundingProgram provided by a vivo:FundingOrganization through a roh:FundingSource. As a foaf:Agent an Organization may be involved in several roh:Actitity, has several instances of attribute vivo:freetextKeyword, is associated through roh:hasKnowledgeArea with roh:KnowledgeArea and bound to a geographical scope through gn:locatedIn with gn:Feature, it may also have a time span through vivo:dateTimeInterval linking it with an instance of vivo:DateTimeInterval.

Based on FOAF [10], the foaf:Organization entity takes into account the data properties (attributes: vivo:abbreviation, foaf:homepage) and data properties (links) defined by the Organization Unit in CERIF. It also takes into account and supports the relationships of CERIF Equipment (via entity vivo:Equipment and object property roh:hasReservable), Event (roh:Activity), Expertise and Skill (via vivo:freeTextKeyword and roh:hasKnowledgeArea), Facility (roh:Facility and roh:hasReservable), Funding (roh:Funding), Organization Unit (kinship relationships between organizations can be established with obo-ro:BFO\_0000051 (has part) and obo-ro:BFO\_0000051 (part of), Prize Award (through roh:Accreditation), Result Patent, Result Product, Result Publication and Service - all of them through roh:ResearchObject which can be obtained through the roh:produces relationship from the Projects in which an organization participates by playing a declared role through roh:hasRole, Person (through roh:hasPosition). Therefore, the CERIF data model for Organization is covered.

An exhaustive hierarchy of organizations is included, e.g. roh:AccreditationIssuer, vivo:Company or vivo:University, among many others.

Besides, an instance of a foaf:Organization is associated to the following entities through object properties:

- roh:Accreditation, where an organization of type roh:AccrediationIssuer issues (roh:issues) accreditations, e.g. roh:ResearchAccreditation or roh:AcademicAccreditation.
- roh:Activity, where an organization may play vivo:OrganizerRole through roh:hasRole in an activity or may through its participation role in a project participate (roh:participates) in an activity.
- vivo:AwardedDegree, where a vivo:University may roh:awards degrees which are related to both a concrete vivo:AcademicDegree and an instance of foaf:Person.
- skos:Concept, where an organization through roh:hasKnowledgeArea may be associated to several knowledge areas, defined as instance data of thesaurus created with SKOS ontology. A concept linked to an organization must necessary belong to roh:KnowledgeArea concept scheme.
- vivo:Company, where an organization might be linked to several spinoffs through object property roh:hasSpinOff.
- vivo:DateTimeInterval, where an organization may exist during a given time interval
- foaf:Document, where an organization may be associated to several homepages foaf:homePage
- gn:Feature through relationship gn:locatedIn, where an organization may be associated a geographical scope.
- roh:FundingAmount where an organization may receive several funding amounts part of a roh:Funding through roh:grants object property.
- vcard:Organization, where an organization obo:hasContactInfo described through ontology vcard.
- roh:Infrastructure, where an organization may roh:hasInfrastructure, belonging to any of its subclasses, e.g. roh:Equipment or roh:Facility.
- foaf:Organization, where a foaf:Organization may be linked through vivo:hasSucessorOrganization or vivo:hasPredecessorOrganization with another foaf:Organization or may be part of (obo-ro:BFO\_0000050 (part of)) or include (obo-ro:BFO\_0000051 (has part)) other several foaf:Organization.
- obo-ero:ERO\_0000005 (Service), where an organization roh:provides several services, e.g. obo-ero:ERO\_0000392 (Storage Service)

Check the following table for more details on object and data properties for foaf:Organization.

![](RackMultipart20210319-4-78hqcd_html_be594263462cdba4.jpg)

![](RackMultipart20210319-4-78hqcd_html_3d7716baf12cb36b.png)

**Figura**  **5**. Ontological diagram for entity Organization.

  1.
## Funding entity

The roh:Funding entity (see Figura 6), new in ROH, represents the funding associated with a project (vivo:Project) whose funding is associated with a funding program (roh:FundingProgram) and comes from a (roh:FundingSource), which in turn is associated with a funding organization (vivo:FundingOrganization). A funding is divided into several amounts (roh:FundingAmount), associated with the different entities that participate in a project and the annuities in which they do so. Funding amounts for an organization in a projects are expressed through data properties roh:monetaryAmount and roh:currency.

A funding can be marked as public through property roh:publicFunding, qualified by properties vivo:identifier, vivo:description and vivo:freeTextKeyword and classified into roh:Grant, roh:Loan, roh:Outsourcing or roh:RefundableAdvance.

The funding organization (vivo:FundingOrganization) (see Figura 6), imported from VIVO [1], inherits from foaf:Organization, promotes (roh:promotes) research through different funding programs (roh:FundingProgram) and through different funding sources (roh:FundingSource). A roh:Funding is associated with roh:FundingAmounts through object property obo-ro:BFO\_0000051 (has part). A roh:FundingProgram funds (roh:funds) a roh:Funding, funding programs are promoted by roh:FundingOrganizations. Notice that a roh:Funding is divided into several roh:FundingAmounts associated with different foaf:Organizations through the roh:grants relationship.

The Funding Program entity (roh:FundingProgram) (see Figura 6), new in ROH, defines the funding initiatives promoted (roh:promotedBy) by a Funding Organization (roh:FundingOrganization) which is, likewise, promoted by a roh:FundingSource. A funding is in operation during a time interval (vivo:dateTimeInterval) and is usually linked to a geographical scope (geonames:Feature) associated to the roh:FundingProgram.

The following table illustrates the object and data properties associated to entities dealing with the funding concept in ROH.

![](RackMultipart20210319-4-78hqcd_html_67cf2d73d0bfda22.jpg)

![](RackMultipart20210319-4-78hqcd_html_5dd123a1415d5dd2.png)

**Figura**  **6**. Ontological diagram for Funding.

  1.
## Research Object Entity

The research object entity (roh:ResearchObject) is a new entity defined in ROH (see Figura 7) that corresponds to a research result generated by a person (researcher), usually through work on a project. Notice that roh:ResearchObject is a defined class, which follows these restrictions: (((roh:correspondingAuthor some foaf:Person) and (roh:hasKnowledgeArea some

(skos:Concept and (skos:inScheme some roh:KnowledgeArea)))) and (roh:correspondingAuthor only foaf:Person) and (roh:hasKnowledgeArea only

(skos:Concept and (skos:inScheme some roh:KnowledgeArea)))) or (roh:producedBy only roh:Project). This is, an instance in ROH belongs to class roh:ResearchObject if it meets these restrictions.

A research object has been modelled around entity obo-iao:IAO\_0000030 (Information Content Entity). Such entity is linked to at least one foaf:Personthrough object property roh:correspondingAuthor. In the case of its subclass bibo:Document, the contributors of a research object are accessible through object property bibo:authorList. Usually a roh:ResearchObject results from working on a vivo:Project (roh:produces). Under obo-iao:IAO\_0000030 (Information Content Entity) entity a complete taxonomy of research objects mostly imported from BIBO [4], covering all kinds of publications, patents, software and web pages, is defined. Some examples are: bibo:Collection, bibo:Journal, bibo:Article, bibo:Book, bibo:Chapter, vivo:DataSet, bibo:Patent, bibo:Thesis and bibo:Webpage. The primary author of a research object is accessible through the roh:correspondingAuthor property. A roh:ResearchObject may have several knowledge areas bound to it through roh:hasKnowledgeArea, where the linked concepts should be associated to concept scheme roh:KnowledgeArea or one of its subclasses. The vertical module knowledge-area contains relevant instance data scientific domains, research subjects and UNESCO codes.

The most important research result is represented by the concept publication and is defined mainly through the imported entity bibo:Document. Currently, the following sets of entities related to the publication concept are supported: bibo:Collection (Newspaper, Magazine) and bibo:Document (Article, ConferencePaper, EditorialArticle, Book, Proceedings, ConferencePaper, Chapter, Thesis). bibo:Thesis has been refined into roh:BachelorsThesis, roh:MastersThesis and roh:PhDThesis.

Two entities worth mentioning that belong to the hierarchy of classes associated to the roh:ResearchProject are: bibo:Report and roh:Dossier. A bibo:Report has been refined to include subclasses roh:EthicalReport (which includes roh:EthicalAudit and roh:EthicalValidation), roh:EvaluationSummary, roh:Justification and roh:ResearchProposal. This implies that a report may correspond to ethical validation and auditing needs of a project, correspond to the evaluation of the project, its proposal or the set of documents corresponding to its justification.

On the other hand roh:Dossier represents a collection of reports related to a vivo:Project, which may include all the types of reports above mentioned.

The below table shows the data and object properties, as well as subclasses, of entity roh:ResearchObject.

![](RackMultipart20210319-4-78hqcd_html_217e6286f227dc79.jpg)

![](RackMultipart20210319-4-78hqcd_html_e74c18866a1d2431.jpg)

![](RackMultipart20210319-4-78hqcd_html_d19e51004c197075.jpg)

![](RackMultipart20210319-4-78hqcd_html_39845d2a291a22af.jpg)

![](RackMultipart20210319-4-78hqcd_html_c8054b7e9f80e321.png)

**Figura**  **7**. Ontological diagram for ResearchObject.

  1.
## Activity entity

The entity research activity (roh:Activity), new in ROH and visualized in Figura 8, represents the activities in which People participate (roh:participes) and organized by Organizations (foaf:Organization) reflected through the roh:hasRole relationship that connects with the intermediary entity vivo:OrganizerRole. Each activity is usually linked to a project through the relationship (roh:participes) and causes a project expenditure linked through (vivo:relates). A detailed hierarchy of activity subtypes is defined below roh:Activity: bibo:Conference, vivo:Course, vivo:Internship or roh:ThesisViva.

Related to Activity, it is also important to describe roh:Expense, which denotes the expenses incurred either by a project (vivo:Project) or person (foaf:Person) and linked through roh:spends. Every expense has a time instant of associated expense (vivo:DateTimeValue) and other properties that qualify it as (roh:monetaryAmount, roh:currency, roh:title or vivo:description. The following subclasses of roh:Expense have been defined: roh:PatentExpense, roh:PesonExpense, roh:ProjectExpense and roh:ResearchObjectExpense. Besides, each expense can have associated a different type of expense through roh:hasExpenseClassification (Congress/network, external recruitment, Investment/inventory, office, other costs, publication, representation or staff expenses).

The following table illustrates the class hierarchy, object and data properties defined by roh:Activity.

![](RackMultipart20210319-4-78hqcd_html_43376860ec21e326.jpg)

![](RackMultipart20210319-4-78hqcd_html_438ab66e0887f341.png)

**Figura**  **8**. Ontological diagram for entity Activity.

  1.
## Other entities in ROH

For more details on other entities in ROH check the tables detailing class hierarchies, object and data properties for all entities defined in ROH at the following PDF file: [https://github.com/HerculesCRUE/ROH/blob/gh-pages/1-%20OntologyDocumentation.pdf](https://github.com/HerculesCRUE/ROH/blob/gh-pages/1-%20OntologyDocumentation.pdf).

## **Bibliography**

[1] «Ontology Reference - VIVO 1.10.x Documentation - LYRASIS Wiki». [En línea]. Disponible en: https://wiki.lyrasis.org/display/VIVODOC110x/Ontology+Reference. [Accedido: 12-feb-2020].

[2] «Current research information system - Wikipedia». [En línea]. Disponible en: https://en.wikipedia.org/wiki/Current\_research\_information\_system. [Accedido: 14-feb-2020].

[3] «CERIF 1.5 Reference». [En línea]. Disponible en: https://www.eurocris.org/Uploads/Web%20pages/CERIF-1.5/cerif.html#cfResProd. [Accedido: 13-feb-2020].

[4] «euroCRIS | Current Research Information Systems». [En línea]. Disponible en: https://www.eurocris.org/. [Accedido: 14-feb-2020].

[5] «SKOS Simple Knowledge Organization System Namespace Document 30 July 2008 &quot;Last Call&quot; Edition». [En línea]. Disponible en: https://www.w3.org/TR/2008/WD-skos-reference-20080829/skos.html. [Accedido: 13-feb-2020].

[6] «Public Procurement Ontology». [En línea]. Disponible en: http://contsem.unizar.es/def/sector-publico/pproc.html. [Accedido: 13-feb-2020].

[7] «CVN». [En línea]. Disponible en: https://cvn.fecyt.es/editor/cvn.html?locale=spa#ENTRADA. [Accedido: 13-feb-2020].

[8] «SWRC-FE (SWRC Funding Extension) | MORElab Ontologies». [En línea]. Disponible en: https://morelab.deusto.es/ontologies/swrcfe. [Accedido: 13-feb-2020].

[9] «GeoNames Ontology - Geo Semantic Web». [En línea]. Disponible en: http://www.geonames.org/ontology/documentation.html. [Accedido: 13-feb-2020].

[10] «FOAF Vocabulary Specification». [En línea]. Disponible en: http://xmlns.com/foaf/spec/. [Accedido: 12-feb-2020].

[11] «Bibliographic Ontology Specification | The Bibliographic Ontology». [En línea]. Disponible en: http://bibliontology.com/. [Accedido: 13-feb-2020].

[12] «OOPS! – OntOlogy Pitfall Scanner!» [En línea]. Disponible en: http://mayor2.dia.fi.upm.es/oeg-upm/index.php/en/technologies/292-oops/index.html. [Accedido: 13-feb-2020].

![](RackMultipart20210319-4-78hqcd_html_adf2bf3d593fc664.gif)

| Documento | Unified ROH Ontology Documentation |
| --- | --- |
| Autor | ![](RackMultipart20210319-4-78hqcd_html_feadf2f7a8b7d165.jpg) ![](RackMultipart20210319-4-78hqcd_html_a81a16d5a9bf17cc.png) | Versión | Fecha |
| 1 | 11/03/2021 |

Página **5** de **7**