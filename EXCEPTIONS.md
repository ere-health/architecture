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

## FaultExceptions

The gematik defines multiple FaultExceptions in https://fachportal.gematik.de/fachportal-import/files/gemSpec_Kon_V5.16.0.pdf

Here is a table from the different use cases and the possible exceptions:

Tabelle 218: TAB_KON_128 Fehlercodes TUC_KON_150 „Dokument QES signieren“ (Page: 344)

| Code | ErrorType | Severity | Text (de) | Text (en)* |
|------|-----------|----------|-----------|------------|
| 4060 | Technical | Error | Ressource belegt | Resource is in use  |
| 4110 | Technical | Error | ungültiges Dokumentformat (%Format%) Der Parameter Format enthält das übergebene Dokumentformat. | Unknown document format (%Format%). The paramter %Format% contains the request document format |
| 4111 | Technical | Error | ungültiger Signaturtyp oder Signaturvariante | Unknown signature type or signature variant |
| 4118 | Technical | Error | Stapelsignaturen werden nur für den HBA unterstützt. Mit HBA-Vorläuferkarten sind nur Einzelsignaturen möglich. | Batch signature are only supported for HBA. With pre-HBA cards it is only possible to do single signature. |
| 4126 | Security  | Error | Kartentyp nicht zulässig für Signatur | Card type not supported for signature |
| 4049 | Technical | Error | Abbruch durch den Benutzer | Cancellation by user |

Tabelle 65: TAB_KON_089 Fehlercodes TUC_KON_012 „PIN verifizieren“ (Page: 160)

| Code | ErrorType | Severity | Text (de) | Text (en)* |
|------|-----------|----------|-----------|------------|
| 4001 | Technical | Error | Interner Fehler | Internal error |
| 4043 | Technical | Warning | Timeout bei der PIN-Eingabe | Timeout during PIN entering |
| 4049 | Technical | Error | Abbruch durch den Benutzer | Cancellation by user |
| 4053 | Security | Error | Remote-PIN nicht möglich | Remote-PIN not possible |
| 4060 | Technical | Error | Ressource belegt | Ressource is in use |
| 4063 | Security | Error | PIN bereits gesperrt (BLOCKED) | PIN is already locked (BLOCKED) |
| 4065 | Technical | Warning | PIN ist transportgeschützt, Änderung erforderlich | PIN is transport procted, change required |
| 4072 | Technical | Error | Ungültige PIN-Referenz PinRef | Invalid PIN-Reference PinRef |
| 4092 | Technical | Error | Remote-PIN-KT benötigt aber für diesen Arbeitsplatz nicht definiert | Remote-PIN-KT required but not defined for this workplace |
| 4093 | Technical | Error | Karte wird in einer anderen Kartensitzung exklusiv verwendet | Card is used in another session exclusivly |
| 4094 | Technical | Error | Timeout beim Kartenzugriff aufgetreten | Timeout during accessing card. |

The english text is a translation by us it won't be send by the connector.

Examples for our response message can be found here:

 1. [Timeout during PIN entering](ERezeptWithDocuments-Exception-4043.json)
 2. [Abbruch durch den Benutzer](ERezeptWithDocuments-Exception-4049.json)
 3. [Card is used in another session exclusivly](ERezeptWithDocuments-Exception-4093.json)

Further please read the following document [ERezeptWithDocuments-Exception-4093.json](ERezeptWithDocuments-Exception-4093.json)
