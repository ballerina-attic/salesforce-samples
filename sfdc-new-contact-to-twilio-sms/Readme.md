Example to send a Twilio SMS for every new Salesforce Contact.

## Use case
Twilio is a cloud communications platform as a service (CPaaS) company. It allows software developers to programmatically make and receive phone calls, send and receive text messages, and perform other communication functions using its web service APIs. 

As most of the organizations maintains a well organized sales process, it is important to follow up with leads as soon as they are added in Salesforce. There maybe a specific person who wanted to be on alert of new Salesforce leads. Any time you create a new lead in Salesforce, an SMS message will automatically send to the specific person via Twilio. 

The following sample demonstrates a scenario in which a Twilio SMS message containing all the defined fields in lead SObject is sent to a given mobile number when a new lead is created in Salesforce.

## Prerequisites
* Pull the template from central  
  `bal new -t choreo/sfdc_new_contact_to_twilio_sms <newProjectName>`
* Twilio account
* Salesforce account

### Setting up Salesforce account
1. Create a Salesforce account and create a connected app by visiting [Salesforce](https://www.salesforce.com).
2. Salesforce username, password will be needed for initializing the listener.
3. Once you obtained all configurations, Replace relevant places in the `Config.toml` file with your data.
4. [Select Objects](https://developer.salesforce.com/docs/atlas.en-us.change_data_capture.meta/change_data_capture/cdc_select_objects.htm) for Change Notifications in the User Interface of Salesforce account.

### Setting up Twilio account
1. Create a [Twilio developer account](https://www.twilio.com/).
2. Obtain the Account SID and Auth Token from the project dashboard.
3. Obtain the phone number from the project dashboard and set as the value of the `fromNumber` variable in the `Config.toml`.
4. Give a mobile number where the SMS should be sent as the value of the `toNumber` variable in the `Config.toml`.
5. Once you obtained all configurations, Replace relevant places in the `Config.toml` file with your data.

## Configuration
Create a file called `Config.toml` at the root of the project.

## Config.toml
```
[<ORG_NAME>.sfdc_new_contact_to_twilio_sms]
fromNumber = "<TWILIO_FROM_MOBILE_NUMBER>"  
toNumber = "<TWILIO_TO_MOBILE_NUMBER>"  

[<ORG_NAME>.sfdc_new_contact_to_twilio_sms.salesforceListenerConfig]
sfdcUsername = "<SALESFORCE_USERNAME>"  
sfdcPassword = "<SALESFORCE_PASSWORD>" 

[<ORG_NAME>.sfdc_new_contact_to_twilio_sms.twilioClientConfig]
twilioAccountSid = "<TWILIO_ACCOUNT_SID>"  
twilioAuthToken = "<TWILIO_AUTH_TOKEN>"

```
Phone numbers must be provided in E.164 format: +<country code><number>, for example: +16175551212
## Testing
Run the Ballerina project created by the integration template by executing `bal run` from the root.

You can check the Twilio SMS for information related to the new Salesforce Contact.
