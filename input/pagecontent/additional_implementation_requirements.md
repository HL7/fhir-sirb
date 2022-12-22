The Capability Statement does not capture all of the requirements for sIRB IG compliance. This page explains other requirements necessary to meet conformance expectations. It also discusses optional capabilities which could be implemented depending on the use case.

The sIRB IG assumes that the implementer is familiar with the [SDC Specification](http://hl7.org/fhir/uv/sdc/STU3/).
<br>
<br>

### Questionnaire and QuestionnaireResponse resources

#### Support and rendering for Questionnaire and QuestionnaireResponse

* To be compliant with this IG, a system SHALL render the eight [sIRB Questionnaires](artifacts.html#questionnaires) and display the completed QuestionnaireResponse for edits, review or saving to pdf.
<br>
<br>
#### Extensions for the Questionnaire and QuestionnaireResponse

The following extensions are used in the sIRB Questionnaires in order to make the Questionnaires display and function as described in the examples, as tested by prospective users and as shown in the [forms rendered by the Questionnaire Viewer](index.html#renderedForms):
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
Style decisions, color choices and orientation of the questions and/or answers were developed using feedback from prospective users. If the forms are integrated into other research study systems, harmonization of the appearance of the forms with the design of the research study system will not result in non-compliance with the IG.
<br>
<br>
If an implementer chooses to use the optional ResearchStudy resource, the workflow-researchStudy MAY optionally be used on the QuestionnaireResponses to capture that the QuestionnaireResponses are relevant to the specified research study(ies). The official URL for the workflow-researchStudy is [http://hl7.org/fhir/StructureDefinition/workflow-researchStudy](http://hl7.org/fhir/StructureDefinition/workflow-researchStudy).
<br>
<br>
### Expectations for Questionnaire Population

The sIRB Questionnaires are [populatable](http://hl7.org/fhir/uv/sdc/populate.html#pre-population-service). The sIRB forms are designed with one master form, the [Initiate a Study](Questionnaire-sirb-initiate-study-questionnaire-populate.html) questionnaire, that collects common data elements which will then be populatable into the other sIRB forms so that researchers do not need to re-type the same information into multiple forms. Entering common data elements only once (via the [Initiate a Study](Questionnaire-sirb-initiate-study-questionnaire-populate.html) questionnaire) saves time for the researchers and study coordinators while reducing data entry errors.
<br>
Implementation assumes that the implementers will be knowledgeable about [SDC Form Population](http://hl7.org/fhir/uv/sdc/populate.html).
<br>

* The following SDC extensions are used in the Questionnaires to make the populate functionality work as described:

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
<br>


Some guidance is provided here:

* The client software can be designed to function similar to the [population operations](http://hl7.org/fhir/uv/sdc/populate.html#population-operations) described in the SDC IG, but as a client-side process, rather than calling the FHIR server population operations.
<br>
<br>
* The sIRB Questionnaires use [Expression-Based Population](http://hl7.org/fhir/uv/sdc/populate.html#exp-pop).
<br>
<br>
* The Questionnaires also utilize [answerExpression](http://hl7.org/fhir/uv/sdc/STU3/StructureDefinition-sdc-questionnaire-answerExpression.html) functionality from the [Form Behavior and Calculation](http://hl7.org/fhir/uv/sdc/STU3/behavior.html) section of the SDC IG in order to populate the drop-down list of [permitted](http://hl7.org/fhir/uv/sdc/STU3/behavior.html#choice-restriction) answers for some of the questions.
<br>
<br>
* For more information on Expressions, also see [Expression Extensions](http://hl7.org/fhir/uv/sdc/STU3/expressions.html).
<br>
<br>
* [fhirpath](https://hl7.org/fhirpath/) is used in the Answer Expression(s), Initial Expression(s), Calculated Expression(s) and Launch Context Expression(s) used in the Questionnaires. An [implementation of fhirpath](http://hl7.org/fhirpath/#fhirpath-tooling-and-implementation) will need to be included with the software client for the sIRB forms.
<br>
<br>

### Other implementation recommendations

The client software ([REST FHIR Questionnaire Management Software](conformance_and_functionality_expectations.html#clientSoftware))   ([REST FHIR Questionnaire Management Software](conformance/_and/_functionality/_expectations.html#clientSoftware)) will need to perform activities such as:

* Retrieving Questionnaires from the repository

* Displaying Questionnaires

* Populating Questionnaires

* Validating completed forms and submitting to the FHIR server for exchange and/or storage

* Retrieving Questionnaire Responses for edit and display

* Extracting data from the Initiate a Study Questionnaire Response to create and update the ResearchStudy resource (if the optional ResearchStudy resource is being used)

* Creating the workflow-researchStudy extension (if the optional workflow-researchStudy extension is being used)

* Creating the optional Provenance resource and providing the data for the elements of the resource
<br>
It is beyond the scope of this IG to provide detailed instructions on how to implement these functions, especially because the client [REST FHIR Questionnaire Management Software](conformance_and_functionality_expectations.html#clientSoftware) could be the research study system of the lead principal investigator's institution, another type of software or the sIRB on FHIR software.
<br>
<br>
### RESTFUL interactions

Some of the [RESTFUL interactions](https://www.hl7.org/fhir/http.html) that implementers may find useful for the exchange of resources are listed here. Please consult the [General Considerations](https://www.hl7.org/fhir/http.html#general) section if there are questions about the meaning of any components in the interaction definitions.

http commands:

* A Questionnaire can be retrieved either by read or search by _id
```
GET [base]/Questionnaire/[id]
```

    or

```
GET [base]/Questionnaire?_id=[id]
```

* A QuestionnaireResponse can be retrieved either by read or search by _id

```
GET [base]/QuestionnaireResponse/[id]
```

    or

```
GET [base]/QuestionnaireResponse?_id=[id]
```

* A completed form can be sent to the FHIR server using POST:

```
POST [base]/QuestionnaireResponse
```

* If the optional ResearchStudy resource and/or the Provenance resource(s) are part of the implementation, they can be created using POST also:

```
POST [base]/ResearchStudy
```

    and/or

```
POST [base]/Provenance
```

* vread can help the implementer retrieve a specific version of a QuestionnaireResponse

```
GET [base]/QuestionnaireResponse/[id]/_history/[vid]
```


* As discussed at [https://www.hl7.org/fhir/questionnaireresponse.html#scope](https://www.hl7.org/fhir/questionnaireresponse.html#scope), QuestionnaireResponses are often retrieved with the cooresponding Questionnaire in order to display the questions, allow for editing of the answers or to validate answers against the Questionnaire definitions. The Questionnaire can be included as follows:

```
GET [base]/QuestionnaireResponse?_id=[id]&_include=QuestionnaireResponse:questionnaire
```

* If the QuestionnaireResponse \_id is unknown, the \_id of the Questionnaire can be used as a search parameter:

```
GET [base]/QuestionnaireResponse?questionnaire=[id]&_include=QuestionnaireResponse:questionnaire
```


* The update interaction is used to send an updated/edited QuestionnaireResponse to the FHIR server:

```
PUT [base]/QuestionnaireResponse/[id]
```

    <br>The sIRB IG allows for the [patch](https://www.hl7.org/fhir/http.html#patch) interaction, if implementers wish to use patch to only update a portion of a resource.
<br>
In addition to the search interactions discussed above, the [sIRB Server Capability Statement](CapabilityStatement-sIRB-CapabilityStatementServer.html) and the [sIRB Client Capability Statement] (CapabilityStatement-sIRB-CapabilityStatementClient.html) provide other possible search parameters. In the event that the data from the completed forms will be persisted outside of the FHIR server, many of the search functions listed in the [sIRB Server Capability Statement](CapabilityStatement-sIRB-CapabilityStatementServer.html) and the [sIRB Client Capability Statement] (CapabilityStatement-sIRB-CapabilityStatementClient.html) could foreseeably be handled by another system. Hence, many of the search parameters in the sirb Capability Statements are listed as "MAY" because some implementations will handle data searching in another system.