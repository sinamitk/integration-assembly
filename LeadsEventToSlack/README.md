# Andy G "Leads Event to Slack" Demo
(This is purely a 'This is what I use for my demos' repo - feel free to use what's here but there is no support available and this is NOT an official IBM demo)

Shortcut to [Build Instructions](Docs/README.md)
## Scenario overview
This demo is very simple on its own. It's an event-driven flow. When a new lead is created in Salesforce, Tia wants a slack message to be created to let the team know that there is a new lead and that they should review it.

In the ['LeadsAPI' Demo](../LeadsAPI/README.md), Tia has created an API that lets her create leads in Salesforce and which then sends her a slack message to let her know when a new lead has been created.

The only problem with this is that it only sends a slack message if the lead is created via Tia's API - if it is created directly in Salesforce, no notification is sent.

To solve this, Tia creates an App Connect event-driven flow that detects new leads being created in Salesforce and sends a message in slack when it happens.

To show the value of this, create a new lead using Tia's API - a slack message is sent. Then create a new lead directly in Salesforce - a slack message is sent - it doesn't matter how the lead is created.


### Tia's Background and Skills

Tia is a mobile app developer, not an integration developer.

(She could also be a website developer or any other API client...)

Tia is not a 'citizen developer' - she is a fully-fledged techie developer - she can write goLang or Javascript as well as anyone  - it's just that her skill set is in UI-driven mobile applications, not integration.

She just needs to send a message to slack when a new lead is created - she doesn't know Salesforce and most importantly doesn't want to have to learn it.

This is a 'I just want it done' requirement - Tia is a mobile App Developer - if she could get an integration specialist to build the flow that detects new events in Salesforce, she would - but she can't get a resource from Central IT, so she needs to do it herself.

### Tia's Requirements
1. When a lead is created in Salesforce, minimal details of that lead (Firstname, lastname, email) must be notified to a slack channel.
2. It doesn't matter how that lead is created - either by her API or by entering details into Salesforce directly; it must notify in slack
3. Production strength - it must be highly available and resilient

## Bill of Materials ("You will need...")
* Openshift Cluster - 4.12 or 4.14: A supported Even Numbered (EUS) version. Note that CP4I supports single-node Openshift so you don't need a 'full cluster' if you don't have one.
* Cloud Pak for Integration (CP4I)- 2023.4.1 or later if you want to do this as a 'follow on' demo to the LeadsAPI demo as you will need assemblies and canvas. Using Canvas to deploy the flow is good anyway. As a stand-alone "App Connect running on CP4I", any version will work - you'll need to deploy the flow using the App Connect Dashboard - or you can just run it in designer.
* CP4I Platform Navigator installed on CP4I
* App Connect Designer installed on CP4I
* App Connect Dashboard installed on CP4I
* If you want to use this as the follow-on to 'LeadsAPI' then install API Connect.
* Automation Assets Installed on CP4I - this is not mandatory but makes the demo a lot easier with 'Import from Assets' meaning a lot less typing.
* A Salesforce 'Developer' account - note that this is NOT the same as a Salesforce trial account.
* A Slack instance that you have administrator access to - you will need to be able to generate a slack access token.
* Github or similar place to store your assets and artefacts
* If you are following on from LeadsAPI and using APIC, An email server which supports SMTP so that APIC can send you emails. If you don't have one, try signing up to [mailtrap.io](https://mailtrap.io) - note this is not a recommendation from me or IBM to use mailtrap - it's just what I use for demos.
* Your favourite beverage to help you along!

## Demo Flow
1. Build and Test the Event Flow in App Connect Designer
2. Export the Event Flow BAR file from designer to be deployed
3. Upload the BAR file to the App Connect BAR store - or to github - whichever is your preference.
3. If you are following on from the LeadsAPI demo:

3a. Edit the LeadsAPI Integration Assembly to add a new Inegration Runtime with the new Event Driven Flow BAR reference - this will re-use the credentials used in LeadsAPI by linking to them in the canvas.

4. If you want to just show Canvas/Integration Assemblies:

4a Create a Configuration for Salesforce and Slack so the Integration Runtime has the right credentials to connect to Salesforce and Slack

5. If you want to just show "App Connect on CP4I":

4a Create a Configuration for Salesforce and Slack so the Integration Runtime has the right credentials to connect to Salesforce and Slack

4b. Use the App Connect Dashboard to deploy the Event Driven flow and link it to the Credentials Object.


5. Create a lead in Salesforce by any method and see a slack message created
6. Celebrate with your tasty beverage!

## Next Steps
Go to [Build Instructions](Docs/README.md) to get started.