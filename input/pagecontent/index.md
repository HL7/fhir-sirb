Data standards to move data and documents from clinical research sites to a single ethics review board in support of the "NIH Policy on the Use of a Single Institutional Review Board for Multi-Site Research".

### Background
Launching a multi-site clinical research study is frequently a long and involved process that can delay the development of potentially effective clinical treatment. Part of this process is applying for and receiving the review and approval of an ethics review board, termed the Institutional Review Board or IRB.  This IRB is reponsible for reviewing all study methodology prior to enrollment of any participants, as well as providing ongoing monitoring of the study. Ethics review and approval processes conducted by IRBs have been cited as a major contributor to delays in initiating multi-site studies. In response, the set of protections for research subjects in the code of federal regulations for human-subjects research (Common Rule, 45 CFR Part 46.114) was revised with a requirement that a single IRB be named when multiple sites are using the same protocol. Rather than each site waiting for approval of a study by its local IRB before enrolling subjects, a single IRB review will expedite approval and improve the timeline for study initiation and completion. Researchers commented about the redundancy of effort, additional costs, and administrative burdens that often lead to delays and imbalances in enrollment of research participants in multi-site clinical studies. Before creating the questionnaires, considerable effort was made to examine and compare the existing forms from a sample set of institutions. In arriving at the versions of the questionnaires in the IG, the content of the forms from the sample set were harmonized and rationalized in conjunction with the Common Rule provisions, where applicable.

### Project Goals
The project is a proof of concept in hopes of moving toward a national standard for the content of the research study forms in widespread use.  As institutions trial these forms, it is expected that the authors will receive considerable feedback on the content of the forms.  

The intent of this project is to use the Structured Data Capture (SDC) features of the Questionnaire resource so that the research study forms are standardized for exchange between the sIRB and the relying institutions, with a national standard being established so that all sIRB studies will use the same content with the same level of granularity in their forms.
![Reviewing and Relying Sites](Cooperative Research Terminology.jpg){:width="900px"}

Right now, research study forms in common use have large text boxes which are not easily integrated with the research study management software, as each text box contains too many different fields of data.  Our design of the forms is novel in that it separates concepts into separate questions, as individual questionnaire items.

The end product of the project consists of the QuestionnaireResponses to be exchanged.  The forms are complete documents with a separate existence from any of the current FHIR resources. The form data elements should be considered in their entirety in the context of the complete document.  The data should be maintained in FHIR format for editing and transmission.

The sIRB questionnaires, if adopted, would be replacing paper forms, word processing documents (eg. MS Word or Google Docs) or off-board study forms software that is not integrated with the institution’s existing research study management software.  The forms would also be independent of any particular form management software, allowing different sites to use the software of their choice so long as that software complies with the FHIR standard.



### Significance
In lieu of ad hoc transfers of PDFs and other document formats via email or online submission, this project utilizes FHIR based standards to facilitate document exchange. A standards enabled process leveraged by software has the potential to significantly decrease the extensive manual tasks that have become associated with using a single IRB system. This use of FHIR standards to meet the need for an efficient exchange of data and documents will improve the operational efficiency. 

### Coverage
This Implementation guide covers the suite of seven research study questionnaires for sIRB studies: Determination Letter Questionnaire, Protocol Questionnaire, Consent Form Questionnaire, Recruitment Materials Questionnaire, Adverse Medical Events Questionnaire, Non-Medical Events Questionnaire and Continuing Review Questionnaire. It also includes an Initiate a Study Questionnaire for an optional, but suggested, implementation that takes advantage of the SDC Populate functionality. The Initiate a Study Questionnaire is intended to collect data for fields common to many of the forms, such as the Study Title, Study Protocol Number, Principal Investigator (PI) Name, PI Address, PI email, PI phone, sIRB site name, sIRB site address and the name and address for each relying site. The SDC Populate functionality can then use the data captured in the Initiate a Study Questionnaire to populate the corresponding fields in the suite of seven research study questionnaires.

### Scope
The sIRB implementation guide deals with creation and exchange of standardized sIRB forms and form responses using FHIR questionnaire and questionnaire response resources. The questionnaires may have nested structures and embed skip/branching logics to display appropriate questions based on previous answers. Extraction of data elements/resources from questionnaire responses is out of scope for the current version of sIRB implementation guide. Extraction can be incorporated into your specific implementation by referring to [Structured Data Capture (SDC) implementation guide](http://hl7.org/fhir/uv/sdc/STU3/extraction.html).

### Assumptions
The implementation guide assumes that the implementer has or will have a capability to send, receive, render and display FHIR questionnaires and questionnaire responses. Implementers may consider using free software such as National Library of Medicine's (NLM) FHIR Questionnaire rendering tool or incorporate these standards into a tool of their own. Exchange of resources can be achieved by any of the FHIR messaging mechanisms. Please refer to FHIR standard documentation, open source implementations of FHIR specifications, and FHIR Messaging for additional information. 

### Design Decisions
Some of the relying sites may be small clinics or rural providers that do not have their own FHIR server.  They may be using paper forms at this time for any research study activities. To allow for easier adoption of the FHIR forms and make it more likely for the smaller sites to transition away from paper forms, it was decided to keep the technical and implementation burden very low.  

In order to keep the implementation burden very low, the project was designed with the intent that the institutions would not be integrating the questionnaires with any of their existing research study management software.  Lists of the research studies, names of principal investigators, names of study participants and all study details would be stored, maintained and searched from within the existing research study management software that already exists at the institutions.  

Some of the institutions may participate in a sIRB study only once every few years. Therefore, they may not want to devote time and money to implementing a large set of FHIR resources if they are not using a FHIR server already if they can get the forms created and transmitted using only Questionnaire and QuestionnaireResponse resources. 

Some of the sites may never implement a FHIR server, instead accessing the forms via web browser using the form viewers and FHIR servers maintained by the lead (sIRB) site. 


A simple JavaScript-based website (sIRB on FHIR) was built as part of the project to demonstrate the ease of implementation.  The code is available at https://github.com/kirubel22/sIRB_Site_New and the website can be viewed at [https://sirb-on-fhir.dev.cloud.duke.edu/](https://sirb-on-fhir.dev.cloud.duke.edu/).

The Questionnaires were built with the free and open source NLM Form Builder available from [https://lhcformbuilder.nlm.nih.gov/](https://lhcformbuilder.nlm.nih.gov/).

The Questionnaires and Questionnaire Responses are rendered with the free and open source Lister Hill Center (LHC) Forms software available from [http://lhncbc.github.io/lforms/](http://lhncbc.github.io/lforms/).  The sIRB on FHIR software uses the JavaScript version of the LHC Forms widget.


All [code sets](codesystems_descriptions.html) are defined within the questionnaire form definitions.  No external valuesets are used. Where concepts in the forms aligned to concepts in existing Code Systems, the existing Code Systems were used to allow for interoperability with resources.  As the forms stabilize, the temporary codes defined in this implementation guide will be submitted to and migrate into other ‘official’ terminologies, such as SNOMED or HL7’s shared terminologies.


As part of the proof of concept, the sIRB on FHIR software creates a ResearchStudy resource in the FHIR server for each research study.  A sample of a ResearchStudy resource created by the sIRB on FHIR software is [included](https://build.fhir.org/ig/HL7/fhir-sirb/ResearchStudy-ResearchStudy2858.html).  In the future, information from this resource can also be used to report study details to ClinicalTrials.gov.

References to other resources (PlanDefinition and Practitioner) used by the ResearchStudy resource are ‘[contained](https://www.hl7.org/fhir/references.html#contained)’ references.  If an institution implements the sIRB questionnaires after a trial use, the best practice recommended is to use references to the full PlanDefinition and Practitioner resources.

The use of the ResearchStudy resource is completely optional.  The official record at this time is the QuestionnaireResponse.  There is no expectation in the implementation that the software will use the ResearchStudy resource.

### Populate
The intention is that the 7 core forms will all be populatable using the data collected in the Initiate a Study Questionnaire.  The populate functionality will save time in data entry, improve data consistency and reduce typing errors.

If an institution is not using the populate functionality, then the Initiate a Study Questionnaire can be used to gather data to make a record of the research study in the ResearchStudy resource, to gather data to register the study with ClinicalTrials.gov  or it can be left out of the implementation altogether. 

![Populate Process Flow](Populate Process Flow.jpg){:height="600px"}

### Actors
1. sIRB Form Repository: A form repository that stores standardized sIRB forms. IRB systems will request form templates from this repository.
2. Central IRB Application: An IRB software system that a PI will access to retrieve forms to complete and submit.
3. Relying IRB Application: An IRB software that receives and renders completed and approved forms by the central IRB.

### Forms
![sIRB FHIR forms](sirb FHIR forms.jpg){:width="1200px"}


Form (Link to Page) | Link to External Questionnaire Viewer
[Intiate Study](https://build.fhir.org/ig/HL7/fhir-sirb/Questionnaire-sirb-initiate-study-questionnaire.html)| [Viewer](https://lhncbc.github.io/questionnaire-viewer/?q=https://raw.githubusercontent.com/HL7/fhir-sirb/master/input/resources/questionnaire/sirb-initiate-study-questionnaire.json)
[Protocol](https://build.fhir.org/ig/HL7/fhir-sirb/Questionnaire-sirb-protocol-questionnaire.html) | [Viewer](https://lhncbc.github.io/questionnaire-viewer/?q=https://raw.githubusercontent.com/HL7/fhir-sirb/master/input/resources/questionnaire/sirb-protocol-questionnaire.json)
[Consent](https://build.fhir.org/ig/HL7/fhir-sirb/Questionnaire-sirb-consent-questionnaire.html) | [Viewer](https://lhncbc.github.io/questionnaire-viewer/?q=https://raw.githubusercontent.com/HL7/fhir-sirb/master/input/resources/questionnaire/sirb-consent-questionnaire.json)
[Determination Letter](https://build.fhir.org/ig/HL7/fhir-sirb/Questionnaire-sirb-determination-letter-questionnaire.html) | [Viewer](https://lhncbc.github.io/questionnaire-viewer/?q=https://raw.githubusercontent.com/HL7/fhir-sirb/master/input/resources/questionnaire/sirb-determination-letter-questionnaire.json)
[Recruitment Materials](https://build.fhir.org/ig/HL7/fhir-sirb/Questionnaire-sirb-recruitment-materials-questionnaire.html) | [Viewer](https://lhncbc.github.io/questionnaire-viewer/?q=https://raw.githubusercontent.com/HL7/fhir-sirb/master/input/resources/questionnaire/sirb-recruitment-materials-questionnaire.json)
[Medical Adverse Events](https://build.fhir.org/ig/HL7/fhir-sirb/Questionnaire-sirb-adverse-event-questionnaire.html) | [Viewer](https://lhncbc.github.io/questionnaire-viewer/?q=https://raw.githubusercontent.com/HL7/fhir-sirb/master/input/resources/questionnaire/sirb-adverse-event-questionnaire.json)
[Non Medical Adverse Events](https://build.fhir.org/ig/HL7/fhir-sirb/Questionnaire-sirb-nonmedicalevent-questionnaire.html) | [Viewer](https://lhncbc.github.io/questionnaire-viewer/?q=https://raw.githubusercontent.com/HL7/fhir-sirb/master/input/resources/questionnaire/sirb-nonmedicalevent-questionnaire.json)
[Continuing Review](https://build.fhir.org/ig/HL7/fhir-sirb/Questionnaire-sirb-continuing-review-questionnaire.html) | [Viewer](https://lhncbc.github.io/questionnaire-viewer/?q=https://github.com/HL7/fhir-sirb/raw/master/input/resources/questionnaire/sirb-continuing-review-questionnaire.json)

### Workflow Overview

In the workflow outlined below, a Central IRB system requests one of the standardized sIRB questionnaires forms from the repository as a form of a questionnaire resource. The central IRB system receives the questionnaire response resource and renders/displays it to the Principal Investigator-PI (user). The PI enters and submits responses applicable to the selected standardized sIRB form. The submitted responses will be saved as questionnaire response resources on the Central IRB's FHIR server. The Central IRB will serve as a single source of truth for IRB Documents. The relying IRB system will send a RESTful request or implement a subscription resource to get most recent forms from the central IRB's FHIR server.

![sIRB dataflow](sirb-dataflow.jpg){:width="500px"}
Number 1, The software, whether our sIRB on FHIR software or the commercial IRB software at the sIRB, requests the official sIRB Questionnaire from the FHIR File Server at the central repository responsible for maintaining the official FHIR Questionnaires.
Number 2, The FHIR Questionnaire is transmitted to the sIRB via the Internet to the FHIR File server associated with the IRB sofrware.
Number 3 The IRB software at the sIRB processes the information in the FHIR Questionnaire and creates the Data Collection Form.  This form is then presented to the user.
Number 4 After the study coordinator inputs the data and presses the “Submit” button, the data are saved into a structured FHIR Questionnaire Response and stored in the FHIR File Server at the sIRB.
Number 5 The data  captured as a FHIR Questionnaire Response is rendered by the IRB software in a user-friendly End Result Display.  So this is the viewing of the data by reviewers at the IRB or other staff in a web browser, pdf, or within the custom IRB software. 
Number 6, After the data is reviewed and finalized, the FHIR Questionnaire Response is transmitted over the Internet to the Relying IRB’s FHIR File Server for use within their systems.
Number 7, Each of the relying IRBs can use their own software (whether sIRB on FHIR or a commercial vendor and render display friendly End Result Displays for their users.




### Considerations for the Future
During this trial, the Questionnaires are intended to be self-contained without the need to use any other resources such as Practitioner, ResearchSubject, AdverseEvent or Organization.

After this implementation guide matures further - and because the data in the FHIR questionnaires is being captured in a standardized, structured way - it is expected that the larger institutions will want some or complete integration with their existing research study management software, which may or may not be FHIR-based. 

One challenge is that although the forms utilize some data that can be found in other resources, much of the data contained in the forms does not currently have corresponding data elements in current FHIR resources. 

Another challenge is that the primary purpose and scope of the sIRB forms is different from questionnaires that would be designed to capture data to capture study records using FHIR resources.

Also, many of the existing resources serve different purposes and contexts than the sIRB forms.  The sIRB forms are essentially detailed requests for different types of approval and reports of study activities. 

Nevertheless, the structured nature of the data capture lends itself well to extraction and storage of some of the form data into individual FHIR resources, should the institutions or their software vendors opt for this implementation.  

Also, appropriate FHIR resources for storage of the content of each complete form as a unique document will need to be evaluated or developed in the next phases.


As this is a trial of the Questionnaires, decisions regarding how to populate some of the form data from existing standard FHIR resources implemented by potential study sites will need to be made in future work in order to achieve interoperability and integration with other systems for a more streamlined implementation.

Capturing the provenance of the requests for approvals, approval decisions and reports would make for a more robust implementation if the forms are incorporated into a study management software system that has FHIR capabilities.



### Credits
These standards were developed by Duke University with assistance from University of Arkanasas of Medical Sciences and Vanderbilt University.

### Dependencies
These standards were developed based upon the [R4](http://hl7.org/fhir/R4/) FHIR version.