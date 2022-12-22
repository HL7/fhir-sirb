
### Actors

**Host of the FHIR server (generally the lead principal investigator's institution)**<a id="fhirServer"></a><br>
In general, the lead principal investigator's institution will host the sIRB FHIR server that stores the Questionnaires and the QuestionnaireResponses. This is the server referenced in the [sIRB Server Capability Statement](CapabilityStatement-sIRB-CapabilityStatementServer.html). 

**FHIR Questionnaire Management Software (could be the host institution’s research study system, another type of software or the sIRB on FHIR software)**<a id="clientSoftware"></a>
The lead principal investigator's institution will also host a website or other sIRB software to render the blank forms and display the completed questionnaire responses for edits, review or saving to pdf. This is the client referenced in the [sIRB Client Capability Statement](CapabilityStatement-sIRB-CapabilityStatementClient.html).  The client REST FHIR Questionnaire Management Software could be the research study system of the lead principal investigator's institution, another type of software or the sIRB on FHIR software).
<br>
The single Institutional Review Board (sIRB) is either the ethics review board at the lead principal investigator's institution or a 3rd party ethics review board retained by the lead principal investigator's institution. The sIRB is listed here as relevant for business practices and for workflow processes, although it is not a separate actor because it acting on behalf of the lead principal investigator's institution. The sIRB will need access to the research study system, the sIRB on FHIR software or other sIRB software to review the completed forms.
<br>
<br>
**Relying Sites (generally non-hosts)**<br>
If the relying sites wish to interact with the forms without the requirement of having a FHIR server, then the host institution must provide [client software](#clientSoftware) or a website with the client software for viewing, completing and storing the forms on the host institution's FHIR server. If the relying sites wish to use a FHIR server, then the FHIR server SHOULD have the capabilities defined in the "[Host of the FHIR server (generally the lead principal investigator's institution)](#fhirServer)" section.
<br>
<br>
In the future state, ideally, an organization can be identified to host the official versions of the forms. If an organization is found to host the forms, then the capabilities will be the same as [sIRB Server Capability Statement](CapabilityStatement-sIRB-CapabilityStatementServer.html), but using only the Questionnaire resource.
<br>
<br>

### Conformance Verbs

The conformance verbs - SHALL, SHOULD, MAY - used in this implementation guide are defined in [FHIR Conformance Language](http://hl7.org/fhir/R4/conformance-rules.html#conflang0).
<br>
<br>

### Capability Statements

The [sIRB Server Capability Statement](CapabilityStatement-sIRB-CapabilityStatementServer.html) describes the expectations for the server. A compliant server SHALL adhere to the requirements listed in this resource, and implement the RESTful behavior according to the FHIR specification. 
<br>

The [sIRB Client Capability Statement](CapabilityStatement-sIRB-CapabilityStatementClient.html) describes the expectations for the client. A compliant client SHALL adhere to the requirements listed in this resource, and implement the RESTful behavior according to the FHIR specification.
<br>
<br>

