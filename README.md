# AGDemos
Andy G demo artefacts for IBM Cloud Pak for Integration (CP4I)

These are my own artefacts, resources and notes that I use for my demos - there may be errors/bugs/omissions....

## List of Demos ##
### Create and Deploy a Leads API
Create an API to create new Sales leads in Salesforce and send a slack notification when a new lead arrives.
Uses Integration Designer, App Connect, API Connect, CP4I Automation Assets, Platform Navigator, Declarative APIs, Integration Canvas and Integration Assemblies.

Go to [AG DEMO Leads API](LeadsAPI/README.md) to get started.

### When a new lead is created in Salesforce, send a slack notification
When a new lead is created in Salesforce by any means (either by using the Salesforce UI or by using the API in 'Create and Deploy a Leads API' above), a notification is sent to slack.

This differs from the notification above as it works however the lead is created - not just when the API is used.

This demo can be run standalone or as a follow-on from the Leads API demo above - if it is a follow on, it is deployed as an addition to the same integration assembly.

Go to [AG DEMO Leads Event to Slack ](LeadsEventToSlack/README.md) to get started.

### When a new lead is created in Salesforce, put a message on an Event Streams/Kafka topic and publish it to Event Endpoint Management (EEM)
When a new lead is created in Salesforce by any means (either by using the Salesforce UI or by using the API in 'Create and Deploy a Leads API' above), a notification is sent to slack.

This differs from the notification above as it works however the lead is created - not just when the API is used.

This demo can be run standalone or as a follow-on from the "Leads API" or the "Leads Event to Slack" demos above - if it is a follow on to 'Leads API', it is deployed as part of the same integration assembly. If it is a follow on to "Leads Event to Slack" then it replaces that flow.

Go to [AG DEMO Leads Event to Kafka and EEM ](LeadsEventToKafkaAndEEM/README.md) to get started.

## Disclaimer: ##

These are purely 'as is' and are my artefacts that I use for demos - if you find them useful, then that's great....if you want to use these as a basis to build your own demos, that's great too!

There is no support for these either from myself or IBM and these are in no way 'Official IBM' demos or artefacts.

All trademarks are acknowledged.

Any non-IBM systems or applications used in these demos are purely to show IBM software interacting with third party applications. This does not represent an endorsement or recommendation of these systems - they are ones that (a) provide data and context for demonstrating CP4I and (b) provide  free developer instances for us to demo with.