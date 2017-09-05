# CiviCRM Module for Meetup.com integration with CiviEvent in Wordpress

Design Notes:

TODO:
* sql/auto_install.sql -> CREATE **civimeetup_link** to store CiviEvent ID, MeetupID, Meetup Host User ID?
* sql/auto_uninstall.sql -> DROP **civimeetup_link*
* templates/CRM/CiviMeetup -> Templates for insertion/configuration
* Add web Hook to add fields/buttons in Event_Edit, Event_Add, Event_Manage pages to include link to Meetup along with "Assign Meetup" "Push to Meetup".
* Drop Down field with list of Meetups to associate? On Add/Edit? As long as they aren't in civimeetup_link?
* Function to modify CiviConfig to add Meetup API Key.

Functions to add:
* _civimeetup_get_meetup_id($event_id) - returns Meetup Event ID, Name, and URL. $null if no match found.
* _civimeetup_link_events($event_id, $meetup_id) - Creates or updates record in civimeetup_link.
* _civimeetup_get_meetup_events($start_date, $end_date) - returns list of Meetup Events that fall within the date range specified.
* _civimeetup_unlink_events($event_id, $meetup_id) - removes civimeetup_link record.

Process for New Event:
* User with Edit/Administer privileges for Events will click on Events -> New Event
* At bottom of form, there will be a select field and a "Create New Meetup" Button.
* If the event already exists in Meetup, the user can select it from the select field and click save.
* A new record is inserted into the civimeetup_link table containing: CiviEvent ID, Meetup Event ID, Meetup Event Title, Meetup Event Link.
* If there is no matching Meetup Event, clicking "Create New Meetup" will generate a new Event using the information provided in the form and refresh the select field with the new Meetup at the top (Select ordered by ID descending). This might be a datatable given the additional information needed for the form submit...

Process for Existing Event:
* User with Edit/Administer privileges for Events will click on Events -> Manage Events
* If the event listed has a linked Meetup, a "Linked Meetup" hypertext link will be generated in the first column with `<a id="$meetup_id" href="$meetup_url">Linked Meetup</a>`. If no link exists, the column will remain blank.
* The user will click Configure -> Info and Settings and use the same procedure as listed above for creating a New Event.
