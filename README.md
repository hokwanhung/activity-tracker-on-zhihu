# Activity-Tracker-On-Zhihu
This is a web scrapper dedicated to analyse activity data from zhihu.com, which then transfer into useful models and graphs for displaying purpose. It is meant to cause no harm to the website, if any inappropriate uses are detected, the repository would be archieved immediately.

The software would be designed as an exe to run on window starts, and perform automatically in background - as long as the host stays online.

## Use Case Analysis

Suppose that the Web Scraper has only one type of user (operator), and the following business process:

An operator may:
- **Retrieve** the target list from [Google Sheet](https://docs.google.com/spreadsheets/d/1lb8m-a9SYrr1ImEoVnNulC6iEFg9kNFWiX87mBgy-H8/edit#gid=0) to a `JSON` file.
- **Search** through the target list once every six hours to check its activity.
- **Output** a list of the target list's today pins (later).
- **Write** the newest activity log (a `JSON` file) to the [Google Sheet](https://docs.google.com/spreadsheets/d/1lb8m-a9SYrr1ImEoVnNulC6iEFg9kNFWiX87mBgy-H8/edit#gid=0).
- **Display** a warning dialog if any person from the target list is missing for over 5 days.

## Use Case Description

*Use Case Name: Retrieve the target List*  
Actor: Operator  
Prerequisite: When the system starts.  
Description:  
1. The system automatically retrieve the target list from the [Google Sheet](https://docs.google.com/spreadsheets/d/1lb8m-a9SYrr1ImEoVnNulC6iEFg9kNFWiX87mBgy-H8/edit#gid=0).
2. The URL and name is then saved in a `JSON` file called `source.json`.
3. The normal flow is then resumed.

*Use Case Name: Search through the target list*  
Actor: Operator  
Prerequisite: When the system starts `OR` the timer runs off.  
Description:   
1. The URL is retrieved from the `source.json`.
2. The bot goes through every single URL of the list, to retrieve the date of the latest activity, with the latest today's pin if possible.
3. The normal flow is then resumed.

*Use Case Name: Output a list of today's pins*  
Actor: Operator  
Description:  
1. The today pins from the target list is generated into a list.
2. The list is then displayed as one pop-up window.
3. The normal flow is then resumed.

*Use Case Name: Write the newest activity log*  
Actor: Operator  
Description:  
1. The retrieved date is written to the [Google Sheet](https://docs.google.com/spreadsheets/d/1lb8m-a9SYrr1ImEoVnNulC6iEFg9kNFWiX87mBgy-H8/edit#gid=0).
2. The normal flow is then resumed.

*Use Case Name: Display warning dialogs*  
Actor: Operator  
Description:   
1. The system automatically retrieve the calculated answer form the [Google Sheet](https://docs.google.com/spreadsheets/d/1lb8m-a9SYrr1ImEoVnNulC6iEFg9kNFWiX87mBgy-H8/edit#gid=0) again.
2. If the response is `negative`, the system will then display a warning dialog that the target has been disappeared for more than a number of days.
3. The system is then return to its `count-down` status.
