

# Mentor2Mentee

## Table of Contents
1. [Overview](#Overview)
1. [Product Spec](#Product-Spec)
1. [Wireframes](#Wireframes)
2. [Schema](#Schema)

## Overview
### Description
Mentor2Mentee simply bridges the gap between students and mentors, one connection at a time. 
At the press of a button, a student can find a mentor in their respective field, schedule a call with them, and the app will help facilitate by allowing students to list goals that they and their mentor come up with, 
along with allowing mentors to leave feedback for students. 


### App Evaluation
[Evaluation of your app across the following attributes]
- **Category: Productivity**
- **Mobile: This is a primarily mobile application, with potential to even become a viable web application.**
- **Story:Users who are in need of mentors can create an account, look at a list of mentors in different fields and pick a compatible mentor. Users can also schedule calls with their mentor and track their progress with their mentors.**
- **Market: Students in need of mentors**
- **Habit:This app could be used daily by individuals who need mentors and could use constant assistance**
- **Scope: First, the app would allow users to create accounts and store a list of potential mentors. Next, we would build the aspects that allow for communication and progress tracking between mentors and mentees.**

## Product Spec

### 1. User Stories (Required and Optional)

**Required Must-have Stories**

[x] User can create profile
[x] User can log in
[x] Users can swipe left or right to choose a mentor from a list of mentors
[x] User can view his/her profile page
[x] User can chat with mentor

**Optional Nice-to-have Stories**

* App has Mentor2Mentee branding

### 2. Screen Archetypes

* Login
   * User can login or create an account with email and password
* Home
   * User can see a dashboard with their mentor and bar to navigate between different screens
 * Chat
   * User can message their mentor and receive messages from their mentor
 * Mentor Select
   * User can swipe left or right between mentor selections and choose mentors that are compatible

### 3. Navigation

**Tab Navigation** (Tab to Screen)

* Home
* Profile
* Chat

**Flow Navigation** (Screen to Screen)

* Account login or creation
* Mentor Selection
* Chatting with mentor
* Viewing profile


## Wireframes
[Add picture of your hand sketched wireframes in this section]
<img src="https://github.com/Mentor2Mentee/Mentor2Mentee-App/blob/main/Screen%20Shot%202021-10-18%20at%2010.27.39%20PM.png" width=600>

### [BONUS] Digital Wireframes & Mockups
<img src="https://github.com/Mentor2Mentee/Mentor2Mentee-App/blob/main/Screen%20Shot%202021-10-18%20at%2010.16.17%20PM.png" height=200>

### [BONUS] Interactive Prototype
<img src="https://github.com/Mentor2Mentee/Mentor2Mentee-App/blob/main/m2m.gif" width=200>

### Networking

* Create User
```
public void createUser() {
  ParseUser user = new ParseUser();
  user.setUsername("my name");
  user.setPassword("my pass");
  user.setEmail("email@example.com");

  // Other fields can be set just like any other ParseObject,
  // using the "put" method, like this: user.put("attribute", "its value");
  // If this field does not exists, it will be automatically created

  user.signUpInBackground(e -> {
    if (e == null) {
        // Hooray! Let them use the app now.
    } else {
        // Sign up didn't succeed. Look at the ParseException
        // to figure out what went wrong
        Toast.makeText(this, e.getMessage(), Toast.LENGTH_SHORT).show();
    }
  });
}
```
* Login
   * User can login or create an account with email and password

```
public void loginUser() {
  ParseUser.logInInBackground("<userName>", "<password>", (user, e) -> {
    if (user != null) {
        // Hooray! The user is logged in.
    } else {
        // Login failed. Look at the ParseException to see what happened.
        Toast.makeText(this, e.getMessage(), Toast.LENGTH_SHORT).show();
    }
  });
}
```

* Home
   * User can see a dashboard with their mentor and bar to navigate between different screens
   * Pull picture
```
ParseFile image = post.getImage();
            if (image != null) {
                Glide.with(context).load(post.getImage().getUrl()).into(ivImage);


            }
```
  * Pull User
 ```
 public ParseUser getUser() {
        return getParseUser(KEY_USER);
    }
 ```
    
    * 
 * Chat
   * User can message their mentor and receive messages from their mentor
   ```
   ibSend.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                String data = etMessage.getText().toString();
                ParseObject message = ParseObject.create("Message");
                message.put(USER_ID_KEY, ParseUser.getCurrentUser().getObjectId());
                message.put(BODY_KEY, data);
                message.saveInBackground(new SaveCallback() {
                    @Override
                    public void done(ParseException e) {
                        if (e == null) {
                    	    Toast.makeText(ChatActivity.this, "Successfully created message on Parse",
                            Toast.LENGTH_SHORT).show();
                        } else {
                            Log.e(TAG, "Failed to save message", e);
                        }
                    }
                });
                etMessage.setText(null);
            }
        });
   ```

## Schema 
| Property      | Type     | Description |
   | ------------- | -------- | ------------|
   | objectId      | String   | unique id for the user post (default field) |
   | username      | String   | unique id for user |
   | author        | Pointer to User| image author |
   | image         | File     | image that user posts |
   | caption       | String   | image caption by author |
   | messages      | String   | conversation shared between parties |
   | likesMatch    | Bool     | did the user swipe to connect to mentor or not|
   | createdAt     | DateTime | date when post is created (default field) |
   | updatedAt     | DateTime | date when post is last updated (default field) |
[This section will be completed in Unit 9]
### Models
[Add table of models]
### Networking
- [Add list of network requests by screen ]
- [Create basic snippets for each Parse network request]
- [OPTIONAL: List endpoints if using existing API such as Yelp]
