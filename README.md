# MoveDuo
IOS App Development Project

 The name of the application is MoveDuo, written in Swift language in XCode. It is an iOS mobile application developed to find partners in multiplayer activities such as dancing and sports. There are many pages in the application, I designed all the pages from storyboard. Main pages: login (log in / sign up), feed (home page), chats, post, requests, profile.

### login
 The application starts with the beginning screen. If the user wants to log in with their existing account, they can click the “Log In” button, if they want to create a new user account, they can click the “Sign Up” button to go to the next page. I designed the login screen and the sign-up screen with the same Controller. I turned the page into a sign-up or login page by hiding some Labels, TextFields and Buttons on the page according to the button the user pressed. 
 MoveDuo is an online, social platform, application. Users need to be able to access not only their own data in the application, but also all users' data to the extent necessary. Therefore, instead of keeping the data locally (CoreData), I stored it online using Firebase. I used Firebase Authentication to create a user and access the existing user. Firebase Authentication also shows the necessary error message to the user in case of incorrect input.

### feed
 After the user logs in to the application, they are directed to the main page that lists the activity posts shared by all users. This page is actually the first tab of the page that has 5 sub-tabs. On this page, the user can send a request to join other activity posts by clicking the “+” button. The activity post that has been requested and is waiting for the other user’s response will show the text “pending…”. If the other user accepts the request and does not accept it, the text “matched” will show the “+” button to send a request again. The user can also see their own posts on this page. No button or text will appear on the user’s own posts.
 I used TableView to create this page in the storyboard. I used TableViewCell to create a cell for each ad in this table and design a prototype cell. This TableViewCell contains information about the ad such as the activity name, available days and times, and the owner of the post.

 ### post
 If the user wants to create and share an post in this way, they can create the post by selecting the activity, comment, days, time range and ad validity period from the "Post" tab. They can share the created post by clicking the "Upload" button.
 As a new post is shared, it is stored under the collection called “Post” in Firebase’s Cloud Firestore. Firestore is a NoSQL-based database. Each document has a structure similar to JSON format. In other words, all users’ activity posts on the home page are actually pulled from the “Post” collection. If the home page is refreshed, if a new posts is shared, it will appear on the page. 
 Cloud Firestore stores not only the "Post" but also the user's birthday, gender, profile photo url, username, and other extra information that is not kept by Firebase Authentication, under the "Users" collection, with the document name being the user id. I used Firebase Storage to store large images such as profile photos. This way, while the image url is kept in Cloud Firestore, the image in the url is stored in Storage.

### requests
 The user can open the request for the activty post they share from the “Requests” tab. The user can reject or accept the request. In both cases, the request will be deleted from the “Requests” section. However, if the user accepts the request, the application sends a message to the user who sent the request automatically that the activity has been accepted. In this way, the two users can chat for the details of the activity and more.
 While designing “Requests” in Storyboard, I used TableView again and designed each connection request with TableViewCell corresponding to a cell..
 Requests are stored in the Realtime Database in Firebase. Thus, if there is an update in the data, it is reflected in the application simultaneously.
 Activity connection requests are stored in Firebase Realtime Database under the name of the id of the user to whom the request is sent under "requests". "Requests" are kept with variables such as activity id, requesting user id, request sending user id, and sent time. 
 
### chats
 The user can access the chats by clicking on the “chats” tab. By clicking on the cell they want to chat with, they can access the chat with the selected user and continue chatting. In the Storyboard, the cells are listed horizontally using the TableView in “Chats” and “Messages” as in other pages. I used TableViewCell to design the cells. I created two different views by writing two different TableViewCells for sent and received messages. While sent messages are on the right and green, received messages are on the left and gray.
 By storing the messages in the Realtime Database in Firebase, I was able to display them in the application simultaneously as messages came in. In other words, the messages were displayed up-to-date without the need to close and reopen the page or refresh it.

### profile
 The last tab is the “Profile” tab, which is for the user to view and edit their own profile. This page consists of two parts. The upper part contains the user’s profile picture, username, email, gender and date of birth. At the same time, the changes made to the profile information are saved to Firebase with the “Save” button. The “Log Out” button logs out of the user account and automatically redirects to the application’s beginning page.
There are 4 different sub-tabs at the bottom. In this section that I created with TableView, each tab is designed with a different TableViewCell. Thus, whichever tab the user clicks on, those TableViewCells will be displayed.
 The first sub-tab shows the about sub-page. Here, the user can see the about post that was entered during sign-up. The second sub-tab shows a list of all the activity postings shared by the user. The third sub-tab shows the posts that the user made to give more ideas about himself to other users. I made the posts here using CollectionView. Thus, I showed three posts in a row instead of a single post. The last tab, the fourth tab, is the page that allows the user to share about himself. These posts are also stored in the collection called “ProfilePosts” in Cloud Firestore. 
 
 MoveDuo consists of many pages such as activity sharing, profile, messaging, activity connection request. In addition to writing a ViewController class for each page, I also wrote many TableViewCell classes to organize the cells in the page. At the same time, I created classes for objects such as message, user, connection request and stored the properties, arrays and functions.
 I stored the data on the internet using Firebase. I enabled data access from all devices. I took advantage of Firebase's Authentication, Storage, Firestore Database and Realtime Database features.




