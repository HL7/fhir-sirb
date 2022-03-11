# sIRB Ideal Workflow (High Level)
<br>
<br>
## Initial Submission
<br>
1.	Lead Principal Investigator (Lead PI) creates a new study in sIRB system (required to obtain IRB study identifier). 
2.	Lead PI completes the Initiate a Study Questionnaire (FHIR) (used to pre-populate other FHIR questionnaires). 
3.	Lead PI submits initial study application via the FHIR sIRB system. 
a.	Initial application submission includes sIRB Study Application and builds key study documents to be reviewed and approved by the sIRB before they can be sent to Relying Sites. 
b.	Key Study Documents built in FHIR include:  Study Protocol, Informed Consent, HIPAA Authorization, and Recruitment Template.
c.	Key Study Documents, when rendered by FHIR, are uploaded into the sIRB system. 
4.	Once IRB Study Application and associated FHIR documents are complete, the Lead PI signs off on the submission and the application with FHIR documents is sent to the sIRB for review. 
5.	The sIRB communicates with the Lead PI as necessary to obtain an acceptable application. 
6.	Once the sIRB has approved the IRB Study Application with associated documents, the Lead PI receives notification of submission approval from the sIRB.  
a.	Submission approval consists of approval of Study Protocol and submitted study documents/templates.

<table><tr><td><img src="Initial Submission 20211021.jpg" style="width:1150px;height:auto;" /></td></tr></table>

## Site addition
<br>
1.	Once the Lead PI receives the notification of approval from the sIRB system, they are able to begin the process of adding (previously identified) Relying Sites to the approved study.
2.	The Relying Site completes Reliance Documents and the Local Context Survey. 
3.	Once the Relying Site has completed the reliance process, they will send, via FHIR the Cede Decision Letter/Reliance Decision Letter to the Lead PI.
4.	The Lead PI will make the approved study documents available, via FHIR, to the identified Relying Site. 
a.	This electronic packet includes the sIRB approved Study Protocol and sIRB approved study templates (Informed Consent, HIPAA Authorization, Recruitment Template).
b.	The Relying Site will update the Informed Consent, HIPAA authorization, and recruitment materials for Relying Site specific local context and policies/considerations specific to the institution for which the Relying Site is affiliated.  
c.	Once these updates are made, the sIRB and the Lead PI will be automatically notified that the Relying Site documentation is completed (FHIR). 
5.	The Lead PI receives the Relying Site study documents via FHIR.  
6.	An Amendment Form to the approved study is generated in the sIRB system (FHIR). 
7.	Once the Relying Site addition Amendment Form is approved by the sIRB, the Lead PI receives notification of approval (sIRB system). 
8.	Official approval letter and sIRB approved documents are made available to Relying Site (FHIR). 

<table><tr><td><img src="Site Addition 20211021.jpg" style="width:1150px;height:auto;"  /></td></tr></table>


## Continuing Review
<br>
1.	sIRB notifies Lead PI and Relying Sites (via FHIR) of the need for a continuing review.
a.	The date of the Continuing Review is based on the approval date of the initial sIRB study application, not the approval of an individual Relying Site.
2.	The Lead PI creates a Continuing Review FHIR document for each Relying Site from the study electronic data capture system. 
3.	Relying Sites reviews Continuing Review FHIR document information as it relates to any previously reported events, enrollments, and withdrawals. Relying Sites also add the number of approached individuals. This information is sent to the Lead PI via FHIR. 
4.	Once the Lead PI receives the required information from Relying Sites, the Lead PI logs into the sIRB system to complete the Continuing Review form. 
a.	All of the Relying Site level documentation is compiled into a single study level report that is uploaded into the sIRB system. 
5.	Once the sIRB completes their review, an approval is issued via the sIRB system to the Lead PI. 
6.	The sIRB system sends a copy of the Continuing Review approval and the updated sIRB approved Informed Consent to the Relying Sites (FHIR). 

<table><tr><td><img src="Continuing Review 20211021.jpg" style="width:1150px;height:auto;" /></td></tr></table>

## UPIRTSO/Reportable Events
<br>
1.	If the Lead PI or a Relying Site experiences an event (safety or protocol violation), they send, via FHIR, the necessary information or documentation (as outlined by the sIRB) to the Lead PI. 
2.	Upon receiving the event information from the Relying Site, the Lead PI reviews this information and completes a Reportable Event form in the sIRB system. 
3.	Depending on the severity of the event, the type of review by the sIRB will determine the remediation plan including, but not limited to, a Corrective Action Plan with a timeline for completion and reporting back to the sIRB. 
4.	The Lead PI will complete the recommended course of action and provide a report to the sIRB. 

<table><tr><td><img src="Reportable Events 20211021.jpg" style="width:1150px;height:auto;"  /></td></tr></table>

**Note**:  The ideal workflow is based on the minimum required by the Common Rule.  In particular, under the Common Rule Relying Sites are not even required to have their own IRBs so the only IRB that is shown is the one for the sIRB.