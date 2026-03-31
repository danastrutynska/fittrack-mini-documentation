# fittrack-mini-documentation

## Table of Contents

- [Product Overview](#product-overview-and-target-audience)
- [User Guide](#user-guide)
- [API Documentation](#api-documentation)

## Product overview and target audience

FitTrack Mini is a mobile fitness tracking application designed to help users monitor their daily activity, set goals, and track progress.

### Key features include:

- Step tracking
- Workout logging
- Goal management
- Progress statistics
- Notifications and reminders

### Target Audience:

- General users interested in fitness tracking
- Beginner users looking for simple health monitoring tools

## User Guide

### Introduction

FitTrack Mini is a simple application for your fitness and health journey. With its versatile set of features, you can track your daily step number, record workouts, set your own personal goals, review statistics and progress, and receive activity reminders. 

### Getting Started

### Installing the application

Go to App Store. 
Type FitTrack Mini into the search bar.
Find the FitTrack Mini app in the search results
Tap Get next to the FitTrack Mini icon. 
Wait for the application to install. 
Tap Open to launch the application. 

### Registration 

Tap New account link on the main page.
Fill out the fields with your First Name, Last Name, email, and date of birth.
Create a password that consists of at least 6 characters, one of which is a letter. 
Repeat the password to confirm it.
Toggle the switch to allow the application to send notifications (optional). 
Once your account is created, you will be redirected to the main screen.

### Login

On the main page, fill out the email and password fields.
Tap the Log in button.
Once you are logged in, you will be redirected to the app’s main screen. 

### Tracking Daily Steps

### How to track daily steps

On the main screen, tap Menu.
Select Steps at the top of the list. 
Toggle the switch next to Track daily steps to enable tracking.
Once enabled, the app starts tracking your daily steps automatically. 

### How to track progress of daily steps

On the main screen, tap Menu.
Select Steps at the top of the list. 
Tap View Daily Progress link.
Once selected, the app generates a chart showing the number of daily steps per hour throughout a day. 

### Logging workouts

### Add a workout

On the main screen, tap Menu.
Select Workouts from the menu. 
Tap Log a Workout link.
Select Workout Type from the list (e.g., jogging, yoga, power lifting).
Enter Duration into the field in minutes (e.g., 45). 
The app automatically calculates calories burned and adds them to daily statistics. 

### Setting goals

### How to set up daily or weekly goals

On the main screen, tap Menu.
Select Goals from the menu. 
Tap Add New Goal.
Add Goal Name. 
Select Goal Duration (e.g., Daily)
Select Goal Type (e.g., Steps)
Enter the number of steps for your goal (e.g., 4000).
Tap Create New Goal button. 
Once the goal is set up, the app adds it to Current Goals. 

### How to track goals

On the main screen, tap Menu
Select Goals from the menu. 
Tap Current Goals.
Tap Goal Name on the list to view its details. 
The app opens Goal Details screen with a progress bar indicating goal completion. 

### Viewing statistics

### How to view statistics

On the main screen, tap Menu
Select Statistics from the menu. 
Select a category from the list (e.g., Steps)
Select a duration (e.g., week)
The app generates a chart showing the daily steps taken throughout the selected duration and the average daily steps.  

### Notifications & reminders

### How to turn on notifications

On the main screen, tap Settings.
Select Reminders.
Toggle the switch next to the preferred category (e.g., Turn On Goal Completion Reminders).
The app will send notifications to your home screen based on your preferred selection.

### What to do if the app does not send notifications

Open Settings on your iPhone
Select Notifications
Select FitTrack Mini from the Notification Style section.
Toggle the switch next to Allow Notifications. 
The app will send notifications to your home screen based on your preferred selection.

### Troubleshooting

### What to do if the step counting does not work.

On the main screen, tap Settings.
Select Access.
Toggle the switch next to Allow Motion Sensors Access. 
Make sure the access is also enabled in your phone settings. 

## API Documentation

### Create a Goal

**Endpoint**

`POST /goals`

**Description**

`Creates a new goal` 

**Request Body**

```json
{ 
 "name": "burn 200 calories",
 "type": "power lifting",
 "duration": 60
 }
```

**Response**

201 Created 

```json
{ 
 "id": 1, 
 "name": "burn 200 calories", 
 "type": "power lifting",
 "duration": 60
}
```
### Get All Goals

**Endpoint**

`GET /goals`

**Description** 

`Returns a list of all goals`

**Response**

200 OK

```json
[
 {
   "id": 1,
   "name": "daily steps",
   "calories": 200
 },
{
   "id": 2,
   "name": "yoga",
   "calories": 150
}
]
```

### Update a Goal 

**Endpoint**

`PUT /goals/{id}`

**Description** 

`Updates an existing goal`

**Request Body** 

| Field   | Type   | Required | Description                  |
|--------|--------|----------|------------------------------|
| name   | string | yes      | Name of the goal             |
| target | number | yes      | Target in calories or steps  |
| duration | string | yes   | Goal duration                |

**Example Request** 

```json
{ 
 "name": "power lifting",
 "target": 200,
 "duration": "weekly"
 }
```

**Response**

200 OK

```json
{ 
 "id": 1, 
 "name": "power lifting", 
 "target": 200,
 "duration": "weekly"
}
```

**Possible Errors**

|Code|Description|
|--------|--------|
|400|Invalid request data|
|404|Goal was not found|
|401|Unauthorized|

### Delete a Goal

**Endpoint**

`DELETE /goals/{id}`

**Description**

`Deletes a goal by ID.`

**Response**

204 No content

**Possible errors**

|Code|Description|
|--------|--------|
|404|Goal not found|
|401|Unauthorized|

### Get goals with filtering

**Endpoint**

`GET /goals?type=calories&limit=3`

**Description**

`Returns a list of goals filtered by type and limited by the specified number.`

**Response**

```json
{
 [
  {
    "id" : 1,
    "name" : "weight lifting",
    "type : "calories"
   },
   {
    "id" : 5,
    "name" : "yoga",
    "type : "calories"
   },
   {
    "id" : 15,
    "name" : "pilates",
    "type : "calories"
   },
  ]
}
````

**Possible errors**

|Code|Description|
|--------|--------|
|400|Invalid parameters|
|401|Unauthorized|


