# ALERT EDITOR

Overview

The alert management functions are located on the Alert Editor tab.  These include the ability to add, modify, and delete alerts.  An alert consists of a descriptive name, a threshold value, a time span, one or more recipient email addresses, and a set of conditions.  When a Premier Responder call satisfies all of the conditions, it represents a single occurrence.  For an alert to go active, the number of occurrences must exceed the specified threshold value within time period specified.  A notification is sent to each recipient address when this happens.

Adding Alerts

To add an alert, enter the alert information in the boxes located beneath the line of text that reads: If the occurrences of this event reaches this limit in this time period send email to this address.  Starting with the far left box, enter a descriptive name, then the threshold value, next the time period, and finally the recipient email addresses.

To enter conditions for an alert, select the Edit Criteria button.  This brings up the Alert Criteria tab.  An alert condition is a query against the Premier Responder cases database.  To build the query, first select a column on the left side of the window inside the frame labeled Data Columns.  Next, on the right side of the window, enter a value to look for in the box below the IS, FROM, and LIKE radio buttons.  The radio buttons determine if the query is looking for an exact match (the IS operator), a range of values (the FROM and TO operators), or an occurrence of a text value within the column (the LIKE operator).

Include the Emergency Category column in the query when the alert pertains to either a fire, law enforcement, or a medical call.  Selecting one of the emergency categories from the resulting drop down list on the right will add the general questions for the category as additional columns.  The additional columns allow the query to be made more specific.

If the alert is related to a specific complaint, then include the general question column that lists the complaints in the query.  This adds the vital points for the complaint as additional columns.

To see the search criteria previously entered, use the scroll bars inside the Data Columns text box.  When the query is completed, select the OK button to save the changes and close the Edit Alert Criteria window.  The alert conditions appear in the text box labeled Alert Criteria.  Next, select the Add Alert button to add it to the list on the Alert Monitor tab.

Updating Alerts

Updating an alert is similar to adding an alert in that the alert information and conditions are entered in the same manner.  To modify an existing alert, either select the alert from the list on the Alert Monitor tab or from the drop down list on the left side of the Alert Editor tab.  This loads the alert information to the Alert Editor tab.  Make the necessary changes to the alert information or conditions and then select the Update Alert button.

Deleting Alerts

To delete an existing alert, first select it from the list on the Alert Monitor tab or from the drop down list on the left side of the Alert Editor tab.  Next, on the Alert Editor tab, select the Delete Alert button.  The alert is deleted from the list on the Alert Monitor tab.

Alert Database

Alerts appearing on the Alert Monitor tab are stored in a Access database file located in the application folder.  To work from a different database select the File/Open menu item on the Email Alert tab.  This brings up and Open file dialog window.  Selecting an existing database from the list and then the Open button opens the specified database.
