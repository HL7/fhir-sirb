# Profiles and StructureDefinitions Relevant to sIRB IG
<br>
<br>
## Implementation Using the [NLM Form Builder](https://lhcformbuilder.nlm.nih.gov/) and [LHC-Forms](http://lhncbc.github.io/lforms/)
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





## Implementation Without Using the [NLM Form Builder](https://lhcformbuilder.nlm.nih.gov/) and [LHC-Forms](http://lhncbc.github.io/lforms/)
<br>
If an implementer does not desire to use the NLM Form Builder and/or the LHC Forms software, then the implementer SHOULD implement a system that additionally utilizes everything described in the [Implementation Using the NLM Form Builder and LHC-Forms](#implementation-using-the-nlm-form-builder-and-lhc-forms) section above plus the following:
 <br>
### Capabilities
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
### Operations
<br>
[Populate Questionnaire](http://hl7.org/fhir/uv/sdc/OperationDefinition/Questionnaire-populate)
<br>
<br>




## Core and Questionnaire Extensions Used in the sIRB IG
<br>
### Questionnaire Extensions
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

### Base FHIR Extensions
<br>
[rendering-style](http://hl7.org/fhir/StructureDefinition/rendering-style)
<br>
[rendering-xhtml](http://hl7.org/fhir/StructureDefinition/rendering-xhtml)
<br>
<br>







## ResearchStudy Resource Base Definition
<br>
If an implementer wishes to optionally use the ResearchStudy resource to transmit or persist data, the R4 base definition of the [ResearchStudy](https://www.hl7.org/fhir/researchstudy.profile.json.html) resource MAY be used.
<br>
<br>

## workflow-researchStudy Extension
<br>
If an implementer chooses to use the ResearchStudy resource, the workflow-researchStudy MAY optionally be used on the QuestionnaireResponses to capture that the QuestionnaireResponses are relevant to the specified research study(ies).
<br>
<br>
The official URL for the workflow-researchStudy is [http://hl7.org/fhir/StructureDefinition/workflow-researchStudy](http://hl7.org/fhir/StructureDefinition/workflow-researchStudy).
<br>
<br>

# fhirpath
<br>
[fhirpath](https://hl7.org/fhirpath/) is used in the Answer Expression(s), Initial Expression(s), Calculated Expression(s) and Launch Context Expression(s) used in the Questionnaires.


