<!-- INTRODUCTION -->

The main reason we are doing this is to see how people use the OrthoNow website. We do not just want to know what pages they look at. We want to know what they actually do on the website. For example we want to know when someone books a consultation or clicks the Call Now button. We also want to know when they open WhatsApp or download the patient guide. We are interested in what people do when they visit the clinic pages and when they read the blog articles on the OrthoNow website. All of this information will help the marketing team at OrthoNow see how well their campaigns are working and make the OrthoNow website better, at getting people to do what we want them to do.


<!-- GTM Event Schema -->

| Event Name                      | Trigger Type                  | Key Parameters                                   | Used For                                                                                                    |
| ------------------------------- | ----------------------------- | ------------------------------------------------ | ----------------------------------------------------------------------------------------------------------- |
| **booking_step_complete**       | Custom Event (dataLayer Push) | `step_number`, `clinic_location`, `specialty`    | Tracks user progress through the 3-step appointment booking funnel and helps identify where users drop off. |
| **consultation_form_submitted** | Form Submit                   | `patient_name`, `phone`, `clinic_location`       | Measures successful consultation requests and records completed leads.                                      |
| **call_now_click**              | Click Trigger                 | `page_name`, `clinic_location`, `phone_number`   | Tracks how many users prefer calling the clinic instead of submitting the form.                             |
| **whatsapp_chat_click**         | Click Trigger                 | `page_name`, `device_type`, `source`             | Measures user engagement with the WhatsApp chat option.                                                     |
| **patient_guide_download**      | Form Submit + File Download   | `guide_name`, `patient_name`, `phone`            | Tracks users who download the patient guide after submitting their details.                                 |
| **clinic_page_view**            | Page View                     | `clinic_name`, `city`, `specialty`               | Identifies which clinic pages receive the highest traffic and user interest.                                |
| **blog_scroll_90**              | Scroll Trigger (90%)          | `article_title`, `category`, `scroll_percentage` | Measures how many users read blog articles until the end, indicating content engagement.                    |


<!-- Booking Funnel Tracking -->

The booking form is really simple. It has three steps. I think it is an idea to track each of these steps on its own. This way I can see where people stop using the booking form. If I track each step of the booking form separately it will be easy to figure out where users leave the booking process of the booking form.

Step 1 – Clinic & Specialty Selected
{
  "event": "booking_step_complete",
  "step_number": 1,
  "step_name": "location_specialty_selected",
  "clinic_location": "Bengaluru",
  "specialty": "Orthopaedic"
}


Step 2 – Patient Details Entered
{
  "event": "booking_step_complete",
  "step_number": 2,
  "step_name": "patient_details_entered",
  "patient_name": "John Doe",
  "phone": "9876543210",
  "preferred_date": "2026-07-10"
}


Step 3 – Booking Confirmed
{
  "event": "booking_step_complete",
  "step_number": 3,
  "step_name": "booking_confirmed",
  "booking_id": "BK1001",
  "clinic_location": "Bengaluru",
  "specialty": "Orthopaedic"
}


<!-- Funnel Tracking Explanation -->

I will make a Funnel Exploration report in Google Analytics 4 using these three events. This report will tell me how many users finish each step of the booking process and where they stop. For example if a lot of users finish the step but do not go to the second step it means there might be a problem with the form or how the website works. This information will help make the booking process better and get more people to complete their bookings. The Funnel Exploration report is really helpful, for understanding the Funnel Tracking. It will show me where people are leaving the Funnel Tracking process. By looking at the Funnel Tracking report I can see what is going wrong with the Funnel Tracking and fix it.


<!-- Google Ads Conversion -->

I would bring the consultation_form_submitted event into Google Ads because it means someone asked for a consultation. This event is better than looking at page views or button clicks because it shows that a user is really interested. Google Ads can use this event to make campaigns better for people who're more likely to submit the Google Ads conversion form, which is the consultation form. This is what Google Ads Conversion is about so using the consultation_form_submitted event, for Google Ads Conversion makes sense.