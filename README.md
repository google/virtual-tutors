**DISCLAIMER:** This is not an official Google product.

Virtual Tutors App
================================================================================

The Virtual Tutors App is a simple, experimental web application to enable multiple tutors
to serve multiple students remotely using a customer service ticket 
model.  In operation, a student creates a help request, and each logged
in tutor sees the help request appear in a queue.  Any tutor can then respond to
a pending help request, which causes a video connection to be automagically established (using
WebRTC) between the student and the tutor.

The app also includes rudimentary admin features to enable provisioning students, teachers,
and classes.

This is still very much an experiment and a work in progress, and **not intended for use in production**.
Please feel free to provide comments or suggestions if you find issues.

Current Features
----------------
* Establish WebRTC connection between a student and a teacher using a Firebase real-time database for
  signaling
* Provision teachers and students in Firebase database
* Create classes in Firebase database
* Google Sign-in Authentication (via Firebase)

Installation
------------
To install, you need to do the following:
* Install npm, bower, and firebase-tools.  See
  [https://firebase.google.com/docs/cli/]
* Provision your own TURN/STUN server. COTURN is a good option and fairly easy to
  setup.  See [https://github.com/coturn/coturn/wiki/CoturnConfig]
* Edit public/src/vt-conference.html to point to your own TURN/STUN server.
* Setup a Firebase project with a realtime database.  See
  [https://firebase.google.com/docs/database/web/start]
* Edit public/src/vt-app.html to point to your Firebase database
* Pull the necessary dependencies - `bower install`
* Optional - copy the security rules from database.json into Firebase.  See
  [https://firebase.google.com/docs/database/security/]
  If you don't do this, the default rules will apply, which require users to
  be authenticated but provide no other restrictions.  The rules in database.json were
  compiled using firebase-bolt from the database.bolt file.  See
  [https://github.com/firebase/bolt]
* Run the application locally - `firebase serve` - or host it on Firebase `firebase
  deploy`

How It Works
------------

The underlying technologies for Virtual Tutors are:
* WebRTC
* Firebase realtime database
* Polymer

Limitations, Known Issues, and Caveats
--------------------------------------
* Currently this has only been tested with modern Chrome and Firefox browsers.  Other
  browsers may work too . . . or not
* When adding new users and classes, there is a known problem with the UI that requires reloading the page
* Currently only single peer-to-peer connections are supported
* Others

License
-------
The code is released under the Apache 2.0 license. See the LICENSE file for
more details.

This project is not an official Google project. It is not supported by Google
and Google specifically disclaims all warranties as to its quality,
merchantability, or fitness for a particular purpose.
