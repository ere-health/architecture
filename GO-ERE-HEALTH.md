# https://go.ere.health

![](img/go-ere-health.png)

https://go.ere.health is ere.health as a Software-as-a-Service offering. The main benefit:

 * No software installation required

## How does this work?

We are assigning every tenant 3 ports that they have to connect via SSH Remote Port forwarding with the following services:

 1. Connector
 2. IdP
 3. Fachdienst

We are making sure that the connector can only be used by the specified tenant by securing it with Basic Authentification or SSL Certificates and these certificates are only stored in the local storage of their local browsers. The main system is not storing and data but just processing it and returning it to the different services.

## Step-by-step introduction

 1. Go to https://go.ere.health
 2. Enter the ip address of your connector
 3. Enter the given commands on your computer terminal
 4. Enter the connector context data: Mandant, Client System Id, Workplace Id
 5. Test set up
 5. Start creating E-Prescriptions
