# CiviCRM Module for Meetup.com integration with CiviEvent in Wordpress

Design Notes:

TODO:
* sql/auto_install.sql -> CREATE **civimeetup_link** to store CiviEvent ID, MeetupID, Meetup Host User ID?
* sql/auto_uninstall.sql -> DROP **civimeetup_link*
* templates/CRM/CiviMeetup -> Templates for insertion/configuration
* Add web Hook to add fields/buttons in Event_Edit, Event_Add, Event_Manage pages to include link to Meetup along with "Assign Meetup" "Push to Meetup".
* Function to modify CiviConfig to add Meetup API Key.