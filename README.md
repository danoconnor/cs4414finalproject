cs4414finalproject
==================

Our project was to modify the Android source code (specifically a popular mod called Cyanogenmod 10.2) in order to give the user greater control over the way applications access their personal data. Currently, in order to install and run an application, a user must accept all permissions that the app requests. Our solution will allow the user to blacklist certain applications, which will cause our system to feed the application false information when it attempts to access either a list of contacts or the user's current location. This solution enables the app to continue to function (and not crash due to some null pointer problem), while preventing it from getting your actual data. 

For each type of data (contacts and location), we had to take slightly different approaches. For contacts, we blocked access through the ContentProvider class, which is the standard path to access a user's contacts list. Location is generally accessed through the LocationManager class, so to block location data we modified that class to return a default location (coordinates 0, 0) whenever a blacklisted application asked LocationManager for the location. 

To allow the user to modify the blacklist, we modified the Settings application that is included with Cyanogenmod. Now when the user opens the application manager section of Settings, they will see a checkbox that will allow them to add each application individually to the blacklist. 

We successfully build Cyanogenmod 10.2 with our modifications (harder than you might think), and flashed the resulting ROM to a Motorola Droid Bionic. 

Note: due to the very large size of the Cyanogenmod source code, we only included the files that we modified in this repository. Each file has its location in the Cyanogenmod source documented as a comment at the top of the file. 
