<h2>FHIR Server</h2>
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
<h2>Required and Optional Resources</h2>
<br>
The FHIR R4 resources required for this IG are:
Questionnaire
<br>
QuestionnaireResponse
<br>
<br>
Optional FHIR R4 resource utilized in this IG:
ResearchStudy
<br>
<br>




<h2>Implementation Using the [NLM Form Builder](https://lhcformbuilder.nlm.nih.gov/) and [LHC-Forms](http://lhncbc.github.io/lforms/)</h2>
<br>
The sIRB IG assumes that the implementer is using the [SDC Specification]( http://hl7.org/fhir/uv/sdc/StructureDefinition/sdc-questionnaireresponse).
<br>
<br>
The Questionnaires were built with the free and open source NLM Form Builder available from [https://lhcformbuilder.nlm.nih.gov/](https://lhcformbuilder.nlm.nih.gov/)
<br>
<br>
The Questionnaires and Questionnaire Responses are rendered with the free and open source LHC Forms software available from [http://lhncbc.github.io/lforms/](http://lhncbc.github.io/lforms/).
<br>
<br>

To get the full functionality that is described in this IG, the following SDC profiles SHOULD be used:
<br>
[SDC Questionnaire Response](http://hl7.org/fhir/uv/sdc/StructureDefinition/sdc-questionnaireresponse)
<br>
[SDC Base Questionnaire](http://hl7.org/fhir/uv/sdc/StructureDefinition/sdc-questionnaire)
<br>
[Populatable Questionnaire - Expression](http://hl7.org/fhir/uv/sdc/StructureDefinition/sdc-questionnaire-pop-exp)
<br>
[Advanced Behavior Questionnaire](http://hl7.org/fhir/uv/sdc/StructureDefinition/sdc-questionnaire-behave) 
<br>
[Advanced Rendering Questionnaire](http://hl7.org/fhir/uv/sdc/StructureDefinition/sdc-questionnaire-render)
<br>
<br>

The following SDC extensions SHALL be used for the populate functionality to work as described:

| Extension  | Profile   |  
| -------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- | 
| [Answer Expression](http://hl7.org/fhir/uv/sdc/StructureDefinition/sdc-questionnaire-answerExpression)  | [Populatable Questionnaire - Expression](http://hl7.org/fhir/uv/sdc/StructureDefinition/sdc-questionnaire-pop-exp)  |
| [Initial Expression](http://hl7.org/fhir/uv/sdc/StructureDefinition/sdc-questionnaire-initialExpression)    | [Populatable Questionnaire - Expression](http://hl7.org/fhir/uv/sdc/StructureDefinition/sdc-questionnaire-pop-exp) |
| [Calculated Expression](http://hl7.org/fhir/uv/sdc/StructureDefinition/sdc-questionnaire-calculatedExpression)   | [Populatable Questionnaire - Expression](http://hl7.org/fhir/uv/sdc/StructureDefinition/sdc-questionnaire-pop-exp)  |
| [Launch Context](http://hl7.org/fhir/uv/sdc/StructureDefinition/sdc-questionnaire-launchContext)  |   [Populatable Questionnaire - Expression](http://hl7.org/fhir/uv/sdc/StructureDefinition/sdc-questionnaire-pop-exp)  |
{: .grid}

<br>
<br>





<h2>Implementation Without Using the [NLM Form Builder](https://lhcformbuilder.nlm.nih.gov/) and [LHC-Forms](http://lhncbc.github.io/lforms/)</h2>
<br>
If an implementer does not desire to use the NLM Form Builder and/or the LHC Forms software, then the implementer SHOULD implement a system that additionally utilizes everything described in the [Implementation Using the NLM Form Builder and LHC-Forms](#implementation-using-the-nlm-form-builder-and-lhc-forms) section above plus the following:
 <br>
<h3>Capabilities</h3>
<br>
[SDC Form Designer](http://hl7.org/fhir/uv/sdc/CapabilityStatement/sdc-form-designer)
<br>
[SDC Form Response Manager](http://hl7.org/fhir/uv/sdc/CapabilityStatement/sdc-form-response-manager)
<br>
[SDC Form Filler](http://hl7.org/fhir/uv/sdc/CapabilityStatement/sdc-form-filler)
<br>
[SDC Form Manager](http://hl7.org/fhir/uv/sdc/CapabilityStatement/sdc-form-manager)
<br>
[SDC Form Receiver](http://hl7.org/fhir/uv/sdc/CapabilityStatement/sdc-form-receiver)
<br>
[SDC Form Archiver](http://hl7.org/fhir/uv/sdc/CapabilityStatement/sdc-form-archiver)
<br>
<br>
<h3>Operations</h3>
<br>
[Populate Questionnaire](http://hl7.org/fhir/uv/sdc/OperationDefinition/Questionnaire-populate)
<br>
<br>




<h2>Core and Questionnaire Extensions Used in the sIRB IG</h2>
<br>
<h3>Questionnaire Extensions</h3>
<br>
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
<br>

<h3>Base FHIR Extensions</h3>
<br>
[rendering-style](http://hl7.org/fhir/StructureDefinition/rendering-style)
<br>
[rendering-xhtml](http://hl7.org/fhir/StructureDefinition/rendering-xhtml)
<br>
<br>







<h2>Optional ResearchStudy Resource</h2>
<br>
<h3>ResearchStudy R4 Base Definition</h3>
If an implementer wishes to optionally use the ResearchStudy resource to transmit or persist data, the R4 base definition of the [ResearchStudy](https://www.hl7.org/fhir/researchstudy.profile.json.html) resource MAY be used.
<br>
<br>

<h3>workflow-researchStudy Extension</h3>
<br>
If an implementer chooses to use the ResearchStudy resource, the workflow-researchStudy MAY optionally be used on the QuestionnaireResponses to capture that the QuestionnaireResponses are relevant to the specified research study(ies).
<br>
<br>
The official URL for the workflow-researchStudy is [http://hl7.org/fhir/StructureDefinition/workflow-researchStudy](http://hl7.org/fhir/StructureDefinition/workflow-researchStudy).
<br>
<br>

<h2>fhirpath</h2>
<br>
[fhirpath](https://hl7.org/fhirpath/) is used in the Answer Expression(s), Initial Expression(s), Calculated Expression(s) and Launch Context Expression(s) used in the Questionnaires. LHC Forms includes [fhirpath.js](https://github.com/HL7/fhirpath.js/). If other form software is used, an implementation of fhirpath will need to be added if not bundled with the form software package.


