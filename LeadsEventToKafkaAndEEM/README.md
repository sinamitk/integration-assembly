# Andy G "Leads Event to Kafka and EEM" Demo
(This is purely a 'This is what I use for my demos' repo - feel free to use what's here but there is no support available and this is NOT an official IBM demo)

Shortcut to [Build Instructions](Docs/README.md)
## Scenario overview
Tia wants to send a slack message whenever a new lead is created in Salesforce - she did this in the ['Leads Event To Slack' Demo](../LeadsEventToSlack/README.md)

The problem is that now her friends have seen this - and want do their own things when a new lead is created. For example Lea wants to add the lead details to a google sheet(TODO - pick an easy target system) every time that a new lead is created.

The problem is that Lea doesn't have access to Salesforce - it took Tia lots of time, paperwork, cunning and coffee buying to obtain her Salesforce integration credentials - and she certainly isn't about to share them: If nothing else, it's against corporate policy.

So Tia decides to use Event Streams/Kafka and Event Endpoint Management (EEM) to solve this.

When a new event arrives in Salesforce, she will put a message on a Kafka topic.

She will publish this Kafka topic to Event Endpoint Management - from there, as long as Tia approves the request, anyone can get access to the lead data - without having to have Salesforce credentials.

As EEM provides self-service signup and credentials management, it means Tia doesn't spend all day creating credentials for her co-workers!

This demo can be run standalone, or as a follow on to ['Leads Event To Slack' Demo](../LeadsEventToSlack/README.md) (which in turn can follow on from [LeadsAPI](../LeadsAPI/README.md) to make a whole integration story)


### Tia's Background and Skills

Tia is a mobile app developer, not an integration developer.

(She could also be a website developer or any other API client...)

Tia is not a 'citizen developer' - she is a fully-fledged techie developer - she can write goLang or Javascript as well as anyone  - it's just that her skill set is in UI-driven mobile applications, not integration.

She just needs to send a message to slack when a new lead is created - she doesn't know Salesforce and most importantly doesn't want to have to learn it.

This is a 'I just want it done' requirement - Tia is a mobile App Developer - if she could get an integration specialist to build the flow that detects new events in Salesforce, she would - but she can't get a resource from Central IT, so she needs to do it herself.

### Lea's Background and Skills
Lea is a business analyst - she is comfortable with spreadsheets, macros and formulae but is not reall a 'developer'.

She just wants the data where she needs it so she can use it for her business objectives.

If she could wave a magic wand and just have the data magically arrive, she would. If she could get Tia to do it every time she would but Tia (and the integration department) are always busy and have their own jobs to do.

### Tia's Requirements
1. When a lead is created in Salesforce, minimal details of that lead (Firstname, lastname, email) must be notified to a slack channel.
2. It doesn't matter how that lead is created - either by her API or by entering details into Salesforce directly; it must notify in slack
3. When other people come asking her to 'borrow' her confidential Salesforce credentials, she cannot share them
4. When other people ask her to create things to deliver lead data to them, Tia does not ahve the time to do it - she must enable them to do it themselves - or at least do it for them very quickly.
5. Tia does not want to spend all day creating new credentials for co-workers - she wants that to be automated.
6. Production strength - it must all be highly available and resilient

## Bill of Materials ("You will need...")
* Openshift Cluster - 4.12 or 4.14: A supported Even Numbered (EUS) version. Note that CP4I supports single-node Openshift so you don't need a 'full cluster' if you don't have one.
* Cloud Pak for Integration (CP4I)- 2023.4.1 or later if you want to do this as a 'follow on' demo to the LeadsAPI demo as you will need assemblies and canvas. Using Canvas to deploy the flow is good anyway. As a stand-alone "App Connect running on CP4I", any version will work - you'll need to deploy the flow using the App Connect Dashboard - or you can just run it in designer.
* CP4I Platform Navigator installed on CP4I
* App Connect Designer installed on CP4I
* App Connect Dashboard installed on CP4I
* IBM Event Streams installed on CP4I
* IBM Event Endpoint Management installed on CP4I.
* If you want to use this as the follow-on to 'LeadsAPI' then install API Connect.
* Automation Assets Installed on CP4I - this is not mandatory but makes the demo a lot easier with 'Import from Assets' meaning a lot less typing.
* A Salesforce 'Developer' account - note that this is NOT the same as a Salesforce trial account.
* A Slack instance that you have administrator access to - you will need to be able to generate a slack access token.
* Github or similar place to store your assets and artefacts
* If you are following on from LeadsAPI and using APIC, An email server which supports SMTP so that APIC can send you emails. If you don't have one, try signing up to [mailtrap.io](https://mailtrap.io) - note this is not a recommendation from me or IBM to use mailtrap - it's just what I use for demos.
* Your favourite beverage to help you along - if you're using this as a follow on to the LeadsAPI and Leads Event to Slack demos, now's the time to get a refill!

## Demo Flow
1. Create a Leads topic in Event Streams
2. Publish the Leads topic to Event Endpoint Management.
3. Create a connection account to connect App Connect to Event Streams
4. Build and Test the Event Flow in App Connect Designer
5. Export the Event Flow BAR file from designer to be deployed
6. Upload the BAR file to the App Connect BAR store - or to github - whichever is your preference.
7. If you are following on directly from the LeadsAPI demo:

6a. Edit the LeadsAPI Integration Assembly to add a new Inegration Runtime with the new Event Driven Flow BAR reference - this will re-use the credentials used in LeadsAPI by linking to them in the canvas.

4. If you want to just show Canvas/Integration Assemblies:

4a Create a Configuration for Salesforce and Slack so the Integration Runtime has the right credentials to connect to Salesforce and Slack

5. If you want to just show "App Connect on CP4I":

4a Create a Configuration for Salesforce and Slack so the Integration Runtime has the right credentials to connect to Salesforce and Slack

4b. Use the App Connect Dashboard to deploy the Event Driven flow and link it to the Credentials Object.


5. Create a lead in Salesforce by any method and see a slack message created
6. Celebrate with your tasty beverage!

## Next Steps
Go to [Build Instructions](Docs/README.md) to get started.