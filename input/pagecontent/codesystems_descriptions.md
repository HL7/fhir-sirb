### Usage of Codesystems from HL7 CodeSystems Registry in the sIRB Questionnaires
<br>
Where possible, the [sIRB Questionnaires](artifacts.html#questionnaires) use the values in the HL7 CodeSystems Registry<a href="#fn-1"><sup>1</sup></a> at <a href="https://terminology.hl7.org/3.0.0/codesystems.html">https://terminology.hl7.org/3.0.0/codesystems.html</a>. For some questions, not all values in a given codesystem were applicable to the sIRB use case and only a subset of the values were included as answer options for those questions.
<br>
<br>
The Codesystems from [HL7 CodeSystems Registry](https://terminology.hl7.org/3.0.0/codesystems.html) that were used in the [sIRB Questionnaires](artifacts.html#questionnaires) are:
<br>
<br>

| CodeSystem  | Official URL   |   Questionnaire(s) Using this CodeSystem |
| -------------------- | ---------------- | ---------------------------------- |
|expandedYes-NoIndicator|[http://terminology.hl7.org/CodeSystem/v2-0532](http://terminology.hl7.org/CodeSystem/v2-0532)|Initiate a Study Questionnaire, Protocol Questionnaire, Consent Questionnaire, Recruitment Materials Questionnaire, Continuing Review Questionnaire, Adverse Medical Event Questionnaire and Adverse Non-Medical Event Questionnaire|
|ResearchStudyPhase|[http://terminology.hl7.org/CodeSystem/research-study-phase](http://terminology.hl7.org/CodeSystem/research-study-phase)|Protocol Questionnaire|
|Unified Code for Units of Measure (UCUM)<a href="#fn-2"><sup>2</sup></a>|[http://unitsofmeasure.org](http://unitsofmeasure.org)|Consent Questionnaire|
|relationship|[http://terminology.hl7.org/CodeSystem/v2-0063](http://terminology.hl7.org/CodeSystem/v2-0063)|Consent Questionnaire|
|ResearchStudyStatus|[http://hl7.org/fhir/research-study-status](http://hl7.org/fhir/research-study-status)|Continuing Review Questionnaire|
|administrativeSex|[http://terminology.hl7.org/CodeSystem/v2-0001](http://terminology.hl7.org/CodeSystem/v2-0001)|Adverse Medical Event Questionnaire|
|Ethnicity|[http://terminology.hl7.org/CodeSystem/v3-Ethnicity](http://terminology.hl7.org/CodeSystem/v3-Ethnicity)|Adverse Medical Event Questionnaire|
|Race|[http://terminology.hl7.org/CodeSystem/v3-Race](http://terminology.hl7.org/CodeSystem/v3-Race)|Adverse Medical Event Questionnaire|
|AdverseEventSeriousness|[http://terminology.hl7.org/CodeSystem/adverse-event-seriousness](http://terminology.hl7.org/CodeSystem/adverse-event-seriousness)|Adverse Medical Event Questionnaire|
|AdverseEventSeverity|[http://terminology.hl7.org/CodeSystem/adverse-event-severity](http://terminology.hl7.org/CodeSystem/adverse-event-severity)|Adverse Medical Event Questionnaire|
|AdverseEventCausalityAssessment|[http://terminology.hl7.org/CodeSystem/adverse-event-causality-assess](http://terminology.hl7.org/CodeSystem/adverse-event-causality-assess)|Adverse Medical Event Questionnaire|
|actionTakenInResponseToTheEvent|[http://terminology.hl7.org/CodeSystem/v2-0251](http://terminology.hl7.org/CodeSystem/v2-0251)|Adverse Medical Event Questionnaire|
{: .grid}

<br>
<br>
### sIRB-specific Codesystem in the sIRB Questionnaires
<br>
In many cases, the values and concepts in the [sIRB Questionnaires](artifacts.html#questionnaires) were not yet captured by an existing HL7 Codesystem or the existing Codesystems did not contain all of the values needed.  In these circumstances, we have created our own codes for the [sIRB Questionnaires](artifacts.html#questionnaires). We have included these in the siRB IG at [CodeSystem-temporarycodes.html](CodeSystem-temporarycodes.html), which is represented as a codeSystem resource.
<br>
<br>
Because of the low maturity level of the sIRB IG, a temporary code list within the IG was used. As the sIRB Questionnaires mature, the codes within the sIRB Questionnaires will grow in maturity and we foresee that we will work with the HL7 terminology workgroup to have officially registered CodeSystems created and listed in the  [HL7 CodeSystems Registry](https://terminology.hl7.org/3.0.0/codesystems.html).
<br>
<br>
Below are the descriptions of the [sIRB temporary codes](CodeSystem-temporarycodes.html):
<br>

|Topic|Code|Display|Questionnaire(s) Using this Codesystem| 
| -------------------- | ---------------- | ------------------- | ------------------------------------------------- |
|Adverse Event Submission Type|INITIAL|Initial|Adverse Medical Event Questionnaire|
|Adverse Event Submission Type|UPDATE|Update|Adverse Medical Event Questionnaire|
| | | | |
|Study Type|INT|Interventional|Initiate a Study Questionnaire, Protocol Questionnaire and Adverse Medical Event Questionnaire|
|Study Type|OBS|Observational|Initiate a Study Questionnaire, Protocol Questionnaire and Adverse Medical Event Questionnaire|
| | | | |
|Status of reliance|APPROVED|Approved for reliance|Initiate a Study Questionnaire|
|Status of reliance|POSSIBLE|Potential/possible|Initiate a Study Questionnaire|
|Status of reliance|CANCELLED|Cancelled or not participating|Initiate a Study Questionnaire|
|Status of reliance|ONHOLD|Temporarily on hold|Initiate a Study Questionnaire|
|Status of reliance|DENIED|Denied reliance|Initiate a Study Questionnaire|
| | | | |
|Professional Relationship Type|SFS|Sponsor or Funding Source|Initiate a Study Questionnaire|
|Professional Relationship Type|CRO|Contract Research Organization (CRO)|Initiate a Study Questionnaire|
| | | | |
|Determination Decision|AR|Accepts Review|Determination Letter Questionnaire|
|Determination Decision|DR|Denies Review|Determination Letter Questionnaire|
| | | | |
|Types of communication methods that will be used to reply to potential participants|PHONECALL|Telephone calls|Recruitment Materials Questionnaire|
|Types of communication methods that will be used to reply to potential participants|VM|Voice mail and telephone voice messages|Recruitment Materials Questionnaire|
|Types of communication methods that will be used to reply to potential participants|VC|Video Conferencing|Recruitment Materials Questionnaire|
|Types of communication methods that will be used to reply to potential participants|EMAIL|Email|Recruitment Materials Questionnaire|
|Types of communication methods that will be used to reply to potential participants|TXT|Text messages/texting|Recruitment Materials Questionnaire|
|Types of communication methods that will be used to reply to potential participants|EHPRTL|eHealth Portal messaging|Recruitment Materials Questionnaire|
| | | | |
|Type of study agent received|SA|Study Agent|Adverse Medical Event Questionnaire|
|Type of study agent received|PLACEBO|Placebo|Adverse Medical Event Questionnaire|
|Type of study agent received|BSA|Blinded Study Agent|Adverse Medical Event Questionnaire|
| | | | |
|Possible alternate causes of the SAE|PRMYDIS|Primary disease|Adverse Medical Event Questionnaire|
|Possible alternate causes of the SAE|STDYPRO|Study Procedure|Adverse Medical Event Questionnaire|
|Possible alternate causes of the SAE|PRE|Pre-existing condition|Adverse Medical Event Questionnaire|
|Possible alternate causes of the SAE|UNDERLYINGDIS|Underlying disease|Adverse Medical Event Questionnaire|
|Possible alternate causes of the SAE|CONCMITMED|Concomitant medication|Adverse Medical Event Questionnaire|
|Possible alternate causes of the SAE|OTHERCAUSE|Other known or suspected cause|Adverse Medical Event Questionnaire|
| | | | |
|Status of study research activities|nochange|No change in research activities|Adverse Non-Medical Event Questionnaire|
|Status of study research activities|stopped|All research activities temporarily and voluntarily stopped for all participants|Adverse Non-Medical Event Questionnaire|
|Status of study research activities|partial|Partial voluntary hold on some research activities for all participants (explain below)|Adverse Non-Medical Event Questionnaire|
|Status of study research activities|hold|Voluntary hold on new participant enrollment only|Adverse Non-Medical Event Questionnaire|
| | | | |
|Adverse Non-Medical Event Report Status|init|Initial|Adverse Non-Medical Event Questionnaire|
|Adverse Non-Medical Event Report Status|followup|Follow-up|Adverse Non-Medical Event Questionnaire|
| | | | |
|Status of Risk Reduction Activities|completed|Done, performed or completed|Adverse Non-Medical Event Questionnaire|
|Status of Risk Reduction Activities|pending|Pending - Currently under development|Adverse Non-Medical Event Questionnaire|
|Status of Risk Reduction Activities|notundertaken|Not done or undertaken|Adverse Non-Medical Event Questionnaire|
| | | | |
|Exception Types for Protocol and Consent Changes after Adverse Non-Medical Event|mla|Adverse Non-Medical Event consisted of a missed lab or assessment by a participant (which does not jeopardize the study or increase risks to other participants)|Adverse Non-Medical Event Questionnaire|
|Exception Types for Protocol and Consent Changes after Adverse Non-Medical Event|mtd|Adverse Non-Medical Event consisted of a missed treatment or dose by a participant (which does not jeopardize the study or increase risks to other participants|Adverse Non-Medical Event Questionnaire|
|Exception Types for Protocol and Consent Changes after Adverse Non-Medical Event|otherreason|Other reason|Adverse Non-Medical Event Questionnaire|
| | | | |
|Study Enrollment Status|open|Open for enrollment|Continuing Review Questionnaire|
|Study Enrollment Status|closed|Closed to enrollment|Continuing Review Questionnaire|
|Study Enrollment Status|not-open|Not yet open|Continuing Review Questionnaire|
|Study Enrollment Status|open-no-participants|Open with no participants|Continuing Review Questionnaire|
| | | | |
|Study Intervention Status|complete|All interventions complete|Continuing Review Questionnaire|
|Study Intervention Status|continue-meds|Continuing interventions|Continuing Review Questionnaire|
|Study Intervention Status|continue-min-risk|Continuing interventions - minimal risk|Continuing Review Questionnaire|
| | | | |
|Study Funding Source|federal|Federal|Continuing Review Questionnaire|
|Study Funding Source|state|State|Continuing Review Questionnaire|
|Study Funding Source|industry|Industry|Continuing Review Questionnaire|
|Study Funding Source|foundation|Foundation|Continuing Review Questionnaire|
|Study Funding Source|institutional|Institutional|Continuing Review Questionnaire|
|Study Funding Source|departmental|Departmental|Continuing Review Questionnaire|
|Study Funding Source|otherfund|Other Funding Source|Continuing Review Questionnaire|
| | | | |
|Intervention Type|DBV|Drug/Biologic/Vaccine|Protocol Questionnaire|
|Intervention Type|DEV|Device|Protocol Questionnaire|
|Intervention Type|SBE|Social/Behavioral/educational (SBE)|Protocol Questionnaire|
|Intervention Type|PRO|Procedural|Protocol Questionnaire|
| | | | |
|Type of FDA exemption|IND|IND|Initiate a Study Questionnaire, Protocol Questionnaire and Adverse Medical Event Questionnaire|
|Type of FDA exemption|IDE|IDE|Initiate a Study Questionnaire, Protocol Questionnaire and Adverse Medical Event Questionnaire|
| | | | |
|Additional Investigator Role|COPI|Co-Principal Investigator|Protocol Questionnaire|
|Additional Investigator Role|COI|Co-Investigator|Protocol Questionnaire|
|Additional Investigator Role|PD|Program Director|Protocol Questionnaire|
| | | | |
|Research Indicator|RES|Research|Consent Questionnaire|
|Research Indicator|STDCR|Standard of Care|Consent Questionnaire|
| | | | |
|Risk Category|PHYS|Physical|Consent Questionnaire|
|Risk Category|NONPHYS|Non-Physical|Consent Questionnaire|
| | | | |
|Coverage for medical treatment from research related injury|TRTNOTCOV|Treatment not covered|Consent Questionnaire|
|Coverage for medical treatment from research related injury|RRICOV|Research Related injury covered|Consent Questionnaire|
|Coverage for medical treatment from research related injury|ACNOTCICOV|Acute but not chronic injury covered|Consent Questionnaire|
| | | | |
|Role or group who will have access to data|OTHINSTRES|Researchers at other institutions|Consent Questionnaire|
|Role or group who will have access to data|THISINSTRES|Researchers outside the study team at this institution|Consent Questionnaire|
|Role or group who will have access to data|EXTREGAUTH|External Regulatory Authorities|Consent Questionnaire|
| | | | |
|Deidentification detail|DEIDUSED|Identifiers might be removed from private information or biospecimens, and this information could then be used for future research studies or distributed to another investigator for future research studies without additional informed consent.|Consent Questionnaire|
|Deidentification detail|DEIDNOTUSED|Information or biospecimens collected will not be used or distributed for future research studies, even if deidentified.|Consent Questionnaire|
| | | | |
|launchContext name code|sourceQuestionnaireResponse|The content of the Questionnaire Response transferred to this Questionnaire during form launch|Protocol Questionnaire, Consent Questionnaire, Determination Letter Questionnaire, Recruitment Materials Questionnaire, Adverse Medical Event Questionnaire, Adverse Non-Medical Event Questionnaire and Continuing Review Questionnaire|
| | | | |
|Justification for Adverse Event Classification as Serious|ResultsInDeath<a href="#fn-3"><sup>3</sup></a>|Results in death|Adverse Medical Event Questionnaire|
|Justification for Adverse Event Classification as Serious|IsLifeThreatening<a href="#fn-3"><sup>3</sup></a>|Is Life-threatening|Adverse Medical Event Questionnaire|
|Justification for Adverse Event Classification as Serious|ResultsInHospitalization<a href="#fn-3"><sup>3</sup></a>|Requires or prolongs inpatient hospitalization|Adverse Medical Event Questionnaire|
|Justification for Adverse Event Classification as Serious|IsBirthDefect<a href="#fn-3"><sup>3</sup></a>|Is a congenital anomaly/birth defect|Adverse Medical Event Questionnaire|
|Justification for Adverse Event Classification as Serious|ResultsInDisability<a href="#fn-3"><sup>3</sup></a>|Results in persistent or significant disability/incapacity|Adverse Medical Event Questionnaire|
|Justification for Adverse Event Classification as Serious|RequiresPreventImpairment<a href="#fn-4"><sup>4</sup></a>|Requires intervention to prevent permanent impairment|Adverse Medical Event Questionnaire|
|Justification for Adverse Event Classification as Serious|Other<a href="#fn-3"><sup>3</sup></a>|Other|Adverse Medical Event Questionnaire|
| | | | |
|Outcome of Adverse Medical Event|RCVRED<a href="#fn-5"><sup>5</sup></a>|Recovered/Resolved|Adverse Medical Event Questionnaire|
|Outcome of Adverse Medical Event|RCVRING<a href="#fn-5"><sup>5</sup></a>|Recovering/Resolving|Adverse Medical Event Questionnaire|
|Outcome of Adverse Medical Event|NRCVRED<a href="#fn-5"><sup>5</sup></a>|Not recovered/Not resolved/Ongoing|Adverse Medical Event Questionnaire|
|Outcome of Adverse Medical Event|SEQL<a href="#fn-5"><sup>5</sup></a>|Recovered/Resolved with sequelae|Adverse Medical Event Questionnaire|
|Outcome of Adverse Medical Event|FATAL<a href="#fn-5"><sup>5</sup></a>|Fatal|Adverse Medical Event Questionnaire|
|Outcome of Adverse Medical Event|UNK<a href="#fn-5"><sup>5</sup></a>|Unknown|Adverse Medical Event Questionnaire|
| | | | |
|Other Actions Taken Regarding Study Intervention in Response to Adverse Event|NC<a href="#fn-6"><sup>6</sup>|Product dose or frequency of use not changed|Adverse Medical Event Questionnaire|
|Other Actions Taken Regarding Study Intervention in Response to Adverse Event|NA<a href="#fn-6"><sup>6</sup>|Not applicable|Adverse Medical Event Questionnaire|
|Other Actions Taken Regarding Study Intervention in Response to Adverse Event|UNK<a href="#fn-6"><sup>6</sup>|Unknown|Adverse Medical Event Questionnaire|
| | | | |
|Participant Accrual Type|PreviousAccrual|Previous Accrual|Continuing Review Questionnaire|
|Participant Accrual Type|AdditionalEnrollees|Additional enrollees this approval period|Continuing Review Questionnaire|
{: .grid}


<br>
### Example ResearchStudy resource (optional)
<br>
In the example, the research study category of C98388 Interventional Study from the <a href="http://ncimeta.nci.nih.gov">NCI Metathesaurus</a><a href="#fn-7"><sup>7</sup></a> codesystem is shown. This codesystem is not meant to imply that this codesystem is the required or suggested codesystem to use in the ResearchStudy category element in the sIRB utililization of the ResearchStudy resource.
<br>


<br>
### Copyright/Legal Notes for Codesystems


<div role="doc-endnotes" class="footnotes">

	<div role="doc-endnote" id="fn-1"><sup>1</sup>
		<a href="https://terminology.hl7.org/3.0.0/codesystems.html">HL7 CodeSystems Registry</a>. Content is copyright HL7. Licensed under creative commons public domain.
	</div>
<br>
	<div role="doc-endnote" id="fn-2"><sup>2</sup>
		The UCUM codes, UCUM table (regardless of format), and UCUM Specification are copyright 1999-2009, Regenstrief Institute, Inc. and the Unified Codes for Units of Measures (UCUM) Organization. All rights reserved. <a href="https://ucum.org/trac/wiki/TermsOfUse">https://ucum.org/trac/wiki/TermsOfUse</a>.
	</div>
<br>
	<div role="doc-endnote" id="fn-3"><sup>3</sup>
		Based on the Boolean data elements for ICSR E.i.3.2 Seriousness Criteria at Event Level in the <a href="https://www.ich.org/page/e2br3-individual-case-safety-report-icsr-specification-and-related-files">Implementation Guide for
Electronic Transmission of Individual Case Safety Reports (ICSRs) E2B(R3) Data Elements and Message Specification, Version 5.02, 10 November 2016</a> by International Council for Harmonisation of Technical Requirements for Pharmaceuticals for Human Use (ICH).  Copyright International Council for Harmonisation of Technical Requirements for Pharmaceuticals for Human Use (ICH) and may be used, reproduced, incorporated into other works, adapted, modified, translated or distributed under a public license provided that the ICH's copyright is acknowledged at all times.
	</div>
<br>
	<div role="doc-endnote" id="fn-4"><sup>4</sup>	
		The value "Requires intervention to prevent permanent impairment" is from What is a Serious Adverse Event? at <a href="https://www.fda.gov/safety/reporting-serious-problems-fda/what-serious-adverse-event"> https://www.fda.gov/safety/reporting-serious-problems-fda/what-serious-adverse-event</a>, which is in the public domain.
	</div>
<br>		
	<div role="doc-endnote" id="fn-5"><sup>5</sup>	
		Based on the values in ICSR E.i.7 Outcome of Reaction / Event at the Time of Last Observation in the <a href="https://www.ich.org/page/e2br3-individual-case-safety-report-icsr-specification-and-related-files">Implementation Guide for Electronic Transmission of Individual Case Safety Reports (ICSRs) E2B(R3) Data Elements and Message Specification, Version 5.02, 10 November 2016</a> by ICH.  Copyright ICH. May be used, reproduced, incorporated into other works, adapted, modified, translated or distributed under a public license provided that the ICH's copyright is acknowledged at all times.
	</div>
<br>

	<div role="doc-endnote" id="fn-6"><sup>6</sup>
		These codes are additional values needed to broaden the existing HL7 Codesystem <a href="http://terminology.hl7.org/CodeSystem/v2-0251">actionTakenInResponseToTheEvent</a> to represent all of values in the ICSR Implementation Guide. ICSR G.k.8 Action(s) Taken with Drug in the <a href="https://www.ich.org/page/e2br3-individual-case-safety-report-icsr-specification-and-related-files">Implementation Guide for Electronic Transmission of Individual Case Safety Reports (ICSRs) E2B(R3) Data Elements and Message Specification, Version 5.02, 10 November 2016</a> by ICH. Copyright ICH. May be used, reproduced, incorporated into other works, adapted, modified, translated or distributed under a public license provided that the ICH's copyright is acknowledged at all times.
	</div>

<br>
	<div role="doc-endnote" id="fn-7"><sup>7</sup>
		NCI Metathesaurus at <a href="http://ncimeta.nci.nih.gov">http://ncimeta.nci.nih.gov</a> is in the public domain. For more details about the NCI Metathesaurus, see <a href="https://hl7.org/fhir/2021may/ncimeta.html">Using the NCI Metathesaurus with FHIR</a>.
	</div>

</div>