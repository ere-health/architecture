# Exceptions

The message type SignAndUploadBundles can generate the following exceptions:

Exceptions sends as message through the Websocket:

| Exception  | Generated in | Documentation |
| ---------- | ------------ | ------------- |
| NullPointerException | Everywhere | Happens if a null reference is access |
| JsonException | Websocket.java | if a JSON object cannot be created due to i/o error (IOException would be cause of JsonException) |
| JsonParsingException | Websocket.java | if a JSON object cannot be created due to incorrect representation |
| IllegalStateException | Websocket.java | if read, readObject, readArray, readValue or close method is already called |
| IllegalArgumentException | DocumentService.java | Thrown during intialization of service, when FOP factory has illegal arguments |
| ConfigurationException | DocumentService.java | Thrown during intialization of service, when FOP factory has an invalid configuration |
| ArrayIndexOutOfBoundsException | DocumentService.java | Thrown during intialization of service, when it is tried to access an array that is shorter than the index |
| IOException |  DocumentService.java | Thrown when files can't be read |
| URISyntaxExceptionConfigurationException |  DocumentService.java | Thrown when certain URIs can't be parsed e.g. the onces for the base directory |
| DirectoryIteratorException | DocumentService.java | Thrown during intialization of service, when the fonts from the JARs can't be extracted |
| FOPException |  DocumentService.java | Thrown during intialization of service, when in general the factory can't be build |
| TransformerException | DocumentService.java | Thrown when the XSLT transformation did not work |

Exceptions added to the message ERezeptWithDocuments:

| Exception | Generated in | Documentation |
| ---------- | ------------ | ------------- |
| WebApplicationException | ERezeptWorkflowService.java | Thrown when creating or updating the task (eprescription) on the domain services returns a response code unequals to a success code e.g. 200 this happens e.g. when the id is already taken, the bundle does not validate or signature is invalid |
| ERezeptWorkflowException | ERezeptWorkflowService.java | Is thrown for general errors like task is null after creating it |
| ERezeptWorkflowException - ConnectorCardsException | ConnectorCardsService.java | Is thrown when something goes wrong with the card selection or the PIN entering e.g. no active SMC or eHBA found | 
| ERezeptWorkflowException - FaultMessage | ERezeptWorkflowService.java | Is thrown when something with the signing goes wrong e.g. job number was already used or there is already an elevated security session on the card |

Some example fault messages are:

 1. Timeout bei der PIN-Eingabe
 2. Der Komfortsignatur-Zähler hat den Wert SAK_COMFORT_SIGNATURE_MAX erreicht;HBA-78
 3. Zugriffsbedingungen nicht erfüllt

Full list of error cases can be found here:
 * https://fachportal.gematik.de/fachportal-import/files/gemSpec_Kon_V5.14.0.pdf