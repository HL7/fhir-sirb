The Capability Statement does not capture all of the requirements for sIRB IG compliance. This page explains other requirements necessary to meet conformance expectations. It also discusses optional capabilities which could be implemented depending on the use case.

The sIRB IG assumes that the implementer is familiar with the [SDC Specification](http://hl7.org/fhir/uv/sdc/STU3/).
<br>
<br>

### Questionnaire and QuestionnaireResponse resources

#### Support and rendering for Questionnaire and QuestionnaireResponse

* To be compliant with this IG, a system SHALL support and render the eight [sIRB Questionnaires](artifacts.html#questionnaires).
<br>
<br>
* A system also SHALL support and render the QuestionnaireResponses.
<br>
<br>

#### Extensions for the Questionnaire and QuestionnaireResponse

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
### Expectations for Questionnaire Population

A client SHOULD utilize the [population](http://hl7.org/fhir/uv/sdc/populate.html#pre-population-service). functionality that is designed in the sIRB Questionnaires in this IG.

The sIRB Questionnaires are [populatable](http://hl7.org/fhir/uv/sdc/populate.html#pre-population-service). So that researchers do not need to re-type the same information into multiple forms, the sIRB forms are designed with one master form, the [Initiate a Study](Questionnaire-sirb-initiate-study-questionnaire-populate.html) questionnaire, that collects common data elements which will then be populatable into the other sIRB forms. Entering common data elements only once (via the [Initiate a Study](Questionnaire-sirb-initiate-study-questionnaire-populate.html) questionnaire) saves time for the researchers and study coordinators while reducing data entry errors.

Implementation also assumes that the implementers will be knowledgeable about [SDC Form Population](http://hl7.org/fhir/uv/sdc/populate.html).
<br>
<br>
Some guidance is provided here:

* The client software SHOULD be designed to function similar to the [population operations](http://hl7.org/fhir/uv/sdc/populate.html#population-operations) described in the SDC IG, but as a client-side process, rather than calling the FHIR server population operations.
<br>
<br>
* Implementers should be aware that sIRB Questionnaires use [Expression-Based Population](http://hl7.org/fhir/uv/sdc/populate.html#exp-pop).
<br>
<br>
* The Questionnaires also utilize [answerExpression](http://hl7.org/fhir/uv/sdc/STU3/StructureDefinition-sdc-questionnaire-answerExpression.html) functionality from the Form Behavior and Calculation  (http://hl7.org/fhir/uv/sdc/STU3/behavior.html) section of the SDC IG in order to populate the drop-down list of [permitted](http://hl7.org/fhir/uv/sdc/STU3/behavior.html#choice-restriction) answers for some of the questions.
<br>
<br>
* For more information on Expressions, also see [Expression Extensions](http://hl7.org/fhir/uv/sdc/STU3/expressions.html).
<br>
<br>
* The following SDC extensions SHOULD be used for the populate functionality to work as described:

<style type="text/css">
table{
margin-left: 35px
}
</style>


| Extension  |  
| -------------------------------------------------------------------------------------------------------- | 
| [Answer Expression](http://hl7.org/fhir/uv/sdc/StructureDefinition/sdc-questionnaire-answerExpression) |
| [Initial Expression](http://hl7.org/fhir/uv/sdc/StructureDefinition/sdc-questionnaire-initialExpression) |
| [Calculated Expression](http://hl7.org/fhir/uv/sdc/StructureDefinition/sdc-questionnaire-calculatedExpression) |
| [Launch Context](http://hl7.org/fhir/uv/sdc/StructureDefinition/sdc-questionnaire-launchContext)  |
|[variable](http://hl7.org/fhir/StructureDefinition/variable)| 
{: .grid}
<br>
* [fhirpath](https://hl7.org/fhirpath/) is used in the Answer Expression(s), Initial Expression(s), Calculated Expression(s) and Launch Context Expression(s) used in the Questionnaires. An [implementation of fhirpath](http://hl7.org/fhirpath/#fhirpath-tooling-and-implementation) will need to be included with the software client for the sIRB forms.
<br>
<br>



### Optional ResearchStudy Resource

#### ResearchStudy R4 Base Definition
If an implementer wishes to optionally use the ResearchStudy resource to transmit or persist data, the R4 base definition of the [ResearchStudy](https://www.hl7.org/fhir/researchstudy.profile.json.html) resource MAY be used.
<br>
#### workflow-researchStudy Extension
If an implementer chooses to use the ResearchStudy resource, the workflow-researchStudy MAY optionally be used on the QuestionnaireResponses to capture that the QuestionnaireResponses are relevant to the specified research study(ies).
<br>
<br>
The official URL for the workflow-researchStudy is [http://hl7.org/fhir/StructureDefinition/workflow-researchStudy](http://hl7.org/fhir/StructureDefinition/workflow-researchStudy).
<br>
<br>
### Optional Provenance Resource

If an implementer wishes to capture information about data creation, update, modification or deletion activities, the [Provenance](https://www.hl7.org/fhir/provenance.html) resource MAY be utilized. The Provenance resource can assist with data authenticity and assessing the entities involved with data being stored or transmitted via the system.
<br>
<br>
### Other implementation recommendations

The client software (the REST FHIR Questionnaire Management Software) will need to perform activities such as:

* Retrieving Questionnaires from the repository

* Displaying Questionnaires

* Populating Questionnaires

* Validating completed forms and submitting to the FHIR server for exchange and/or storage

* Retrieving Questionnaire Responses for edit and display

* Extracting data from the Initiate a Study Questionnaire Response to create and update the ResearchStudy resource (if the optional ResearchStudy resource is being used)

* Creating the workflow-researchStudy extension (if the optional workflow-researchStudy extension is being used)

* Creating the optional Provenance resource and providing the data for the elements of the resource
<br>
<p>It is beyond the scope of this IG to provide detailed instructions on how to implement these functions, especially because the client REST FHIR Questionnaire Management Software could be the research study system of the lead principal investigator's institution, another type of software or the sIRB on FHIR software.
</p>
<br>


### Some suggestions for Starter (Beginner) Implementation

#### LHC-Forms
The sIRB on FHIR software uses [LHC-Forms](http://lhncbc.github.io/lforms/), which is free and open source, to render, populate, edit, validate and submit the forms to the FHIR Server. The LHC Forms software was created by the [U.S. National Library of Medicine (NLM)](https://www.nlm.nih.gov/).
<br>
<br>
LHC Forms includes [fhirpath.js](https://github.com/HL7/fhirpath.js/), which is needed for the [fhirpath](https://hl7.org/fhirpath/) that is used in the Answer Expression(s), Initial Expression(s), Calculated Expression(s) and Launch Context Expression(s) used in the Questionnaires.
<br>
<br>
#### FHIR Server

The sIRB IG is based on FHIR R4 (v4.0.1). Please see the [FHIR Server requirements](conformance_and_functionality_expectations.html#fhir-server).  
<br>
If interested in using the HAPI server, implementers can refer to the HAPI Server project page at [https://hapifhir.io/hapi-fhir/](https://hapifhir.io/hapi-fhir/).  The HAPI Server free open-source download is available from [https://github.com/hapifhir/hapi-fhir](https://github.com/hapifhir/hapi-fhir).
<br>
<br>
For the sIRB IG, the HAPI FHIR JPA Starter Project available at [https://github.com/hapifhir/hapi-fhir-jpaserver-starter](https://github.com/hapifhir/hapi-fhir-jpaserver-starter)  was utilized. The JPA starter kit contains an embedded H2 Java Database as the default database, but it can be configured to use other databases. For more details on other database choices, see [https://hapifhir.io/hapi-fhir/docs/server_jpa/database_support.html](https://hapifhir.io/hapi-fhir/docs/server_jpa/database_support.html).