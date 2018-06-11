# gdpr

Note: These tools are under active development.  We're remove this message when they are ready for testing by others.

The [General Data Protection Regulation](https://ec.europa.eu/commission/priorities/justice-and-fundamental-rights/data-protection/2018-reform-eu-data-protection-rules_en) (“GDPR”) requires companies hosting personal data collected from users in the European Economic Union to follow rules on how to handle that data and provide users certain rights to that data.

Two important rights that GDPR provides to users are 

  * the right of access, and 
  * the right to erasure (aka “the right to be forgotten”). 

When a user joins a recorded meeting, any information they share -- which includes video, slides, desktop, chat, and emoji icons, responses to polls, and whiteboard annotations, and other content during a session will be captured in the recording.

As an administrator of a BigBlueButton server, this repository contains a tool -- `bbb-user` -- that you can run on a BigBlueButton server to create a report on what personal data is held in recordings and to remove a user's personal data from a recording.

## Installation

Clone out this repository on a BigBlueButton 2.0 (or later) server.  Before you run, you will first need to install the gem `terminal-table`.

~~~
 gem install terminal-table
~~~

move bbb-user to /bin folder

~~~
 mv bbb-user /bin
~~~

## Usage

The `bbb-user` command takes a parameter `userID`,  a flag and generate a report of content in that recording generated by the given user.

### Usage

~~~
bbb-user -u <user_id> [-r <recordings_dir_path>] -g|-D

Parameters

  -u userID taken from an events.xml file
  -r path to records directory (default: /var/bigbluebutton/recording/raw)
  -g get the personal information for a given userID
  -D delete the personal information for a user from recordings.

Dry run:

When specifying the '-D' option, you may also have bbb-user do a dry run for the deletion 

  -d Output results of deletion without performing the deletion action
  
~~~

### Example of retrieving users info:

~~~
bbb-user -u w_g3btthk9p3cz -g
~~~

### Example of deleting users info:

~~~
bbb-user -u w_g3btthk9p3cz -D 
~~~


### Example of dry run of users info:

~~~
bbb-user -u w_g3btthk9p3cz -D  -d 
~~~
