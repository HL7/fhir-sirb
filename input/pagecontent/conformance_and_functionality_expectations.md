# EXISTING CONTENT IS HERE
<br>
<br>


The conformance and functionality expectations of each type of actor is listed below.  In general, the sIRB will be the institution hosting the sIRB FHIR server that stores the Questionnaires and the QuestionnaireResponses.  The host institution will also host a website or other sIRB software to render the blank forms and display the completed questionnaire responses for edits, review or saving to pdf.

The exchange framework used is the "[RESTful FHIR](https://www.hl7.org/fhir/http.html)". 

**Host of the FHIR server (generally the sIRB)**
FHIR server compliant with FHIR 4.0 and SDC
Questionnaire: 
SHALL support **[search](https://www.hl7.org/fhir/http.html#search)** by url, version and/or status.  
MAY also support search by _lastUpdated

QuestionnaireResponse: 
SHALL support **[create](https://www.hl7.org/fhir/http.html#create)** and **[update](https://www.hl7.org/fhir/http.html#update)** with version-checking.  
SHALL also support **[search](https://www.hl7.org/fhir/http.html#search)** by questionnaire, author and _lastUpdated.  
MAY support **[patch](https://www.hl7.org/fhir/http.html#patch)**

ResearchStudy: 
MAY support **[create](https://www.hl7.org/fhir/http.html#create)** and **[update](https://www.hl7.org/fhir/http.html#update)** with version-checking.  
MAY also support **[search](https://www.hl7.org/fhir/http.html#search)** by identifier



**FHIR Questionnaire Management Software (could be the host institution’s research study system, another type of software or the sIRB on FHIR software)**

Questionnaire: SHALL support **[search](https://www.hl7.org/fhir/http.html#search)** by url, version and/or status.  MAY also support search by _lastUpdated
QuestionnaireResponse: SHALL support **[create](https://www.hl7.org/fhir/http.html#create)** and **[update](https://www.hl7.org/fhir/http.html#update)** with version-checking.  SHALL also support **[search](https://www.hl7.org/fhir/http.html#search)** by questionnaire, author and _lastUpdated.  MAY support **[patch](https://www.hl7.org/fhir/http.html#patch)**
ResearchStudy: MAY support **[create](https://www.hl7.org/fhir/http.html#create)** and **[update](https://www.hl7.org/fhir/http.html#update)** with version-checking.  MAY also support **[search](https://www.hl7.org/fhir/http.html#search)** by identifier



**Non-host (generally the relying sites)**
If the non-host wishes to interact with the forms without the requirement of having a FHIR server, then the host institution must provide software or a website with the software for viewing, completing and storing the forms on the host institution’s FHIR server that can be accessed via a web browser
If the non-host wish to use a FHIR server, then the FHIR server should have the capabilities defined in the “Host of the FHIR server (generally the sIRB)”  section.


<br>
<br>
# NEW CONTENT BELOW
<br>
<br>

## Implementation Compliant with the sIRB IG
<br>
The sIRB IG assumes that the implementer is familiar with the [SDC Specification]( http://hl7.org/fhir/uv/sdc/StructureDefinition/sdc-questionnaireresponse).
<br>
<br>
To be compliant with this IG, a system SHALL support and render the eight [sIRB Questionnaires](artifacts.html#sirb-questionnaires).
<br>
<br>
A system SHALL also SHALL support and render the QuestionnaireResponses.
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
Specifically, the implementation requires that the Form Filler client utilize the [$populate operation](http://hl7.org/fhir/uv/sdc/OperationDefinition-Questionnaire-populate.html).
<br>
Implementers should be aware that sIRB Questionnaires use [Expression-Based Population](http://hl7.org/fhir/uv/sdc/populate.html#exp-pop).
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


## REST client behavior (Form Management Software)
<br>
<br>
### THESE ARE MOCK UPS. HAVE NOT COMPLETED THE JSON CAPABILITY STATEMENTS YET
<br>
<br>
### General
<br>
| --------------------------|--------------------- | 
| FHIR Version:	 |v4.0.1|
| Supported formats:	 |xml, json|
{: .grid}
<br>
<br>
### Security:
<br>
Implementations must meet the general security requirements documented at [FHIR Security]( http://hl7.org/fhir/R4/security.html).
<br>
<br>
### Resource summary
<br>
| Resource |  Search  | 	Read  | 	Read Version  | 	Instance History   | 	Resource History  | 	Create	 | Update  | 	Delete   | 	Operations  | 
| ------- |  -------  | 	-------  | -------  | 	-------  | 	-------  | 	-------	 | -------  | 	-------   | 	-------  | 
| Questionnaire |  SHALL   | 	SHALL   | 	SHALL  | 	   | 	  | 	SHALL 	 | SHALL (with version-checking)   | 	   | $populate	  |
| QuestionnaireResponse |  SHALL   | 	SHALL   | 	SHALL   | 	MAY   | 	 | 	SHALL 	 | SHALL  (with version-checking)  | 	MAY   | 	  |
| CodeSystem |    | 	SHALL  | 	SHALL  | 	   | 	| 	SHALL	 | SHALL  | 	   | 	  |
| ResearchStudy |  MAY  | 	MAY  | 	MAY  | 	  | 	 | 	MAY	 | MAY (with version-checking)  | 	MAY   | 	  |
{: .grid}
<br>
<br>





### Search (Questionnaire)
<br>
| Parameter | Conformance |	Type  |	Definition & Chaining  |
| -------	 |------- |	-------	| -------      |
| _id	 |SHALL |	token	|      |
| version	 |SHALL |	token	|      |
| status	 |SHALL |	token	|      |
| _lastUpdated	 |MAY |	date	|      |
{: .grid}
<br>
<br>

### Search (QuestionnaireResponse)
<br>
| Parameter | Conformance |	Type  |	Definition & Chaining  |
| -------	 |------- |	-------	| -------      |
| _id	 |SHALL |	token	|      |
| questionnaire	 |SHALL |	reference 	|      |
| author	 |SHALL |	token	|      |
| _lastUpdated	 |MAY |	date	|      |
{: .grid}

<br>
<br>

### Search (ResearchStudy)
<br>
| Parameter | Conformance |	Type  |	Definition & Chaining  |
| -------	 |------- |	-------	| -------      |
| _id	 |MAY |	token	|      |
{: .grid}
<br>
<br>



## REST server behavior (FHIR Server)
<br>
<br>
### THESE ARE MOCK UPS. HAVE NOT COMPLETED THE JSON CAPABILITY STATEMENTS YET
<br>
<br>
### General
<br>
| --------------------------|--------------------- | 
| FHIR Version:	 |v4.0.1|
| Supported formats:	 |xml, json|
{: .grid}
<br>
<br>
### Security:
<br>
Implementations must meet the general security requirements documented at [FHIR Security]( http://hl7.org/fhir/R4/security.html).
<br>
<br>
### Resource summary
<br>
| Resource |  Search  | 	Read  | 	Read Version  | 	Instance History   | 	Resource History  | 	Create	 | Update  | 	Delete   | 	Operations  | 
| ------- |  -------  | 	-------  | -------  | 	-------  | 	-------  | 	-------	 | -------  | 	-------   | 	-------  | 
| Questionnaire |  SHALL   | 	SHALL   | 	SHALL  | 	   | 	  | 	SHALL 	 | SHALL (with version-checking)   | 	   | 	  |
| QuestionnaireResponse |  SHALL   | 	SHALL   | 	SHALL   | 	MAY   | 	 | 	SHALL 	 | SHALL  (with version-checking)  | 	MAY   | 	  |
| CodeSystem |    | 	SHALL  | 	SHALL  | 	   | 	| 	SHALL	 | SHALL  | 	   | 	  |
| ResearchStudy |  MAY  | 	MAY  | 	MAY  | 	  | 	 | 	MAY	 | MAY (with version-checking)  | 	MAY   | 	  |
{: .grid}
<br>
<br>

### Search (Questionnaire)
<br>
| Parameter | Conformance |	Type  |	Definition & Chaining  |
| -------	 |------- |	-------	| -------      |
| _id	 |SHALL |	token	|      |
| version	 |SHALL |	token	|      |
| status	 |SHALL |	token	|      |
| _lastUpdated	 |MAY |	date	|      |
{: .grid}
<br>
<br>

### Search (QuestionnaireResponse)
<br>
| Parameter | Conformance |	Type  |	Definition & Chaining  |
| -------	 |------- |	-------	| -------      |
| _id	 |SHALL |	token	|      |
| questionnaire	 |SHALL |	reference 	|      |
| author	 |SHALL |	token	|      |
| _lastUpdated	 |MAY |	date	|      |
{: .grid}
<br>
<br>


### Search (ResearchStudy)
<br>
| Parameter | Conformance |	Type  |	Definition & Chaining  |
| -------	 |------- |	-------	| -------      |
| _id	 |MAY |	token	|      |
{: .grid}
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


