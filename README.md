# Cortex Development Code Test

Please review the following exercises before you begin.  If you require additional clarification please compile your questions and send them to: <TBD>

Complete the main project and your choice of any two of the additional projects.

## MAIN PROJECT (required):

Your task is to build a flow which will collect and parse input data, persist the parsed data and present a report.  This flow will be implemented by using micro-services.  Each micro-service should be a separate process. You're welcome to implement your choice of queueing and/or communication for these micro-services.

For us, micro-services are:
  * Small
  * Single purpose
  * Use messages to communicate
  * Can each have many running instances; and
  * Are not guaranteed to remain alive (process death is expected).

Please build these micro-services that will:
  * Collector: read the input data (see resources)
  * Parser: parse and translate the data (see resources for output format)
  * Persister: store the data (your choice of persistent storage) and;
  * Reporter: correlate and display the data (list and group data like in *report-schema.json*)

### Minimum requirements:
  * Each micro-service should run as a separate process
  * Write a *README.md* file with any explanation and instructions for running this application

### Minimum functionality:
  * Collector application should read JSON payload from file and store it for the Parser application.  The *input.json* file contains both original invoice documents and responses to invoice documents.
  * Parser application should read from the data stored by the Collector application and store each item for the Persister application as a new, formatted individual entity using the defined schema (see *schema.json*).  Note that in this schema the *documentType* field should have a value of either `monospace`Invoice`monospace` or `monospace`Response`monospace` and the *originalDocumentNumber* and *status* fields will only be populated for response documents.
  * Persister application should store each datum that the Parser processed and save it into non-volatile storage
  * Reporter application returns the final data as a JSON payload.  Response documents are to be grouped with their originating invoice (an example record is provided in *report-schema.json*).  Correlation can be done by matching the *originalDocumentNumber* field on a response document to the *documentNumber* field on an invoice document.  Response documents should be ordered by their date, having the newest response listed first.

## ADDITIONAL PROJECTS:
### Please complete two of the following:
**Option 1:**

Add a unit tests for the main project to acheive 100% code coverage

**Option 2:**

How would you architect a continuous deployment of micro-services where different versions can co-exist without breaking the data integrity?

**Option 3:**

How would you architect auto-scalability of micro-services?

**Option 4:**

When 2 or more instances of same micro-service can co-exist in the same ecosystem, how would you architect the micro-service ecosystem so the data is only processed once?


## Resources
<TBD>
