<p align="center">
<img alt="AndroidInterviewQuestions" src="https://raw.githubusercontent.com/MindorksOpenSource/android-interview-questions/master/assets/android_interview_questions.png">
</p>

## Contents
 * [Support](#support)
 * [Core Android](#core-android)
 * [Core Java](#core-java)
 * [Data Structures And Algorithms](#data-structures-and-algorithms)
 * [Architecture](#architecture)
 * [Design Problem](#design-problem)
 * [Tools And Technologies](#tools-and-technologies)
 * [Android Test Driven Development](#android-test-driven-development)

## Support

### REST APIs
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

### Volley
* Better quality, better caching and less coding than Volley

### REST vs SOAP
* SOAP has overhead - envelope and body wrapping actual data while REST only contains actual data
* SOAP offers security for envelopes, while REST does not
* SOAP data format is XML, REST data format is XML/JSON

### ButterKnife
* Eliminate `findViewById` calls by using `@BindView` on field
```
@BindView(R.id.user) EditText username;
@BindView(R.id.pass) EditText password;
@BindString(R.string.login_error) String loginErrorMessage;
```
### About Build System - Gradle
* Build systems are software tools designed to automate the process of program compilation
* Turn all source code into APK file
* Uses Groovy language to customize build system (e.g. compileSdkVersion, dependencies that contains libraries online - replace .aar or .jar file)

#### What are the metrics that you should measure continuously while android application development? [Mindorks]
(https://blog.mindorks.com/android-app-performance-metrics-a1176334186e)

## Core Android

### Activity lifecycle
1. Starting state
   * Before starting an activity, it is not in memory
2. Running state
   * Transition state from starting to running state is very computationally intensive and affects battery life
   * Only one activity is on running state at a time
   * When an activity is called, it will call three methods accordingly and automatically:
     * onCreate() 
     * onStart() 
     * onResume() 
3. Paused state
   * When user is not interacting with screen but screen is still visible to user
   * onPause() 
4. Stop state
   * When activity is not visible, but still in memory
   * onStop() - Only after pausing, it will stop the activity
5. We want to go back to our app
   * onRestart() 
   * onStart() 
   * onResume()
6. We want to go back to previous activity (close current app)
   * onPause() 
   * onStop() 
   * onDestroy()
7. Destroy 
   * Activity is no longer in memory
   * When app is killed, it needs to create the activity again (Same as step 2)
   * onCreate() 
   * onStart() 
   * onResume()  

<p align="center"><img src="https://github.com/jun159/android-interview-questions/blob/master/assets/activity_lifecycle.png" height ="600"></p>

### Define all Android application components
1. Activities
   * Represents a single screen with a user interface 
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

### Service vs IntentService
1. Service
   * Can be used in tasks with no UI, but shouldn't be too long
   * If you need to perform long tasks, you must use threads within Service.
2. IntentService
   * Can be used in long tasks usually with no communication to main thread

### How to persist data in an Android app?
1. SharedPreferences
   * Store private primitive data in key-value pairs
2. Internal Storage (File)
   * Store private data on the device memory
3. External Storage
   * Store public data on the shared external storage
4. SQLite
   * Store structured data in a private database
5. Network Connection
   * Store data on the web with your own network server

### How would you perform a long-running operation in an application?
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
   
### Relative Layout vs Linear Layout
* LinearLayout: Lay out its children next to each other (horizontally or vertically)
* RelativeLayout: Each element’s position is relative to other elements (i.e. Neighbours - top, bottom, left, right)
* AbsoluteLayout: Each element’s position is specified by (x,y)
* TableLayout: Displays elements in the form of table (rows and columns)
* GridView: Arrange its children in 2D scrollable grid

### Difference between `RecyclerView` and `ListView`? 
* RecyclerView reuses same item types so that it doesn't recreate new item
* RecyclerView prevents costly findViewById uses (cache it)
* RecyclerView can dynamically change to list or grid view anytime, but previously we must use ListView for list or GridView for grids
* RecyclerView.ItemDecoration allows adding of borders or dividers easily

### Difference between `View.GONE` and `View.INVISIBLE`?
* View.GONE: View is invisible, and it doesn't take any space for layout purposes
* View.INVISIBLE: View is invisible, but it still takes up space for layout purposes

### Difference between a fragment and an activity? 
* Fragment is a part of an activity, which contributes its own UI to that activity. 
* Fragment can be thought like a sub activity. Where as the complete screen with which user interacts is called as activity. 
* An activity can contain multiple fragments. Fragments are mostly a sub part of an activity.
* A fragment can be reused in multiple activities, so it acts like a reusable component in activities.
* A fragment can't exist independently. It should be always part of an activity. Where as activity can exist with out any fragment in it.

### What is the difference between Serializable and Parcelable? Which is the best approach in Android?
* We cannot just pass objects to activities
* Objects must be either implements Serializable or Parcelable interface 
* Parcelable is faster than serializable interface
* Parcelable interface takes more time for implemetation compared to serializable interface
* Serializable interface is easier to implement
* Serializable interface create a lot of temporary objects and cause quite a bit of garbage collection
* Parcelable array can be pass via Intent in android

### What is `AndroidManifest.xml`?
* Specify permissions, intents, etc.
* Contains essential information about your app to the Android system
* Which the system must have before it can run any of the app's code

#### How would you communicate between two `Fragments`?
* Activity is the middleman

#### Explain Android notification system?

#### How can two distinct Android apps interact?

#### Why is it recommended to use only the default constructor to create a fragment? [StackOverflow](https://stackoverflow.com/a/16042750/2809326)

#### Why Bundle class is used for data passing and why cannot we use simple Map data structure

#### What is `Dialog` in Android?

#### What is `View` in Android?

#### Can you create custom views? How?

#### What are ViewGroups and how they are different from the Views?

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

#### How to implement XML namespaces?

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
