## Conformance and Functionality Expectations

### Actors

**Host (generally the lead principal investigator's institution)**

* Server
In general, the lead principal investigator's institution will be the institution hosting the sIRB FHIR server that stores the Questionnaires and the QuestionnaireResponses. This is the server referenced in the [sIRB Capability Statement](CapabilityStatement-sIRB-CapabilityStatement.html). 

* Client
The lead principal investigator's institution will also host a website or other sIRB software to render the blank forms and display the completed questionnaire responses for edits, review or saving to pdf. This is the client referenced in the [sIRB Capability Statement](CapabilityStatement-sIRB-CapabilityStatement.html).  The client REST FHIR Questionnaire Management Software could be the research study system of the lead principal investigator's institution, another type of software or the sIRB on FHIR software).


**single Institutional Review Board (sIRB)**
The single Institutional Review Board (sIRB) is either the ethics review board at the lead principal investigator's institution or a 3rd party ethics review board retained by the lead principal investigator's institution. The sIRB will need access to the research study system, the sIRB on FHIR software or other sIRB software to review the completed forms.


**Non-host (generally the relying sites)**
If the non-host wishes to interact with the forms without the requirement of having a FHIR server, then the host institution must provide software or a website with the software for viewing, completing and storing the forms on the host institution’s FHIR server that can be accessed via a web browser
If the relying sites wish to use a FHIR server, then the FHIR server should have the capabilities defined in the "Host (generally the lead principal investigator's institution)" section.


### Exchange Framework

The exchange framework used is the "[RESTful FHIR](https://www.hl7.org/fhir/http.html)".


### Conformance Verbs

The conformance verbs - SHALL, SHOULD, MAY - used in this implementation guide are defined in [FHIR Conformance Language](http://hl7.org/fhir/R4/conformance-rules.html#conflang0).


### Capability Statement

The [sIRB Capability Statement](CapabilityStatement-sIRB-CapabilityStatement.html) describes the expectations for the client and server. A compliant server SHALL adhere to the requirements listed in this resource, and implement the RESTful behavior according to the FHIR specification. A compliant client SHALL adhere to the requirements listed in this resource, and implement the RESTful behavior according to the FHIR specification.


### Other functionality expectations and considerations

The Capability Statement does not capture all of the necessary functionality for sIRB IG compliance. This section explains other necessary and optional functionality.

The sIRB IG assumes that the implementer is familiar with the [SDC Specification]( http://hl7.org/fhir/uv/sdc/StructureDefinition/sdc-questionnaireresponse).
<br>
<br>

#### Questionnaire and QuestionnaireResponse resources

To be compliant with this IG, a system SHALL support and render the eight [sIRB Questionnaires](artifacts.html#sirb-questionnaires).
<br>
<br>
A system also SHALL support and render the QuestionnaireResponses.


##### Extensions for the Questionnaire and QuestionnaireResponse

A system SHALL support the following extensions:
<br><br>
[choiceOrientation](http://hl7.org/fhir/StructureDefinition/questionnaire-choiceOrientation)
<br>
[displayCategory](http://hl7.org/fhir/StructureDefinition/questionnaire-displayCategory)
<br>
[hidden](http://hl7.org/fhir/StructureDefinition/questionnaire-hidden)
<br>
[itemControl](http://hl7.org/fhir/StructureDefinition/questionnaire-itemControl)
<br>
[supportLink](http://hl7.org/fhir/StructureDefinition/questionnaire-supportLink)
<br>
[unitOption](http://hl7.org/fhir/StructureDefinition/questionnaire-unitOption)
<br>
[variable](http://hl7.org/fhir/StructureDefinition/variable)
<br>
[rendering-style](http://hl7.org/fhir/StructureDefinition/rendering-style)
<br>
[rendering-xhtml](http://hl7.org/fhir/StructureDefinition/rendering-xhtml)
<br>
<br>
For more information about Questionnaire extensions, please see the [SDC Implementation Guide Extension definitions](http://hl7.org/fhir/uv/sdc/artifacts.html#structures-extension-definitions) and [SDC Implementation Guide Examples](http://hl7.org/fhir/uv/sdc/examples.html). 


<br>
<br>
##### Recommendations for Questionnaire Population

A client SHOULD utilize the [population](http://hl7.org/fhir/uv/sdc/populate.html#pre-population-service). functionality that is designed in the sIRB Questionnaires in this IG.

The sIRB Questionnaires are [populatable](http://hl7.org/fhir/uv/sdc/populate.html#pre-population-service). So that researchers do not need to re-type the same information into multiple forms, the sIRB forms are designed with one master form, the [Initiate a Study](Questionnaire-sirb-initiate-study-questionnaire-populate.html) questionnaire, that collects common data elements which will then be populatable into the other sIRB forms. Entering common data elements only once (via the [Initiate a Study](Questionnaire-sirb-initiate-study-questionnaire-populate.html) questionnaire, saves time for the researchers and study coordinators and reduces data entry errors.

Implementation also assumes that the implementers will be knowledgeable about [SDC Form Population](http://hl7.org/fhir/uv/sdc/populate.html).
<br>
<br>
Some guidance is provided here:

* The client software SHOULD be designed to function similar to the [population operations] (http://hl7.org/fhir/uv/sdc/populate.html##population-operations) described in the SDC IG, but as a client-side process, rather than calling the FHIR server population operations.
<br>
<br>
* Implementers should be aware that sIRB Questionnaires use [Expression-Based Population](http://hl7.org/fhir/uv/sdc/populate.html#exp-pop).
<br>
<br>
* The Questionnaires also utilize [answerExpression](http://hl7.org/fhir/uv/sdc/STU3/StructureDefinition-sdc-questionnaire-answerExpression.html) functionality from the Form Behavior and Calculation  (http://hl7.org/fhir/uv/sdc/STU3/behavior.html) section of the SDC IG in order to populate the drop-down list of [permitted](http://hl7.org/fhir/uv/sdc/STU3/behavior.html#choice-restriction) answers for some of the questions.  
<br>
<br>
* For more information on Expressions, also see [Expression Extensions](http://hl7.org/fhir/uv/sdc/STU3/expressions.html)
<br>
<br>
* The following SDC extensions SHOULD be used for the populate functionality to work as described:

| Extension  |  
| -------------------------------------------------------------------------------------------------------- | 
| [Answer Expression](http://hl7.org/fhir/uv/sdc/StructureDefinition/sdc-questionnaire-answerExpression) |
| [Initial Expression](http://hl7.org/fhir/uv/sdc/StructureDefinition/sdc-questionnaire-initialExpression) |
| [Calculated Expression](http://hl7.org/fhir/uv/sdc/StructureDefinition/sdc-questionnaire-calculatedExpression) |
| [Launch Context](http://hl7.org/fhir/uv/sdc/StructureDefinition/sdc-questionnaire-launchContext)  |
|[variable](http://hl7.org/fhir/StructureDefinition/variable)| 
{: .grid}

<br>
<br>
* fhirpath
<br>
[fhirpath](https://hl7.org/fhirpath/) is used in the Answer Expression(s), Initial Expression(s), Calculated Expression(s) and Launch Context Expression(s) used in the Questionnaires. An implementation of fhirpath will need to be added if not bundled with the form software package.
<br>
<br>



#### Optional ResearchStudy Resource
<br>
##### ResearchStudy R4 Base Definition
If an implementer wishes to optionally use the ResearchStudy resource to transmit or persist data, the R4 base definition of the [ResearchStudy](https://www.hl7.org/fhir/researchstudy.profile.json.html) resource MAY be used.
<br>
<br>

##### workflow-researchStudy Extension
<br>
If an implementer chooses to use the ResearchStudy resource, the workflow-researchStudy MAY optionally be used on the QuestionnaireResponses to capture that the QuestionnaireResponses are relevant to the specified research study(ies).
<br>
<br>
The official URL for the workflow-researchStudy is [http://hl7.org/fhir/StructureDefinition/workflow-researchStudy](http://hl7.org/fhir/StructureDefinition/workflow-researchStudy).
<br>
<br>




#### Optional Provenance Resource
<br>
<br>
If an implementer wishes to capture information about data creation, update, modification or deletion activities, the [Provenance](https://www.hl7.org/fhir/provenance.html) resource MAY be utilized. The Provenance resource can assist with data authenticity and assessing the entities involved with data being stored or transmitted via the system
<br>
<br>

#### Other implementation recommendations
<br>
<br>
The client software (the REST FHIR Questionnaire Management Software) will need to perform activities such as:

* Retrieving Questionnaires from the repository

* Displaying Questionnaires

* Populating Questionnaires

* Validating completed forms and submitting to the FHIR server for exchange and/or storage

* Retrieving Questionnaire Responses for edit and display

<br>
<br>
It is beyond the scope of this IG to provide detailed instructions on how to implement these functions, especially because the client REST FHIR Questionnaire Management Software could be the research study system of the lead principal investigator's institution, another type of software or the sIRB on FHIR software.
<br>
<br>



#### Some suggestions for Starter (Beginner) Implementation
<br>
<br>
##### The sIRB on FHIR software uses [LHC-Forms](http://lhncbc.github.io/lforms/), which is free and open source, to   render, populate, edit, validate and submit the forms to the FHIR Server. The LHC Forms software was created by the [U.S. National Library of Medicine (NLM)](https://www.nlm.nih.gov/).
<br>
<br>
##### LHC Forms includes [fhirpath.js](https://github.com/HL7/fhirpath.js/), which is needed for the [fhirpath](https://hl7.org/fhirpath/) that is used in the Answer Expression(s), Initial Expression(s), Calculated Expression(s) and Launch Context Expression(s) used in the Questionnaires.
<br>
<br>
##### FHIR Server
<br>
The sIRB IG is based on FHIR R4 (v4.0.1). Our assumption is that the implementer will have implemented a HAPI FHIR R4 Server that is running HAPI version 5.0.2 or later, or a FHIR Server that has the equivalent capabilities. 
<br>
<br>
The HAPI Server project page is at [https://hapifhir.io/hapi-fhir/](https://hapifhir.io/hapi-fhir/).
<br>
<br>
The HAPI Server free open-source download is available from [https://github.com/hapifhir/hapi-fhir](https://github.com/hapifhir/hapi-fhir).
<br>
<br>
For the sIRB project and IG, the HAPI FHIR JPA Starter Project available at [https://github.com/hapifhir/hapi-fhir-jpaserver-starter](https://github.com/hapifhir/hapi-fhir-jpaserver-starter)  was utilized. The JPA starter kit contains an embedded H2 Java Database as the default database, but it can be configured to use other databases. For more details on other database choices, see [https://hapifhir.io/hapi-fhir/docs/server_jpa/database_support.html](https://hapifhir.io/hapi-fhir/docs/server_jpa/database_support.html).
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>





Implementers should be aware that sIRB Questionnaires use [Expression-Based Population](http://hl7.org/fhir/uv/sdc/populate.html#exp-pop).



<br>
<br>


## Implementation Compliant with the sIRB IG
<br>

<br>
<br>

### Extensions
A system SHALL support the following extensions, which are used in the Questionnaires:
<br><br>
[choiceOrientation](http://hl7.org/fhir/StructureDefinition/questionnaire-choiceOrientation)
<br>
[displayCategory](http://hl7.org/fhir/StructureDefinition/questionnaire-displayCategory)
<br>
[hidden](http://hl7.org/fhir/StructureDefinition/questionnaire-hidden)
<br>
[itemControl](http://hl7.org/fhir/StructureDefinition/questionnaire-itemControl)
<br>
[supportLink](http://hl7.org/fhir/StructureDefinition/questionnaire-supportLink)
<br>
[unitOption](http://hl7.org/fhir/StructureDefinition/questionnaire-unitOption)
<br>
[variable](http://hl7.org/fhir/StructureDefinition/variable)
<br>
[rendering-style](http://hl7.org/fhir/StructureDefinition/rendering-style)
<br>
[rendering-xhtml](http://hl7.org/fhir/StructureDefinition/rendering-xhtml)
<br>
<br>
For more information about Questionnaire extensions, please see the [SDC Implementation Guide Extension definitions](http://hl7.org/fhir/uv/sdc/artifacts.html#structures-extension-definitions) and [SDC Implementation Guide Examples](http://hl7.org/fhir/uv/sdc/examples.html). 
<br>
<br>
### Questionnaire Population
The sIRB Questionnaires are [populatable](http://hl7.org/fhir/uv/sdc/populate.html#pre-population-service). Hence, implementation also assumes that the implementers will be knowledgeable about [SDC Form Population](http://hl7.org/fhir/uv/sdc/populate.html).

<br>
<br>
Implementers should be aware that sIRB Questionnaires use [Expression-Based Population](http://hl7.org/fhir/uv/sdc/populate.html#exp-pop).
<br>
<br>
The Questionnaires also utilize [answerExpression](http://hl7.org/fhir/uv/sdc/STU3/StructureDefinition-sdc-questionnaire-answerExpression.html) functionality from the Form Behavior and Calculation  (http://hl7.org/fhir/uv/sdc/STU3/behavior.html) section of the SDC IG in order to populate the drop-down list of [permitted](http://hl7.org/fhir/uv/sdc/STU3/behavior.html#choice-restriction) answers for some of the questions.  
<br>
For more information on Expressions, also see [Expression Extensions](http://hl7.org/fhir/uv/sdc/STU3/expressions.html)
<br>
<br>
The following SDC extensions SHALL be used for the populate functionality to work as described:

| Extension  |  
| -------------------------------------------------------------------------------------------------------- | 
| [Answer Expression](http://hl7.org/fhir/uv/sdc/StructureDefinition/sdc-questionnaire-answerExpression) |
| [Initial Expression](http://hl7.org/fhir/uv/sdc/StructureDefinition/sdc-questionnaire-initialExpression) |
| [Calculated Expression](http://hl7.org/fhir/uv/sdc/StructureDefinition/sdc-questionnaire-calculatedExpression) |
| [Launch Context](http://hl7.org/fhir/uv/sdc/StructureDefinition/sdc-questionnaire-launchContext)  |
|[variable](http://hl7.org/fhir/StructureDefinition/variable)| 
{: .grid}

<br>
<br>
### fhirpath
<br>
[fhirpath](https://hl7.org/fhirpath/) is used in the Answer Expression(s), Initial Expression(s), Calculated Expression(s) and Launch Context Expression(s) used in the Questionnaires. An implementation of fhirpath will need to be added if not bundled with the form software package.
<br>
<br>

## Optional ResearchStudy Resource
<br>
### ResearchStudy R4 Base Definition
If an implementer wishes to optionally use the ResearchStudy resource to transmit or persist data, the R4 base definition of the [ResearchStudy](https://www.hl7.org/fhir/researchstudy.profile.json.html) resource MAY be used.
<br>
<br>

### workflow-researchStudy Extension
<br>
If an implementer chooses to use the ResearchStudy resource, the workflow-researchStudy MAY optionally be used on the QuestionnaireResponses to capture that the QuestionnaireResponses are relevant to the specified research study(ies).
<br>
<br>
The official URL for the workflow-researchStudy is [http://hl7.org/fhir/StructureDefinition/workflow-researchStudy](http://hl7.org/fhir/StructureDefinition/workflow-researchStudy).
<br>
<br>






## Starter (Beginner) Implementation that is Compliant with the sIRB IG
<br>
### The Questionnaires were created using the [NLM Form Builder](https://lhcformbuilder.nlm.nih.gov/) which is free and open-source. The NLM Form Builder was created by the [U.S. National Library of Medicine (NLM)](https://www.nlm.nih.gov/).
<br>
<br>
### The forms are rendered, populated and submitted to the FHIR Server using [LHC-Forms](http://lhncbc.github.io/lforms/) which is free and open source. The LHC Forms software was created by the [U.S. National Library of Medicine (NLM)](https://www.nlm.nih.gov/).
<br>
<br>
### fhirpath
<br>
LHC Forms includes [fhirpath.js](https://github.com/HL7/fhirpath.js/), which is needed for the [fhirpath](https://hl7.org/fhirpath/) that is used in the Answer Expression(s), Initial Expression(s), Calculated Expression(s) and Launch Context Expression(s) used in the Questionnaires.
<br>
<br>
### FHIR Server
<br>
The sIRB IG is based on FHIR R4 (v4.0.1). Our assumption is that the implementer will have implemented a HAPI FHIR R4 Server that is running HAPI version 5.0.2 or later, or a FHIR Server that has the equivalent capabilities. 
<br>
<br>
The HAPI Server project page is at [https://hapifhir.io/hapi-fhir/](https://hapifhir.io/hapi-fhir/).
<br>
<br>
The HAPI Server free open-source download is available from [https://github.com/hapifhir/hapi-fhir](https://github.com/hapifhir/hapi-fhir).
<br>
<br>
For the sIRB project and IG, the HAPI FHIR JPA Starter Project available at [https://github.com/hapifhir/hapi-fhir-jpaserver-starter](https://github.com/hapifhir/hapi-fhir-jpaserver-starter)  was utilized. The JPA starter kit contains an embedded H2 Java Database as the default database, but it can be configured to use other databases. For more details on other database choices, see [https://hapifhir.io/hapi-fhir/docs/server_jpa/database_support.html](https://hapifhir.io/hapi-fhir/docs/server_jpa/database_support.html).
<br>
<br>


