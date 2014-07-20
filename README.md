Android Tasker Profile for Huginn Location Agent
========================

[Huginn](https://github.com/cantino/huginn) has a User Location Agent that can be POSTed to with your location. There's an iOS app to do it, but not an Android one (as far as I am aware). Setting this up with [Tasker](http://tasker.dinglisch.net/) is super easy, and requires no extra configuration on your Huginn installation beyond the regular Location Agent setup.

I'll give two sets of instructions below: a simple one for experienced Tasker users, and an in depth one for beginners.

Setup for Experienced Tasker Users
===================================

Requirements:

* [Tasker](https://play.google.com/store/apps/details?id=net.dinglisch.android.taskerm&hl=en)
* [Secure Settings](https://play.google.com/store/apps/details?id=com.intangibleobject.securesettings.plugin&hl=en) (only needed if you want it to turn GPS on and off automatically as needed)
* [Root](http://www.androidcentral.com/root) - Try [TowelRoot](https://towelroot.com/) (only needed if you want it to turn GPS on and off automatically as needed)
* [BusyBox](https://play.google.com/store/apps/details?id=stericson.busybox&hl=en) (only needed if you want it to turn GPS on and off automatically as needed)

Depending on your preference, you can either import the `huginnlocations.xml` or `huginnlocations-togglegps.xml` or follow the exported setup instructions in `description.txt`. If going with the XML, make sure to make a few changes:

* Throw your User Location Agent URL on line 66 for `huginnlocations-togglegps.xml` or line 46 for `huginnlocations.xml` that was given to you when you setup the agent
* The default is to POST the location every 30 minutes. Change that on line 12 if you want a different time frame.

Import `huginnlocations-togglegps.xml` if you want GPS turned on only when needed, and off otherwise. Import `huginnlocations.xml` if you always have GPS on.

Beginner Setup
==============

You'll first need to buy (or try the 7 day free trial) of [Tasker](https://play.google.com/store/apps/details?id=net.dinglisch.android.taskerm&hl=en). (Tasker is awesome, and something I think Huginn users would love.)

We'll go through two setups -- one for those that already have their GPS always on, and one for those of us that want Tasker to turn on our GPS only when sending the POST to Huginn.

GPS Always On (easier setup, bad on battery)
---------------------

* Open up `huginnlocations.xml` and edit line 46 with your Huginn User Location Agent url.
* Transer `huginnlocations.xml` to your Android device.
* Open up Tasker. Long press on "Profiles" until "Import" shows up. Navigate to the xml file, and import it.

GPS Toggling (harder setup, nicer on battery)
-----------------------------

* You'll need to root your device in order to do this. Google for instructions on how to root your particular device or try [TowelRoot](https://towelroot.com/).
* After rooting, install [Secure Settings](https://play.google.com/store/apps/details?id=com.intangibleobject.securesettings.plugin&hl=en) and [BusyBox](https://play.google.com/store/apps/details?id=stericson.busybox&hl=en).
* Open up Secure Settings, go to "System+" and enable the System+ module.
* Open up `huginnlocations-togglegps.xml` and edit line 66 with your Huginn User Location Agent url.
* Open up Tasker. Long press on "Profiles" until "Import" shows up. Navigate to the xml file, and import it.

---

At this point you're pretty much good to go! If you want to change the frequency, just press "Every 30m" and enter your preferred time.


TODO
====

* Add pictures to the guide
* Add step by step direct Tasker instructions (for those that don't want to mess with the XMLs)
* Think about other ways to integrate Tasker w/Huginn
* Improve the instructions
* It might be fun to wrap some various Takser -> Huginn interactions into an app that people can install, thus mitigating a lot of the difficulty for Tasker beginners to get started.
* There's some fun stuff you could do, like put a conditional that tells Tasker not to report location based on certain circumstances. e.g., don't keep sending location reports if I've been in the same place for awhile, or don't send them when I'm connected to my home wi-fi.