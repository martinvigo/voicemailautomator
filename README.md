# voicemailautomator

voicemailautomator is a tool that serves as a Proof of Concept for the research I presented at DEF CON 26, "Compromising online accounts by cracking voicemail systems".

For details and demos please check: [https://www.martinvigo.com/voicemailcracker](https://www.martinvigo.com/voicemailcracker)

## Basic info

voicemailautomator supports two actions:
* "message" - retrieves and records the newest message in the voicemail system. It returns a URL with the recording.
* "greeting" - changes the greeting message to specific DTMF tones

It uses webhooks to obtain information about the ongoing calls and act accordingly. It starts a Webserver on localhost:8080 and uses localhost.me service to reach the machine running the script.

## Setup
You will need a funded [Twilio account](https://www.twilio.com/), setup [TwiML bins](https://www.twilio.com/blog/2017/11/twiml-bins-a-serverless-and-codeless-way-to-try-twilio.html) and configure [localtunnel.me](localtunnel.me) to accept Webhooks. Check the "Twilio setup" section in the script and add the missing information 

```
account_sid = "" # Obtain from Twilio
auth_token = "" # Obtain from Twilio
twimlPayloadChangeGreeting = "" # <?xml version="1.0" encoding="UTF-8"?><Response><Pause length="10"/><Hangup/></Response>
twimlPayloadChangeGetNewestMessage = "" # <?xml version="1.0" encoding="UTF-8"?><Response><Pause length="10"/><Hangup/></Response>
status_callback_url = "" # Obtain from localtunnel.me
```

## Usage
```
python voicemailcracker.py message --victimnumber 5555555555 --carrier tmobile --callerid 4444444444 --backdoornumber 3333333333 --pin 0000
```
```
python voicemailcracker.py greeting --victimnumber 5555555555 --carrier tmobile --callerid 4444444444 --backdoornumber 3333333333 --pin 0000 --payload 1234
```

## Demo videos
##### Bruteforcing a voicemail PIN with voicemailcracker
[![Bruteforcing a voicemail PIN with voicemailcracker](https://img.youtube.com/vi/Z9kO4VmN1FM/0.jpg)](https://www.youtube.com/watch?v=Z9kO4VmN1FM)
##### Compromising Signal with voicemailcracker
[![Compromising Signal with voicemailcracker](https://img.youtube.com/vi/5tlWIxSthow/0.jpg)](https://www.youtube.com/watch?v=5tlWIxSthow)
##### Compromising Paypal with voicemailcracker
[![Compromising Paypal with voicemailcracker](https://img.youtube.com/vi/itEVmcirta0/0.jpg)](https://www.youtube.com/watch?v=itEVmcirta0)

## Tool presentation at DEF CON 26
[![Tool presentation at DEF CON 26](https://img.youtube.com/vi/ZpZbTPYB3cU/0.jpg)](https://www.youtube.com/watch?v=ZpZbTPYB3cU)

## Authors

Martin Vigo - @martin_vigo - [martinvigo.com](https://www.martinvigo.com)
