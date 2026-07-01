             TASK 3 - INTEGRATION DESIGN

<- Integration Architecture >

When someone submits the consultation form on the OrthoNow landing page their request goes to an API built with Node.js and Express.
I think it's better to connect with the HubSpot CRM API instead of using Zapier or Make. This way we have control, less delay and can easily customize things.

The backend checks the form data. First looks up the submitted phone number in HubSpot. Since HubSpot mainly finds duplicates using email I will specifically search for a contact with that phone number before making an one. If we find a matching phone number we update the existing contact; if not we create a contact. We also store the patients name, phone number, clinic, source, as "Google Ads. Consultation Landing Page" and lead status as "New Enquiry".

After HubSpot stores the contact the backend uses the Karix WhatsApp Business API to send a confirmation message to the patient. At the time we send the consultation_form_submitted conversion event to Google Ads so the campaign can focus on completed consultation requests.


<- Biggest Faliure Point -> 

The biggest problem with HubSpot is that it makes contacts. This happens because HubSpot does not remove duplicates by itself when it finds the phone number.
To stop this from happening the system behind the scenes should always look at HubSpot using the phone number before making a contact.
This way HubSpot will update the contact that's already there instead of making a new one and creating duplicate leads with the same phone number. HubSpot will have the information for each contact, with the same phone number.


<- WhatsApp SLA and Monitoring -> 

The WhatsApp confirmation message should be sent within two minutes of form submission. Sometimes there are delays. This can happen because of problems with the API or the network. If the service is down, for a little while.
To deal with this I would make sure the system tries again if it fails. I would also keep a record of what happens and watch how the API is doing. If a request does not work it will be written down in the application logs. We will also get a warning if the message takes longer than two minutes to get to the patient.

This way we can catch any problems away and the patients will still get their confirmations on time. WhatsApp confirmation messages are very important so we need to make sure they get to the patients quickly.