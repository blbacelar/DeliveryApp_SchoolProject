# Pra ja (Delivery app)
<img width="800" alt="screen shot 2018-06-02 at 21 16 03" src="https://user-images.githubusercontent.com/8979200/40883076-3fd984d0-66aa-11e8-96a3-563abf31f55c.png">

This is delivery application for iOS which I created with 4 team members for school project. This is just mock app but I describe what kind of app it is and what technologies I used.
I was tech lead in the team so I decided architecture and supported others.

※ In order to keep secure, I didn't upload `GoogleService-Info.plist`. It means even you run this app, you cannot connect to backend.

# About Technologies
## Architecture
<img width="1680" alt="architecture" src="https://user-images.githubusercontent.com/8979200/40883014-1c966440-66a8-11e8-955f-7e408bfd8d4a.png">

We used Clean Architecture + MVVM.
The reason why we decided using this architecture is that this is the one of most popular and common architecture recently so I thought it's worth to learn.


## Libraries
### Swinject
![13637225](https://user-images.githubusercontent.com/8979200/40883335-df10e792-66ae-11e8-97db-9b4ae4fddc56.png)

https://github.com/Swinject/Swinject

To use the architecture cleanly, dependency injection is useful.
It worked really well and helped us to focus coding!

### RxSwift
![1_vfxlildvzeg4drqbh_2lxw](https://user-images.githubusercontent.com/8979200/40883331-dee59042-66ae-11e8-9e33-8193d419c3d6.png)

https://github.com/ReactiveX/RxSwift

We used RxSwift for binding View and ViewModel and also to receive result in ViewModel.


## Backend
![1_winrwnanwjbzbjlxugrj6a](https://user-images.githubusercontent.com/8979200/40883333-defaa07c-66ae-11e8-875b-062142326191.png)

We used Firebase as backend.
There are 2 options for database, Realtime Database and Cloud Firestore.
We decided to use Cloud Firestore even it's still beta because it enables you to make more flexible query and it seems Cloud Firestore will be standard database of Firebase.

### How we defined data structure
<img width="1014" alt="screen shot 2018-06-02 at 21 30 46" src="https://user-images.githubusercontent.com/8979200/40883178-6024c8ba-66ac-11e8-9086-929b81aae75e.png">

First we defined entity relational diagram or ERD, but we figured out it didn't work for Firebase because Firebase is NoSQL model!! 😨
So we migrated it to SpreadSheet to fit NoSQL model like the above image.


### How we inserted master data to Firestore
You can insert data to Firestore using Firesbase console but if you do this way, you need to input all data one by one.
It's so pain and it's not what developer should do.
Therefore we input master data to SpreadSheet like following.

<img width="1270" alt="screen shot 2018-06-02 at 21 35 41" src="https://user-images.githubusercontent.com/8979200/40883195-f55380d4-66ac-11e8-9975-cf86eaba8efe.png">

Then I wrote google app script using librariy which enables you to insert data to Firestore.
I also created `Firestore` menu to the spread sheet in order to save data from spread sheet to Firestore easily.

<img width="443" alt="screen shot 2018-06-02 at 21 38 43" src="https://user-images.githubusercontent.com/8979200/40883207-79722ce4-66ad-11e8-962f-aa8a63bd0465.png">

The benefits of this are following.
- You don't need to input key and value one by one
- You never typo the name of key
- Even if someone deleted all data by mistake, it's easy to restore

