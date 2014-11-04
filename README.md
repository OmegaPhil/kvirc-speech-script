Speech Script allows you via a called speech synthesis command to listen to what people are saying on channels - similar to the old mIRC Agent functionality on Windows.

Last updated on 4.11.14 for v1.7.


Installation
============

v1.7+ requires KVIrc 4.3.1 r6393 or higher due to a KVIrc Script change - for all I know I'm the only user of this script, if you have an earlier version of KVIrc and want to use this script, please open an issue on Github (see 'Bugs And Feature Requests' later) and I will try to work something out.

To load the script into KVIrc (which then persists until you uninstall) and run its startup alias, in a KVIrc console window:

    /parse <path to script file, speechmark-delimited if the path contains spaces>
    /SpeechScript::Startup

Once the script is installed, SpeechScript::Startup is automatically called when KVIrc is started.


Dependencies
============

This script depends on a speech engine of your choice with a commmandline interface - see configuration later for how to set the command to run when speech is needed. Currently I use [espeak](http://espeak.sourceforge.net/).

If notification bubbles are enabled (notices displayed by the notification daemon when people speak), Python 2.6 or later (not Python 3) and the python-notify package are required (pynotify is imported).


Uninstallation
==============

In a KVIrc console window:

    /SpeechScript::uninstall::uninstall


General Configuration
=====================

The 'Scripts' menu is created on the main KVIrc menubar, which then hosts the Speech Script Script menu:

![Script menu](https://f92fac806bf10a96c0b8-8a0a46e5f1a5cc9854958bc3503f0f88.ssl.cf1.rackcdn.com/media_entries/7506/script-menu.png)

Clear queued messages: When Speech Script is used in a busy channel, you can end up with non-stop talking with no end in sight. While it doesn't kill the current spoken command, any further messages are discarded, until the next message comes in.

Change volume: Currently this has only been implemented for espeak - tell the speech command to output at an arbitrarily-chosen amplitude associated with Mute/Quiet/Normal/Loud/MAXIMUM. When muted, if you have chosen to display notification bubbles, these are still displayed. If you want volume control with something other than espeak, please post a feature request on the issue tracker (see later) - I will implement a more generic way of configuring volume control.

Ignore messages when KVIrc and the relevant channel window is in focus: If you are using the channel generating the speech, you probably don't want it blaring out of the speakers too - however you may leave KVIrc in focus to do something else other than computering, and still want the speech - so this is configurable.

Display messages in notification bubbles: When a message comes in, along with being spoken it is sent to your notification daemon. This is dependent on KVIrc being compiled with Python support and a working Python installation, see Dependencies.

Statuses to ignore messages during: You can ignore this - the functionality works with the unreleased Status Script (I will release it if the current scripts have a warm enough reception, as it is a bit custom).

Configure speech command launches the following dialog:

![Configure speech command dialog](https://f92fac806bf10a96c0b8-8a0a46e5f1a5cc9854958bc3503f0f88.ssl.cf1.rackcdn.com/media_entries/7523/configure-speech-command-dialog.png)

Do pay attention to the strong quoting warning for the command. If you can find a way to make KVIrc run extra script/cause the shell to execute something even when '%m' is properly quoted, please create a bug on the issue tracker (see later) as this will be a security hole.

As mentioned earlier, if you want to configure the volume with a command other than espeak, please make a feature request on the issue tracker - it won't work currently.


Channel Menu Integration
========================

To monitor a channel, right-click the channel window and go Speech Script -> Monitor < channel name >:

![Channel menu](https://f92fac806bf10a96c0b8-8a0a46e5f1a5cc9854958bc3503f0f88.ssl.cf1.rackcdn.com/media_entries/7524/channel-menu.png)

Ignore nicks below hop: Allows you to exclude messages from anyone in the channel with a rank of less than half-operator.

Channel included with message: Speech Script announces the channel the message comes from before the message is spoken.

Network included with message: Announces the network the message comes from.

Ignore messages during particular statuses: Works with Status Script functionality, you can ignore this as this script has not been released.

The rest are self-explanitory - note the next section describes ignoring/unignoring nicks via the nick menu.

Ignore nick dialog:

![Ignore nick dialog](https://f92fac806bf10a96c0b8-8a0a46e5f1a5cc9854958bc3503f0f88.ssl.cf1.rackcdn.com/media_entries/7525/ignore-nick-dialog.png)

Unignore nick dialog:

![Unignore nick dialog](https://f92fac806bf10a96c0b8-8a0a46e5f1a5cc9854958bc3503f0f88.ssl.cf1.rackcdn.com/media_entries/7526/unignore-nick-dialog.png)


Nick Menu Integration
=====================

Right-click the user you want to ignore/unignore in the nick menu:

![Nick menu](https://f92fac806bf10a96c0b8-8a0a46e5f1a5cc9854958bc3503f0f88.ssl.cf1.rackcdn.com/media_entries/7527/nick-menu.png)

Naturally the text indicates the current state of ignoring.


Commands
========

The following commands are available:

    /SpeechScript <command>

    <no command>
        Returns the on/off state of the script
        
    help, h
        Returns this usage information
        
    on
        Turns script on
        
    off
        Turns script off

    startup
        Load script up

    removeignoredstatus <status>
        Removes the desired status from the list of statuses that channel messages are ignored during - Status Script functionality
        
    addignoredstatus <status>
        Adds the desired status to the list of statuses that channel messages are ignored during - Status Script functionality

    addignoredstatusprompt <status>:
        Intended for internal script use to add an ignored status via dynamic GUI

    clearqueuedmessages
        Removes all messages from the queue waiting to be spoken.


Alias/Scripting Usage
=====================

The script is fully commented so should be fairly accessible for those wanting to see how to take its use further - for alias usage, see comments preceeding the alias, or run the alias without parameters for help/errors.


Development
===========

Try out my modification of the [geany](http://www.geany.org/) IDE, extending it to syntax highlight, parse KVIrc Script for aliases, events, variables, shortcut for loading scripts into KVIrc etc: [Github documentation](https://github.com/OmegaPhil/geany-kvircscript/wiki/README---KVIrc-Script-Integration).


Bugs And Feature Requests
=========================

Please create an issue on the [Github issue tracker](https://github.com/OmegaPhil/kvirc-speech-script/issues).


Contact Details
===============

OmegaPhil@startmail.com
