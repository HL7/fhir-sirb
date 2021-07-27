The conformance and functionality expectations of each type of actor is listed below.  In general, the sIRB will be the institution hosting the sIRB FHIR server that stores the Questionnaires and the QuestionnaireResponses.  The host institution will also host a website or other sIRB software to render the blank forms and display the completed questionnaire responses for edits, review or saving to pdf.

ADD LINK  https://www.hl7.org/fhir/http.html
The exchange framework used is the "RESTful FHIR". 
REMEMBER TO LINK EACH BOLDED TERM TO THE CORE SPEC
CREATE  https://www.hl7.org/fhir/http.html#create
SEARCH   https://www.hl7.org/fhir/http.html#search
UPDATE   https://www.hl7.org/fhir/http.html#update
PATCH  https://www.hl7.org/fhir/http.html#patch
Host of the FHIR server (generally the sIRB)
FHIR server compliant with FHIR 4.0 and SDC
Questionnaire: SHALL support search by url, version and/or status.  MAY also support search by _lastUpdated
QuestionnaireResponse: SHALL support create and update with version-checking.  SHALL also support search by questionnaire, author and _lastUpdated.  MAY support patch
ResearchStudy: MAY support create and update with version-checking.  MAY also support search by identifier


REMEMBER TO LINK EACH BOLDED TERM TO THE CORE SPEC

FHIR Questionnaire Management Software (could be the host institution’s research study system, another type of software or the sIRB on FHIR software)

Questionnaire: SHALL support search by url, version and/or status.  MAY also support search by _lastUpdated
QuestionnaireResponse: SHALL support create and update with version-checking.  SHALL also support search by questionnaire, author and _lastUpdated.  MAY support patch
ResearchStudy: MAY support create and update with version-checking.  MAY also support search by identifier



Non-host (generally the relying sites)
If the non-host wishes to interact with the forms without the requirement of having a FHIR server, then the host institution must provide software or a website with the software for viewing, completing and storing the forms on the host institution’s FHIR server that can be accessed via a web browser
If the non-host wish to use a FHIR server, then the FHIR server should have the capabilities defined in the “Host of the FHIR server (generally the sIRB)”  section.
