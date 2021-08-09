# Page Lifecycle Tester

This is a simple application to test when Page Lifecycle Events fire

## What's in this project?

The application currently tests the support for pagevisibility, pagehide, beforeunload and unload fire given different scenarios and device.
Information as to when an event triggers is captured by the [useBeacon Web API](https://developer.mozilla.org/en-US/docs/Web/API/Navigator/sendBeacon)

## HowTo

1. Set up a Pipedream Worflow to record events in a spreadsheet
2. Open the Github Page and append your Pipedream endpoint
3. Run your test scenario and evaluate the data

### Pipedream Setup
Pipedream operates as an endpoint to send the event data to for extracting and transforming before sending it to an enpoitnt of your choosing.
For this project we will set up a Pipedream Workflow to send the event data to Google Sheets.

* Create a [Request Bin](https://pipedream.com/requestbin) at pipedream.com and add a new Workflow with an HTTP API Trigger.
* Next hit the + button and add a Google Sheets Action. Select "Add Single Row". You will be prompted to establish an Oauth handshare between your Google Sheets account and Pipedream.
* Create a new Google Sheet at your docs.google.com account. We will use this to record the events
* In your Pipedream Workflow select your Google Sheets account and Google Sheet to funnel the events to
* In "Cells / Columns Values" you can pick which incoming data to pipedream should be forwarded to your Google Sheet rows. In order to use the visual interface you should exemplary data to Pipedream first: 
  * Open the Github Page at with your Pipedream endpoint (you find the enpoint at the top of your Pipedream workflow. It should look like something.m.pipedream.net) appended as a query string with key beaconUrl 
  * Any triggered events should be send to your Pipedream Workflow now where you can expect incoming events in real time
  * Inspect the incoming events to decide which information you would like to forward to Google Sheets and add them to the "Cells / Columns Values" row of your Google Sheets Action
  
You can test any scenarios that come to your mind to see what events are being triggered by the browser. Here is a list of my own testing:
![Page Lifecycle Matrix](https://cdn.glitch.com/ed81219d-af1f-4927-800e-624873f47bfd%2F4cf515f9-ef44-4ef1-9053-4f5bcb005461.image.png?v=1628513828699)