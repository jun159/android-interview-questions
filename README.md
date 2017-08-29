<p align="center">
<img alt="AndroidInterviewQuestions" src="https://raw.githubusercontent.com/MindorksOpenSource/android-interview-questions/master/assets/android_interview_questions.png">
</p>

## Contents
 * [Data Structures And Algorithms](#data-structures-and-algorithms)
 * [Core Java](#core-java)
 * [Core Android](#core-android)
 * [Architecture](#architecture)
 * [Design Problem](#design-problem)
 * [Tools And Technologies](#tools-and-technologies)
 * [Android Test Driven Development](#android-test-driven-development)
 * [Others](#others)


## Data Structures

### Array
* Group of elements of the same data types
* Each element is data
* Stored continuously in memory

#### 1D array A[10] 
* 1 array with 10 elements

#### 2D array A[10][5]
* 1 array with cells pointing to 10 5-element arrays  

  | Algorithm | Average | Worst Case |
  |:---------:|:-------:|:----------:|
  | Space     | Θ(n)    | O(n)       |    
  | Search    | Θ(n)    | O(n)       |
  | Insert    | Θ(n)    | O(n)       |
  | Delete    | Θ(n)    | O(n)       |

### LinkedList
* Group of nodes of the same data types
* Head: First node
* Tail: Last node

#### LinkedList
* Each node has data and pointer that points to the next node
* Tail: Not pointing to anything `null`

#### Circular LinkedList
* Each node has data and pointer that points to the next node
* Tail: Points to the Head

#### Doubly LinkedList
* Each node has data and two pointers that points to the previous and next node
* Tail: Previous node pointing to previous node; Next node not pointing to anything `null`

#### Circular Doubly LinkedList
* Each node has data and two pointers that points to the previous and next node
* Tail: Previous node pointing to previous node; Next node points to Head

  | Algorithm | Average | Worst Case |
  |:---------:|:-------:|:----------:|
  | Space     | Θ(n)    | O(n)       |
  | Search    | Θ(n)    | O(n)       |
  | Insert    | Θ(1)    | O(1)       |
  | Delete    | Θ(1)    | O(1)       |

### Stack
* Last-in-First-out (LIFO)
* Implemented using LinkedList
* Push: Add item on top of stack
* Pop: Remove item from top of stack

     <table>
            <tr>
                <th>Algorithm</th>
                <th>Average</th>
                <th>Worst Case</th>
                <th>Image representation</th>
            </tr>
            <tr>
                <td>Space</td>
                <td>Θ(n)</td>
                <td>O(n)</td>
                <td rowspan="5">
                    <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/2/29/Data_stack.svg/250px-Data_stack.svg.png"/>
                </td>
            </tr>
            <tr>
                <td>Search</td>
                <td>Θ(n)</td>
                <td>O(n)</td>
            </tr>
            <tr>
                <td>Insert (Push)</td>
                <td>Θ(1)</td>
                <td>O(1)</td>
            </tr>
            <tr>
                <td>Delete (Pop)</td>
                <td>Θ(1)</td>
                <td>O(1)</td>
            </tr>
            <tr>
              <td>Top</td>
              <td>Θ(1)</td>
              <td>O(1)</td>
            </tr>
        </table>
        
### Queue

### PriorityQueue

### Hash Table

### Dynamic Programming

### String Manipulation

### Binary Tree 

### Binary Search Tree


## Sorting Algorithms 
* Efficiency of algorithms measured in [Big O](http://bigocheatsheet.com/)
* Good algorithms perform important actions in O(n log n), O(log n) or even O(1) time
* Time complexity: Time taken to complete algorithm
* Space complexity: Space taken to complete algorithm (i.e. do we need extra memory space other than current space to do sorting?)

  | Algorithm | Data Structure  | Time Complexity | | |
  | :------------: | :---------------: | :-----: | :-----: | :-----: |
  | | | Best | Average | Worst
  | Quicksort | Array | O(n log(n)) | O(n log(n)) | O(n^2)
  | Mergesort |Array | O(n log(n)) | O(n log(n))	 | O(n log(n))
  | Heapsort | Array | O(n log(n))	 | O(n log(n))	 | O(n log(n))
  | Bubble Sort | Array |	O(n)	 | O(n^2) | O(n^2)
  | Insertion Sort | Array | O(n) | O(n^2) | O(n^2)
  | Select Sort | Array | O(n^2) | O(n^2) | O(n^2)
  | Bucket Sort | Array |	O(n+k) |	O(n+k) | O(n^2)
  | Radix Sort | Array | O(nk) | O(nk) | O(nk)

### Bubble Sort
* Compares neighbouring elements and swap with each other if a > b
* Advantages: Simple and low space complexity - only two elements are compared at once and there is no need to allocate more memory
* Disadvantages: Inefficient

     <table>
                <tr>
                    <th colspan="3" align="center">Time Complexity</th>
                    <th align="center">Space Complexity</th>
                </tr>
                <tr>
                    <th align="center">Best</th>
                    <th align="center">Avegage</th>
                    <th align="center">Worst</th>
                    <th align="center">Worst</th>
                </tr>
                <tr>
                    <td align="center">Ω(n)</td>
                    <td align="center">Θ(n^2)</td>
                    <td align="center">O(n^2)</td>
                    <td align="center">O(1)</td>
                </tr>
            </table>
       
### Selection Sort

### Insertion Sort

### Merge Sort

### Quick Sort

### Hash Table / Hash Map


## Pathfinding Algorithms
        
### Dijkstra Algorithm

### Bellmanford Algorithm

### Breadth First Search

### Depth First Search

## Greedy Algorithm

### Core Java

### Core Android

#### Explain Activity and Fragment lifecycle
1. Before starting an activity, it is not in RAM
2. When an activity is called, it will call three methods accordingly and automatically:
  a. onCreate() 
  b. onStart() 
  c. onResume() 
3. Let's say we press home button, so current app will be minimized. (Note that current app is not closed!)
  a. onPause() - Pause activity first
  b. onStop() - After pausing, it will stop the activity
4. Let's say we want to go back to our app
  a. onRestart() 
  b. onStart() 
  c. onResume()
5. Let's say we want to go back to previous activity (close current app)
  a. onPause() - Pause activity first
  b. onStop() - After pausing, it will stop the activity
  c. onDestroy() - Only when activity is stopped, destroy the activity
6. When app is killed, it needs to create the activity again (Same as step 2)
  a. onCreate() 
  b. onStart() 
  c. onResume()  

<p align="center"><img src="https://github.com/jun159/android-interview-questions/blob/master/assets/activity_lifecycle.png" height ="250"></p>

#### What is the structure of an Android Application?

#### Define all Android application components
1. Activities
   *  Represents a single screen with a user interface 
   * Handle the user interaction on phone screen
2. Services
   * Runs in the background to perform long-running operations 
   * For example, fetch data over the network without blocking user interaction with an activity
3. Broadcast Receivers
   * They handle communication between Android OS and applications
   * Respond to broadcast messages from other applications or from the system
   * For example, applications can also initiate broadcasts to let other applications know that some data has been downloaded to the device and is available for them to use
   * Intercept this communication and will initiate appropriate action
4. Content Providers
   * Handle data and database management issues
   * Supplies data from one application to others on request 
   * Data may be stored in the file system, the database or somewhere else entirely

#### Service vs IntentService
1. Service
   * Can be used in tasks with no UI, but shouldn't be too long
   * If you need to perform long tasks, you must use threads within Service.
2. IntentService
   * Can be used in long tasks usually with no communication to Main Thread
   * If communication is required, can use Main Thread handler or broadcast intents
   * Another case of use is when callbacks are needed (Intent triggered tasks)

#### How to persist data in an Android app?
1. SharedPreferences
   * Store private primitive data in key-value pairs
2. Internal Storage
   * Store private data on the device memory
3. External Storage
   * Store public data on the shared external storage
4. SQLite
   * Store structured data in a private database
5. Network Connection
   * Store data on the web with your own network server

#### How would you perform a long-running operation in an application?
* Background
   * Every Java program by default has main thread. Whenever there is error, this thread will throw exception and stop executing
   * Android applications has UI thread that is in charge of any UI related works (e.g. scrolling through list / clicking on button)
1. AsyncTask
   * When application requests for data, UI thread is busy retrieving data from server. This causes entire app to be unresponsive since UI thread is busy doing other things.
   * Instead, we create another thread to request for data instead of UI thread so that our UI is still responsive
2. Handler
   * Do background computation
   * Not concerned with UI
3. Thread
   * Main core of multitasking
   * Parent of both handler and asynctask 
   
#### What is `Fragment`?

#### How would you communicate between two Fragments?

#### Explain Android notification system?

#### How can two distinct Android apps interact?

#### Why is it recommended to use only the default constructor to create a fragment? [StackOverflow](https://stackoverflow.com/a/16042750/2809326)

#### Why Bundle class is used for data passing and why cannot we use simple Map data structure

#### What is `Dialog` in Android?

#### What is `View` in Android?

#### Can you create custom views? How?

#### What are ViewGroups and how they are different from the Views?

#### What is the difference between a fragment and an activity? Explain the relationship between the two.

#### What is the difference between Serializable and Parcelable? Which is the best approach in Android?

#### What are "launch modes"? [Mindorks](https://blog.mindorks.com/android-activity-launchmode-explained-cbc6cf996802)

#### What are Intents? [StackOverflow](https://stackoverflow.com/questions/6578051/what-is-an-intent-in-android)

#### What is an Implicit Intent?

#### What is an Explicit Intent?

#### What is an `AsyncTask`?

#### What is a `BroadcastReceiver`? [StackOverflow](https://stackoverflow.com/questions/5296987/what-is-broadcastreceiver-and-when-we-use-it)

#### What is a `LocalBroadcastManager`? [Developer Android](https://developer.android.com/reference/android/support/v4/content/LocalBroadcastManager.html)

#### What is a `JobScheduler`? [Vogella](http://www.vogella.com/tutorials/AndroidTaskScheduling/article.html)

#### What is DDMS and what can you do with it?

#### What is the support library? Why was it introduced?[MartianCraft](http://martiancraft.com/blog/2015/06/android-support-library/)

#### What is a `ContentProvider` and what is it typically used for?

#### What is Android Data Binding? [Developer Android](https://developer.android.com/topic/libraries/data-binding/index.html)

#### What are Android Architecture Components? [Developer Android](https://developer.android.com/topic/libraries/architecture/index.html)

#### What is ADB?

#### What is ANR? How can the ANR be prevented?

#### What is `AndroidManifest.xml`?

#### Describe how broadcasts and intents work to be able to pass messages around your app?

#### How do you handle `Bitmaps` in Android as it takes too much memory?

#### What are different ways to store data in your Android app?

#### What is the Dalvik Virtual Machine?

#### What is the relationship between the life cycle of an AsyncTask and an Activity? What problems can this result in? How can these problems be avoided?

#### What is the function of an intent filter?

#### What is a Sticky Intent? [AndroidInterview](http://www.androidinterview.com/what-is-a-sticky-intent/)

#### What is AIDL? Enumerate the steps in creating a bounded service through AIDL.

#### What are the different protection levels in permission?

#### How would you preserve Activity state during a screen rotation? [StackOverflow](https://stackoverflow.com/questions/3915952/how-to-save-state-during-orientation-change-in-android-if-the-state-is-made-of-m)

#### Relative Layout vs Linear Layout.

#### How to implement XML namespaces?

#### Difference between `View.GONE` and `View.INVISIBLE`?

#### What is the difference between a regular bitmap and a nine-patch image?

#### Tell about the bitmap pool. [Mindorks](https://blog.mindorks.com/how-to-use-bitmap-pool-in-android-56c71a55533c)

#### How to avoid memory leaks in Android?

#### What are widgets on Home-Screen in Android?

#### What is AAPT?

#### How do you find memory leaks in Android applications?

#### How do you troubleshoot a crashing application?

#### Why should you avoid to run non-ui code on the main thread?

#### How did you support different types of resolutions?

#### What is Doze? What about App Standby?

#### What can you use for background processing in Android?

#### What is ORM? How does it work?

#### What is a `Loader`?

#### What is the NDK and why is it useful?

#### What is the StrictMode? [Mindorks](https://blog.mindorks.com/use-strictmode-to-find-things-you-did-by-accident-in-android-development-4cf0e7c8d997)

#### What is Lint? What is it used for?

#### What is a `SurfaceView`?

#### What is the difference between `ListView` and `RecyclerView`?

#### What is the ViewHolder pattern? Why should we use it?

#### What is a PendingIntent?

#### Can you manually call the Garbage collector?

#### What is the best way to update the screen periodically?

#### What are the different types of Broadcasts?

#### Have you developed widgets? Describe. [Mindorks](https://blog.mindorks.com/android-widgets-ad3d166458d3)

#### What is `Context`? How is it used? [Medium](https://medium.com/p/understanding-context-in-android-application-330913e32514)

#### Do you know what is the view tree? How can you optimize its depth?

#### What is the `onTrimMemory` method?

#### Is it possible to run an Android app in multiple processes? How?

#### How does the OutOfMemory happens?

#### What is a `spannable`?

#### What is `overdraw`? [Developer Android](https://developer.android.com/topic/performance/rendering/overdraw.html)

#### What is renderscript? [Mindorks](https://blog.mindorks.com/comparing-android-ndk-and-renderscript-1a718c01f6fe)

#### What are the differences between Dalvik and ART?

#### FlatBuffers vs JSON. [Mindorks](https://blog.mindorks.com/why-consider-flatbuffer-over-json-2e4aa8d4ed07)

#### What are Annotations? [Mindorks](https://blog.mindorks.com/creating-custom-annotations-in-android-a855c5b43ed9), [Link](https://blog.mindorks.com/improve-your-android-coding-through-annotations-26b3273c137a)

#### Tell about Constraint Layout [Mindorks](https://blog.mindorks.com/using-constraint-layout-in-android-531e68019cd)

#### `HashMap`, `ArrayMap` and `SparseArray` [Mindorks](https://blog.mindorks.com/android-app-optimization-using-arraymap-and-sparsearray-f2b4e2e3dc47)

#### Explain Looper, Handler and HandlerThread. [Mindorks](https://blog.mindorks.com/android-core-looper-handler-and-handlerthread-bd54d69fe91a)

#### How to reduce battery usage in an android application? [Mindorks](https://blog.mindorks.com/battery-optimization-for-android-apps-f4ef6170ff70)

#### What is `SnapHelper`? [Mindorks](https://blog.mindorks.com/using-snaphelper-in-recyclerview-fc616b6833e8)

#### How to handle multi-touch in android [GitHub](https://arjun-sna.github.io/android/2016/07/20/multi-touch-android/)


### Architecture

* Describe the architecture of your last app.
* Describe MVP. [Mindorks](https://blog.mindorks.com/essential-guide-for-designing-your-android-app-architecture-mvp-part-1-74efaf1cda40)
* What is presenter?
* What is model?
* Describe MVC.
* What is controller?
* Describe MVVM. [GitHub](https://github.com/MindorksOpenSource/android-mvvm-architecture)
* Tell something about clean code [Mindorks](https://blog.mindorks.com/every-programmer-should-read-this-book-6755dedec78d)


### Design Problem

* Design Uber App.
* Design Facebook App.
* Design Facebook Near-By Friends App.
* Design WhatsApp.
* Design SnapChat.
* Design problems based on location based app.


### Tools And Technologies

* Git. [GitHub](https://github.com/git-tips/tips)
* RxJava. [Mindorks](https://blog.mindorks.com/a-complete-guide-to-learn-rxjava-b55c0cea3631)
* Dagger 2. [Medium](https://medium.com/p/a-complete-guide-to-learn-dagger-2-b4c7a570d99c)
* Android Development Useful Tools. [Mindorks](https://blog.mindorks.com/android-development-useful-tools-fd73283e82e3)
* Firebase. [Firebase.google.com](https://firebase.google.com/)


### Android Test Driven Development

* What is Espresso? [Developer Android](https://developer.android.com/training/testing/ui-testing/espresso-testing.html)
* What is Robolectric? [Robolectric](http://robolectric.org/)
* What is UI-Automator? [Developer Android](https://developer.android.com/training/testing/ui-testing/uiautomator-testing.html)
* Explain unit test.
* Explain instrumented test.
* Have you done unit testing or automatic testing?
* Why Mockito is used? [Official site](http://site.mockito.org/)
* Describe JUnit test.


### Others

#### REST APIs
* Background:
  * Web services: Accessing cloud/server that gives you data
  * Request: App --Request for data--> Server
    * Post - Create
    * Get - Read
    * Put - Update
    * Delete - Delete
  * Response: Server --Respond by giving data in XML/JSON--> App
    * Why XML/JSON format? Data should follow particular structure
  * API: Connect App and Server
* Convert object into JSON/XML and send to client

#### SOAP

#### Retrofit

#### ButterKnife

#### About Build System - gradle, ant, buck

#### Describe SQLite

#### Describe database

#### Reverse Engineering an APK

#### What is proguard used for?

#### What is obfuscation? What is it used for? What about minification?

#### How do you build your apps for release?

#### How do you control the application version update to specific number of users?

#### Can we identify users who have uninstalled our application?

#### APK Size Reduction. [Mindorks](https://blog.mindorks.com/how-to-reduce-apk-size-in-android-2f3713d2d662)

#### Android Development Best Practices. [Mindorks](https://blog.mindorks.com/android-development-best-practices-83c94b027fd3)

#### Android Code Style And Guidelines. [Mindorks](https://blog.mindorks.com/android-code-style-and-guidelines-d5f80453d5c7)

#### Have you tried Kotlin? [Medium](https://medium.com/p/why-you-must-try-kotlin-for-android-development-e14d00c8084b)

#### What are the metrics that you should measure continuously while android application development? [Mindorks]
(https://blog.mindorks.com/android-app-performance-metrics-a1176334186e)


## Found this project useful :heart:
* Support by clicking the :star: button on the upper right of this page. :v:

[Check out Mindorks awesome open source projects here](https://mindorks.com/open-source-projects)

## Credits
* [Mindorks](https://img.shields.io/badge/mindorks-opensource-blue.svg)(https://mindorks.com/open-source-projects)
* [Mindorks Community](https://img.shields.io/badge/join-community-blue.svg)(https://mindorks.com/join-community)
* [Amit Shekhar](https://github.com/amitshekhariitbhu) 

## License
```
   Copyright (C) 2017 MINDORKS NEXTGEN PRIVATE LIMITED

   Licensed under the Apache License, Version 2.0 (the "License");
   you may not use this file except in compliance with the License.
   You may obtain a copy of the License at

       http://www.apache.org/licenses/LICENSE-2.0

   Unless required by applicable law or agreed to in writing, software
   distributed under the License is distributed on an "AS IS" BASIS,
   WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
   See the License for the specific language governing permissions and
   limitations under the License.
```

## Contributing to Android Interview Questions
Just make pull request. You are in!
