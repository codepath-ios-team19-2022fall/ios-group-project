Unit 5: Group Milestone - README
===

# DayFrame

## Table of Contents
1. [Overview](#Overview)
1. [Product Spec](#Product-Spec)
1. [Wireframes](#Wireframes)
2. [Schema](#Schema)

## Overview
### Description
A calendar that can tracker user's emotional ebb and flow

### App Evaluation

- **Category:** Organization/Mental Health
- **Mobile:** This app would primarly be used on mobile but it could be used across different technologies.
- **Story:** Creates a calendar that can add events and show
- **Market:** This app could be used by an individual for their day to day lives, what events they have going on, how they are feeling, and overall help keep track of a person's schedule. 
- **Habit:** This app can be used whenever the user feels the need to track events and keep track of their moods.
- **Scope:** This could be used for individuals wanting to track their personal progress and plan ahead in terms of their schedule. It can also help show trends between moods and their schedule, and it will help a person maintain the progress that they make with tasks and their mood.  

## Product Spec

### 1. User Stories (Required and Optional)

**Required Must-have Stories**

* User logs in to access calendar, mood track, and preference settings
* User updates the mood setting for the day
* User can view the calender in monthly, weekly and daily mode
* User can add, edit and delete events from the calender
* User can switch view between montly, weekly and daily
* User can set up mood settings preference
* Application can send notifications
* Styled log in and registration screen [x]


**Optional Nice-to-have Stories**

* Calender can sync with other calenders
* Calender can shared with other designated users


### 2. Screen Archetypes

* Login
* Register - User signs up
* Update the mood of the day
    * User choose the mood of the day
        * When user choose "Help please", Help page appears
    * User choose how often the app can track his/her mood

* Help Page
    * When user choose "Help please!"
    * Options of helps
* Calendar monthly view
* Calendar weekly view
* Calendar daily view
* Mood Settings
* App Settings

### 3. Navigation

**Tab Navigation** (Tab to Screen)

* Calendar
* Mood Today
* Mood Settings
* App Settings
* Add events
* Daily View
* Weekly View
* Monthly View

**Flow Navigation** (Screen to Screen)

* Login -> Mood Today
* Mood Today -> Monthly View
* Mood Today -> Help Page
* Mood Today -> Cheer me up Page
* Monthly View -> Weekly View
* Monthly View -> Daily View
* Weekly View -> Monthly View
* Weekly View -> Daily View
* Daily View -> Weekly View
* Daily View -> Monthly View


## Wireframes
### [BONUS] Digital Wireframes & Mockups
<img width="1615" alt="Screen Shot 2022-10-11 at 8 53 43 PM" src="https://user-images.githubusercontent.com/89565796/195239117-5ef81102-d9c4-4bff-94d1-c9ddd151ca26.png">

(https://miro.com/app/board/uXjVPPGEU0A=/?share_link_id=423974694587)
<img src="YOUR_WIREFRAME_IMAGE_URL" width=600>


## Schema 

Title Screen
| Property | Type  | Description |
| :---:   | :---: | :---: |
| username | String | The user's username for the account|
| password | String | The password associated with the account|

Today's Mood
| Property | Type  | Description |
| :---:   | :---: | :---: |
| dailyMood | String | Mood of the user on that day|
| dailyMoodTrack | String | How many times the user wants their mood checked|

Monthly View
| Property | Type  | Description |
| :---:   | :---: | :---: |
| month | Number | Correlates with what month it is|
| year | Number | Correlates with what year it is|

Daily View
| Property | Type  | Description |
| :---:   | :---: | :---: |
| day | Number | Correlates with what day it is|
| time | Number | Time of each event|
| event | String | Short description/title for each event given by user |

Mood Settings
| Property | Type  | Description |
| :---:   | :---: | :---: |
| greetings | Boolean | Whether the user wants morning greetings|
| moodNotif | Boolean | Whether the user wants notifications for mood checks|
| moodShare | Boolean | Whether the user wants to share their mood with others on the app |

Contacts
| Property | Type  | Description |
| :---:   | :---: | :---: |
| image | File | Image of the contact|
| name | String | Name of the contact|
| connection | String | Way the user knows the contact|
| contactInfo | String | Contact information of the contact|


### Networking
- Login
    - (Read/GET) Query identity provider with username and password
```
    @IBAction func signin(_ sender: Any) {
        PFUser.logInWithUsername(inBackground: self.txtUsernameSignin.text!, password: self.txtPasswordSignin.text!) {
          (user: PFUser?, error: Error?) -> Void in
          if user != nil {
            self.displayAlert(withTitle: "Login Successful", message: "")
          } else {
            self.displayAlert(withTitle: "Error", message: error!.localizedDescription)
          }
        }
    }
```
    
- Register
    - (Write/POST) Register user on back4app
```
    @IBAction func signup(_ sender: Any) {
        let user = PFUser()
        user.username = self.txtUsernameSignup.text
        user.password = self.txtPasswordSignup.text
        
        self.indicatorSignup.startAnimating()
        user.signUpInBackground {(succeeded: Bool, error: Error?) -> Void in
            self.indicatorSignup.stopAnimating()
            if let error = error {
                self.displayAlert(withTitle: "Error", message: error.localizedDescription)
            } else {
                self.displayAlert(withTitle: "Success", message: "Account has been successfully created")
            }
        }
    }
```

- Mood Selector
    - No network interaction
- Mood Motivations
    - No network interaction
- Motivating Pictures
    - (Read/GET) Query data base for motivating pictures for user
    ```
    // Using back4app.com as back end
    let image = PFObject(imageClass: "images")
    ```
## Progress
<img src='http://g.recordit.co/KNlQTrndtD.gif' title='10-24 Progress' width='' alt='10-24 Progress'/>
