# Folder Tree Report - simple setup
Using the below instructions you can setup the folder tree report as a standalone app running on your local machine. You'll need three things

1. Clone this repository to your local machine
2. Setup a local web server.
3. Generate a developer token and some data (for this you do need a Box account)

## Local web server
See this article on the options of running a local web server (I am on a Mac and use the built-in python web server)
https://developer.mozilla.org/en-US/docs/Learn/Common_questions/Tools_and_setup/set_up_a_local_testing_server

## A developer token

1. Get a free Developer account if you don't already have a Box account. https://support.box.com/hc/en-us/articles/4636662134803-Creating-Your-Developer-Account
2. Login and goto https://developer.box.com and click 'My apps' in the upper left hand corner.
3. This takes you to the developer console where you can create a new app. Create a custom app, OAuth 2.0 and give it a meaningful name
4. Once created you can copy the developer token from the Configuration page. This is valid for 60 minutes
5. If you don't already have data in your Box instance, import a small folder structure to make it have something to report on. Copy the ID of the top folder
6. Open your web browser of choice and navigate to localhost:8000/index.html?token=DEVELOPER_TOKEN&id=ID_OF_A_FOLDER_IN_YOUR_BOX_INSTANCE


