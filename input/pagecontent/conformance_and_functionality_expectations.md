
### Actors

**Host (generally the lead principal investigator's institution)**

In general, the lead principal investigator's institution will be the institution hosting the sIRB FHIR server that stores the Questionnaires and the QuestionnaireResponses. This is the server referenced in the [sIRB Capability Statement](CapabilityStatement-sIRB-CapabilityStatement.html). 

The lead principal investigator's institution will also host a website or other sIRB software to render the blank forms and display the completed questionnaire responses for edits, review or saving to pdf. This is the client referenced in the [sIRB Capability Statement](CapabilityStatement-sIRB-CapabilityStatement.html).  The client REST FHIR Questionnaire Management Software could be the research study system of the lead principal investigator's institution, another type of software or the sIRB on FHIR software).

**Single Institutional Review Board (sIRB)**
The single Institutional Review Board (sIRB) is either the ethics review board at the lead principal investigator's institution or a 3rd party ethics review board retained by the lead principal investigator's institution. The sIRB will need access to the research study system, the sIRB on FHIR software or other sIRB software to review the completed forms.
<br>
<br>


**Relying Sites (generally non-hosts)**
If the relying sites wish to interact with the forms without the requirement of having a FHIR server, then the host institution must provide client software, such as the sIRB on FHIR software, or a website with the client software for viewing, completing and storing the forms on the host institution's FHIR server. If the relying sites wish to use a FHIR server, then the FHIR server should have the capabilities defined in the "Host (generally the lead principal investigator's institution)" section.
<br>
<br>



### Exchange Framework

The exchange framework used is the "[RESTful FHIR](https://www.hl7.org/fhir/http.html)".
<br>
<br>

### Conformance Verbs

The conformance verbs - SHALL, SHOULD, MAY - used in this implementation guide are defined in [FHIR Conformance Language](http://hl7.org/fhir/R4/conformance-rules.html#conflang0).
<br>
<br>

### Capability Statement

The [sIRB Capability Statement](CapabilityStatement-sIRB-CapabilityStatement.html) describes the expectations for the client and server. A compliant server SHALL adhere to the requirements listed in this resource, and implement the RESTful behavior according to the FHIR specification. A compliant client SHALL adhere to the requirements listed in this resource, and implement the RESTful behavior according to the FHIR specification.
<br>
<br>

### FHIR Server

The sIRB IG is based on [FHIR R4 (v4.0.1)](https://www.hl7.org/fhir/R4/). Our assumption is that the implementer will have implemented one of the following:

* a [HAPI FHIR R4 Server](https://hapifhir.io/) that is running [HAPI version 5.0.2](https://hapifhir.io/hapi-fhir/docs/getting_started/versions.html) or later
* a FHIR Server that has the equivalent capabilities as a HAPI FHIR R4 Server that is running HAPI version 5.0.2 or later
* a FHIR server that conforms with the [sIRB Capability Statement](CapabilityStatement-sIRB-CapabilityStatement.html).
