---
title: Automating Google Calendar from Gmail Content
date: 2023-11-08 12:09:31
tags: ["automation", "Google Apps Script", "Gmail", "Google Calendar", "productivity", "coding", "programming", "calendar events", "email processing", "scripting", "Gympass"]
---

As a software engineer based in Dublin, Ireland, I often find myself juggling a busy schedule. Managing my fitness classes, work meetings, and personal commitments can be quite a challenge. To streamline this process, I decided to embark on a project to automatically create Google Calendar events from Gympass confirmation emails. In this blog post, I'll walk you through the steps and code I used to accomplish this task.

{% asset_img "gmail-to-google-calendar.png" %}

## The Problem

Gympass, a popular fitness service, sends confirmation emails whenever I book a fitness class. These emails contain valuable information about the class, such as the date, time, location, and instructor. Manually adding these details to my Google Calendar was becoming a time-consuming task.

## The Solution

To automate this process, I created a Google Apps Script that runs in my Gmail account. This script scans my inbox for Gympass confirmation emails, extracts the relevant information, and creates corresponding Google Calendar events. Here's an overview of how it works:

1. **Create a Google Apps Script Project**:
   - Open your Gmail account in a web browser.
   - Click on the "Apps Script" icon in the top-right corner (it looks like a square with a pencil).
   - This will open the Google Apps Script editor.

2. **Write the Script**:
   - In the Google Apps Script editor, copy and paste the script code provided in this blog post.

3. **Save and Name the Project**:
   - Give your project a name by clicking on "Untitled Project" at the top left and entering a name.

4. **Authorization**:
   - The script will need authorization to access your Gmail and Google Calendar. Click on the run button (▶️) in the script editor.
   - Follow the prompts to grant the necessary permissions to the script.

5. **Trigger the Script**:
   - To automate the script's execution, you can set up triggers. Click on the clock icon ⏰ in the script editor.
   - Create a new trigger that specifies when and how often the script should run. You might want it to run periodically, such as every hour.

6. **Email Search**: The script starts by searching your inbox for emails from `no-reply@gympass.com`. This ensures that it only processes Gympass emails.

7. **Email Parsing**: For each Gympass email found, the script extracts the email's subject and plain text body.

8. **Cancellation Handling**: If the email subject indicates that you canceled a booking, the script performs a cancellation action (you can customize this based on your business logic).

9. **Data Extraction**: For non-cancellation emails, the script removes any unnecessary footer text and URLs from the email body.

10. **Event Details Extraction**: Using regular expressions, the script extracts the date, time, location, and event title from the cleaned email body.

11. **Month-to-Number Conversion**: It converts the month name to a numeric value for creating a `Date` object.

12. **Event Creation**: With all the details in hand, the script creates a new Google Calendar event. It includes the event title, start and end times, location, and a Google Maps link to the event's location.

13. **Duplicate Event Check**: Before creating an event, the script checks if an event with the same date, time, title, and location already exists in the calendar to avoid duplicates.

## Code Organization

To keep the code clean and maintainable, I divided it into several functions:

- `extractAndCreateCalendarEvent`: The main function that orchestrates the entire process.
- `extractEventDetails`: Extracts event details from the email body using regular expressions.
- `monthToNumber`: Converts month names to numeric values.
- `createCalendarEvent`: Creates a new Google Calendar event.
- `isEventExist`: Checks if an event with the same details already exists.
- `removeFooterAndUrls`: Removes unnecessary footer text and URLs from the email body.
- `cancelEvent`: Placeholder for handling event cancellations (customize based on your needs).
- `parseTime`: Parses time in HH:mm a format and returns it as milliseconds.

```js
// Main function to process emails and create calendar events
const extractAndCreateCalendarEvent = () => {
  const searchString = "from:no-reply@gympass.com";
  const threads = GmailApp.search(searchString);

  for (let i = 0; i < threads.length; i++) {
    const messages = threads[i].getMessages();
    for (let j = 0; j < messages.length; j++) {
      const message = messages[j];
      const subject = message.getSubject();
      const body = message.getPlainBody();

      if (subject.includes("You canceled your booking")) {
        cancelEvent(body);
      } else {
        const cleanedBody = removeFooterAndUrls(body);
        const eventDetails = extractEventDetails(cleanedBody);

        if (eventDetails) {
          createCalendarEvent(eventDetails, cleanedBody);
        }
      }
    }
  }
};

// Extract the event details from the email body
const extractEventDetails = (body) => {
  const dateRegex = /(\w+), ([A-Za-z]+) (\d+)th at (\d+:\d+ [APap][Mm]) \(GMT\)/;
  const locationRegex = /In-person • (.+)/;
  const titleRegex = /(.*?) will see you/;
  const timeRegex = /(\d+:\d+ [APap][Mm]) - (\d+:\d+ [APap][Mm]) \(GMT\)/;

  const dateMatch = body.match(dateRegex);
  const locationMatch = body.match(locationRegex);
  const titleMatch = body.match(titleRegex);
  const timeMatch = body.match(timeRegex);

  if (dateMatch && locationMatch && titleMatch && timeMatch) {
    const dayOfWeek = dateMatch[1];
    const month = dateMatch[2];
    const day = dateMatch[3];
    const eventTimeStart = timeMatch[1];
    const eventTimeEnd = timeMatch[2];
    const location = locationMatch[1];
    const eventTitle = titleMatch[1];

    return {
      dayOfWeek,
      month,
      day,
      eventTimeStart,
      eventTimeEnd,
      location,
      eventTitle,
    };
  }

  return null;
};

// Convert month name to a numeric value
const monthToNumber = (month) => {
  const monthMap = {
    "January": 0,
    "February": 1,
    "March": 2,
    "April": 3,
    "May": 4,
    "June": 5,
    "July": 6,
    "August": 7,
    "September": 8,
    "October": 9,
    "November": 10,
    "December": 11
  };
  return monthMap[month];
};

// Create a Google Calendar event
const createCalendarEvent = (eventDetails, cleanedContent) => {
  const {
    dayOfWeek,
    month,
    day,
    eventTimeStart,
    eventTimeEnd,
    location,
    eventTitle,
  } = eventDetails;

  const monthNumber = monthToNumber(month);

  const eventDate = new Date(new Date().getFullYear(), monthNumber, day, 0, 0, 0);
  const eventStartTime = new Date(new Date().getFullYear(), monthNumber, day, 0, 0, 0);
  eventStartTime.setMilliseconds(parseTime(eventTimeStart));

  const eventEndTime = new Date(new Date().getFullYear(), monthNumber, day, 0, 0, 0);
  eventEndTime.setMilliseconds(parseTime(eventTimeEnd));

  const gymName = eventTitle;
  const mapsUrl = 'https://www.google.com/maps/search/' + encodeURIComponent(`${gymName} ${location}`);
  const description = `Google Maps Location URL: ${mapsUrl}\n${cleanedContent}`;

  if (!isEventExist(eventDate, eventEndTime, eventTitle, location)) {
    const calendar = CalendarApp.getDefaultCalendar();
    calendar.createEvent(eventTitle, eventStartTime, eventEndTime, { location, description });
  }
};

// Check if an event already exists
const isEventExist = (startDate, endDate, title, location) => {
  const calendar = CalendarApp.getDefaultCalendar();
  const events = calendar.getEvents(startDate, endDate);
  for (let i = 0; i < events.length; i++) {
    if (events[i].getTitle() === title && events[i].getLocation() === location) {
      return true;
    }
  }
  return false;
};

// Remove footer text and URLs
const removeFooterAndUrls = (body) => {
  const footerRegex = /Help\n<.*?>[\s\S]*$/;
  const cleanedBody = body.replace(footerRegex, '');
  const urlRegex = /<[^>]*>/g;
  const cleanedContent = cleanedBody.replace(urlRegex, '');
  return cleanedContent;
};


// Cancel an event
const cancelEvent = (body) => {
  // Parse the content of the cancellation email and perform the cancellation action as needed
  // You can identify the event to cancel based on the information in the email content
  // The specific implementation of this depends on your business logic
};

// Helper function to parse time in HH:mm a format and return it as milliseconds
const parseTime = (timeString) => {
  const [time, amPm] = timeString.split(' ');
  const [hours, minutes] = time.split(':');
  let hoursInt = parseInt(hours, 10);
  const minutesInt = parseInt(minutes, 10);

  if (amPm.toLowerCase() === 'pm' && hoursInt !== 12) {
    hoursInt += 12;
  } else if (amPm.toLowerCase() === 'am' && hoursInt === 12) {
    hoursInt = 0;
  }

  return (hoursInt * 60 + minutesInt) * 60000; // Convert to milliseconds
};

```

## Conclusion

Automating the creation of Google Calendar events from Gympass emails has significantly reduced the time and effort required to manage fitness classes and appointments. With this script running in the background, you can focus on your workouts and let technology take care of the scheduling.

By following the steps outlined in this blog post, you can set up your own automated email-to-calendar integration and adapt it to your specific needs. Happy coding!

