# Andy G "Create Leads" API Demo
(This is purely a 'This is what I use for my demos' repo - feel free to use what's here but there is no support available and this is NOT an official IBM demo)

Shortcut to [Build Instructions](Docs/READMe.md)
## Scenario overview
Tia is a mobile application developer. She needs to create a new mobile app for an upcoming conference that her company is hosting. Staff will use the mobile app to scan the QR codes on attendees' badges and the app will then create new lead for that attendee with their details in Salesforce.

### Tia's Background and Skills

Tia is a mobile app developer, not an integration developer.

(She could also be a website developer or any other API client...)

Tia is not a 'citizen developer' - she is a fully-fledged techie developer - she can write goLang or Javascript as well as anyone  - it's just that her skill set is in UI-driven mobile applications, not integration.

She needs to build and deploy an API as quickly and easily as possible that her mobile app can use. She has minimal knowledge of Salesforce and her knowledge of APIs is that of a consumer of them.

This is a 'I just want it done' requirement - Tia is a mobile App Developer - if she could get an integration specialist to build the API for her, she would - but she can't get a resource from Central IT, so she needs to do it herself.

### Tia's Requirements
1. An API in REST format that her app can call and which will create a new lead record in Salesforce. When the record is created it would be nice if a slack notification can be sent to Sales to let them know a new lead is available.
2. Security on the API so that she can expose it to the internet for her app to call directly without needing VPNs etc.
3. Consumers of her API must not need to have Salesforce or Slack credentials (or even be aware that the back-end to the app is Salesforce)
4. Self-service sign-up to the API so that she doesn't have to give out credentials to users. Also she doesn't want to have one shared set of credentials - if any of the credentials are compromised, she wants to be able to revoke just that user.
5. Rate limiting on the API so that her Salesforce account is not overloaded.
6. Production strength - it must be highly available and resilient - after all, it's supporting many mobile app users at her company's flagship event.

## Bill of Materials ("You will need...")
* Openshift Cluster - 4.12 or 4.14: A supported Even Numbered (EUS) version. Note that CP4I supports single-node Openshift so you don't need a 'full cluster' if you don't have one.
* Cloud Pak for Integration (CP4I)- 2023.4.1 or later (must have assemblies, declarative APIs and Canvas)
* CP4I Platform Navigator installed on CP4I
* App Connect Designer installed on CP4I
* App Connect Dashboard installed on CP4I
* API Connect Installed on CP4I: Need API Manager, API Gateway and API Portal - Analytics recommended but optional
* Automation Assets Installed on CP4I - this is not mandatory but makes the demo a lot easier with 'Import from Assets' meaning a lot less typing.
* A Salesforce 'Developer' account - note that this is NOT the same as a Salesforce trial account.
* A Slack instance that you have administrator access to - you will need to be able to generate a slack access token.
* Github or similar place to store your assets and artefacts
* An email server which supports SMTP so that APIC can send you emails. If you don't have one, try signing up to [mailtrap.io](https://mailtrap.io) - note this is not a recommendation from me or IBM to use mailtrap - it's just what I use for demos.
* Your favourite beverage to help you along!

## Demo Flow
1. Build and Test the API Flow in App Connect Designer
2. Export the API BAR file from designer to be deployed
3. Create a new Integration Assembly to deploy the API and its dependencies
4. Create an Integration runtime in the Assembly using the BAR file
5. Create a Declarative API Product to expose our API in API Connect
6. Create a Configuration for Salesforce so the Integration Runtime has the right credentials to connect to Salesforce
7. Deploy the Assembly to the Cluster
8. Review the API in the APIC Portal
9. Create an Application and sign up to the API and get some credentials
10. Test the API and see our created lead in Salesforce
11. Celebrate with your tasty beverage!

## Next Steps
Go to [Build Instructions](Docs/READMe.md) to get started.