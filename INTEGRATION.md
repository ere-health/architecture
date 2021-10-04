# Integration Trail

# Starting ere-ps-app

Here you will find a checklist how to start the application: https://github.com/ere-health/ere-ps-app/blob/main/ere-ps-app-installation-checklist.md

# Week 1: Websocket communication

Goal: Send and receive a WebSocket message e.g. RequestSettings

In this week the websocket communication with the ere.health system should be established. It should be 

# Week 2: Build E-Rezept Bundles

Goal: Create an E-Rezept bundle with PZN and Free text medication in XML 

The main business object is the E-Rezept. Technical it is a [FHIR](https://www.hl7.org/fhir/) bundle that typically contains 7 resources.

 1. Composition
 2. Medication
 3. MedicationRequest
 4. Patient
 5. Practitioner
 6. Organization
 7. Coverage 

The official data model is part of the following document:

 * https://update.kbv.de/ita-update/DigitaleMuster/ERP/KBV_ITA_VGEX_Technische_Anlage_ERP.pdf

This document is the basis for the examples shown here:

 * https://simplifier.net/erezept

The E-Rezept is based on [FHIR](https://www.hl7.org/fhir/).

https://fachportal.gematik.de/fachportal-import/files/gemSpec_DM_eRp_V1.1.0.pdf

# Week 3: FHIR Validation

Goal: Validate the created bundles against the HAPI FHIR validator

The KBV created multiple profiles so it is possible to validate against them.

The FHIR Validation profiles can be found here: https://update.kbv.de/ita-update/DigitaleMuster/ERP/KBV_FHIR_eRP_V1.0.1_zur_Validierung.zip

Every bundle is validated against the profiles.

# Week 4: E-Rezept Workflow

Goal: Get the whole E-Rezept workflow working with creating and deleting E-Prescriptions including configuring the telematik settings and receiving a patient print out

The fachdienst operated by Gematik and developed by IBM implements the E-Rezept workflow that is specified here:

https://simplifier.net/erezept-workflow

A step-by-step tutorial can be found here:
https://github.com/gematik/api-erp/blob/master/docs/erp_bereitstellen.adoc

The requirements for the patient print can be found here:

https://update.kbv.de/ita-update/DigitaleMuster/ERP/KBV_ITA_VGEX_Technische_Anlage_ERP.pdf

The telematik API services are here:

https://github.com/gematik/api-telematik