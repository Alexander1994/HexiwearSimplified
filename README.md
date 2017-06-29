# HexiwearSimplified
This is a "fork" of the Wolksense Hexiwear Android app. I've made some simplifications to help everyone with a base implementation.
## Changes in code
1. Login activity inserts "Demo" in the credentials. This disables all the Wolksense Cloud API calls.
2. Main Activity starts with the credentials already set and lists the devices
3. I've simplified the readings activity layout to have a single element that gets updated: HR variable. OnDataReady method is the only one that you should worry about. At least at first glance.
4. Readings activity also stores the HR data into firebase everytime it gets a new value. It does not stores historical data, it just overwrites the current value in Firebase. This is a good example on how to store data and always have the latest value possible.

## Suggestions
* The readings activity uses ControllLayout, I recommend changing to Constraint Layout.
* I could not remove Android Annotations because it would take a long time for me to release this code. Take a look at their [GitHub](https://github.com/androidannotations/androidannotations/wiki) to learn more. TL;DR You annotate a regular Java class "MyClass.java" and the processor will create a full android Java class "MyClass_.java". That is why you see intent calls and activity switches with ReadingsActivity_ insetad of ReadingsActivity
* If you have questions about Annotations and how to use/avoid them come talk to me after one of the labs.
* I've tested the code for 2 minutes, I am pretty sure it is not bug free.

## *WARNING*
The code *will not* compile once you clone it from git. As stated before it uses Firebase so you have to insert your own *google-services.json* file or get rid of the firebase methods and references on the app graddle. 
* The application name for the Firebase bucket is: *com.wolkabout.hexiwear* you can change it on the build.gradle of the app