### Overview

Data standards to move data and documents from clinical research sites to a single ethics review board in support of the "NIH Policy on the Use of a Single Institutional Review Board for Multi-Site Research

### Background
Launching a multi-site clinical research study is frequently a long and involved process that can delay the development of potentially effective clinical treatment. Ethics review and approval processes conducted by IRBs have been cited as a major contributor to delays in initiating multi-site studies. In response, the set of protections for research subjects in the code of federal regulations for human-subjects research (Common Rule, 45 CFR Part 46.114) was revised with a requirement that a single IRB be named when multiple sites are using the same protocol. Rather than each site waiting for approval of a study by its local IRB before enrolling subjects, a single IRB review will expedite approval and improve the timeline for study initiation and completion. Researchers commented about the redundancy of effort, additional costs, and administrative burdens that often lead to delays and imbalances in enrollment of research participants in multi-site clinical studies. The burden of tasks related to IRB approval, which most frequently must be completed manually at multiple clinical investigational sites, can also adversely impact site data quality and sustainability.

### Significance
In lieu of ad hoc transfers of PDFs and other document formats via email or online submission, this project utilizes FHIR based standards to facilitate document exchange. A standards enabled process leveraged by software has the potential to significantly decrease the extensive manual tasks that have become associated with using a single IRB system. This use of FHIR standards to meet the need for an efficient exchange of data and documents will improve the operational efficiency. 

### Coverage
This Implementation guide covers the IRB Determination Letter, Study Protocol, and Consent templates. It will be expanded with the completion of other templates associated with the sIRB approval process when completed.

### Scope
The sIRB implementation guide deals with creation and exchange of standardized sIRB forms and form responses using FHIR questionnaire and questionnaire response resources. The questionnaires may have nested structures and embed skip/branching logics to display appropriate questions based on previous answers. Pre population of questionnaire forms and extraction of data elements/resources from questionnaire responses is out of scope for the current version of sIRB implementation guide; these functionalities can be incorporated into your specific implementation by referring to Structure Data Capture (SDC) implementation guide.

### Assumptions
The implementation guide assumes that the implementer has or will have a capability to send, receive, render and display FHIR questionnaires and questionnaire responses. Implementers may consider using free software such as NLM's FHIR Questionnaire rendering tool or design their own. Exchange of resources can be achieved by any of the FHIR messaging mechanisms. Please refer to FHIR standard documentation, open source implementations of FHIR specifications, and FHIR Messaging for additional information. 

### Actors
1. Form Author/Editor: A system or organization who is responsible for creating, updating and deprecating the standardized sIRB forms such as Determination Letter, Protocol, Consent, Adverse Event, Recruitment Materials, and Continuous Review
2. sIRB Form Repository: A form repository that stores standardized sIRB forms. IRB systems will request form templates from this repository.
4. Central IRB Application: An IRB software system that a PI access to complete and submit the standardized forms.
5. Relying IRB Application: An IRB software that receives and renders completed and approved forms by the central IRB.
6. Principal Investigator/Practitioner: A person who is authorized to initiate a research study by completing sIRB forms.


### Workflow Overview

In the workflow outlined below, a Central IRB system requests one of the standardized sIRB questionnaires forms from the repository as a form of a questionnaire resource. The central IRB system receives the questionnaire response resource and renders/displays it to the Principal Investigator-PI (user). The PI enters and submits responses applicable to the selected standardized sIRB form. The submitted responses will be saved as questionnaire response resources on the Central IRB's FHIR server. The Central IRB will serve as a single source of truth for IRB Documents. The relying IRB system will send a RESTful request or implement a subscription resource to get most recent forms from the central IRB's FHIR server.

<table><tr><td><img src="sirb-dataflow.jpg" /></td></tr></table>




### Dependencies
These standards were developed based upon the [R4](http://hl7.org/fhir/R4/) FHIR version.

[Profiles](file:///C:/SIRB/GitHubLinked/output/artifacts.html)




### Authors

<table>
<thead>
<tr>
<th>Name</th>
<th>Email/URL</th>
</tr>
</thead>
<tbody>
<tr>
<td>HL7 International - Biomedical Research and Regulation</td>
<td><a href="http://www.hl7.org/Special/committees/rcrim" target="_new">http://www.hl7.org/Special/committees/rcrim</a></td>
</tr>
</tbody>
</table>


