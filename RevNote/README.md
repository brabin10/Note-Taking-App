# 220321-Java-React-Team2-P2
## RevNotes
Team Darkmode made a fun note taking application called RevNotes for Revature trainees. It features login, registration, note creation, and a weather feature. The App runs on a stack incorporating various industry grade technologies. Technologies include a Spring Backend with REST APl controllers serving data from a PostgreSQL database instance, a React Redux dispatcher for login and note actions in Typescript as well a charming and minimalistic CSS frontend for theming.

RevNotes has potential to become a full fledged planning application for trainees to help them stay organized and focused while also having fun. Possible features to add include: light and dark mode, a calendar, pop-up reminders, to-do lists, stickers, and background themes. As a group we are proud of what we have created and look forward to working further on new and exciting projects.

## Technologies
* HTML/CSS/
* Typescript
* Javascript
* React.js
* JWT
* Hooks
* Redux
* Spring mvc
* Java
* Hibernate
* Junit
* Rest API
* Spring
* PostgreSQL




## Spring Security Implementation
Our API is now secured via JWT Json Web Token Encryption, on running the application Spring Security will generate 3 boilerplate tables, User, User_Roles, and ROLES. I have defined these roles in an ENUM called ROLES_ENUM


The first thing you should do is register a user with a post request to:

http://hostname:8080/api/auth/signup

with the user details as such in the body 
{
"username":"user",
"password":"password",
"email":"email",
"role":["admin","user"]
}
this will create a user account with a Hashed Password -- do NOT add the user in plain text via DBeaver as it will not read the login info




Login is achieved by sending a post request to http://hostname:8080/api/auth/signin

{
"username":"user",
"password":"password"
}

response will be user info + JSON Web Token. I will likely from here tie in the notes to another table with the same user and pw. 

Registration is a post to signup with the details.
All of the methods tagged @Preauthorize require an auth token




## Requests/Handler Addressing

This API has all of the crud methods neccesary for the purposes of the RevNotes app. Here are the endpoints and protocols, along with a description and a sample JSON payload


## Note Object POST Requests
http://localhost:8080/notes
A post with this object will add a note to the TABLE (read on)
                {
                "note_id": 1,
                "note_title": "firstnote",
                "newUserDTO": null,
                "date_created": "05/15/22",
                "noteObject": "this is a note",
                "userID": 1
                }
 Add this note with a USERID, to attatch to a certain user use the OTHER Add post, an empty user ID will throw a Null pointer. This will work fine from within your webclient once we have a user id, but for testing purposes just use an entry on the database in the RevUserTable
 

A POST Request to 
http://localhost:8080/users/{userID}/notes/{noteID}/add
(UserID and NoteID = The id numbers from the RevUser and Notes Table of your choice)
this adds a note created above to the specified User in the Table.

## Note Object Deletion
http://localhost:8080/users/{userid}/notes/{noteid}
A delete request sent with the requested variables, drops the note object from the table

## Note Update
Pass the note in Json format in a PUT request to:
users/{userid}/notes/"
where the users id is in the link (revnotes user id)



## Application Configuration 
Open the project and navigate to source/main/resources and fill out the placeholders below

spring.main.banner-mode=CONSOLE

logging.level.org.springframework=ERROR

spring.datasource.initialization-mode=always

spring.datasource.platform=postgres

spring.datasource.url=jdbc:postgresql://localhost:5432/{YOUR_DBs_NAME}

spring.datasource.username={YOURPOSTGREUSERNAME}

spring.datasource.password={YOURPOSTGREPASSWORD}

spring.jpa.properties.hibernate.jdbc.lob.non_contextual_creation= true

spring.jpa.properties.hibernate.dialect= org.hibernate.dialect.PostgreSQLDialect

spring.jpa.hibernate.ddl-auto= update

darkmode.app.jwtSecret= teamDarkmode

darkmode.app.jwtExpirationMs= 86400000

# Getting Started with Create React App

Note: You will need to install Java 8 or above
* From terminal, cd to directory where project will be located
* git clone repository https://github.com/brabin10/Project1/tree/main/ERSProject
* git pull
This project was bootstrapped with [Create React App](https://github.com/facebook/create-react-app).

## Available Scripts

In the project directory, you can run:

### `npm start`

Runs the app in the development mode.\
Open [http://localhost:3000](http://localhost:3000) to view it in the browser.

The page will reload if you make edits.\
You will also see any lint errors in the console.

### `npm test`

Launches the test runner in the interactive watch mode.\
See the section about [running tests](https://facebook.github.io/create-react-app/docs/running-tests) for more information.

### `npm run build`

Builds the app for production to the `build` folder.\
It correctly bundles React in production mode and optimizes the build for the best performance.

The build is minified and the filenames include the hashes.\
Your app is ready to be deployed!

See the section about [deployment](https://facebook.github.io/create-react-app/docs/deployment) for more information.

### `npm run eject`

**Note: this is a one-way operation. Once you `eject`, you can’t go back!**

If you aren’t satisfied with the build tool and configuration choices, you can `eject` at any time. This command will remove the single build dependency from your project.

Instead, it will copy all the configuration files and the transitive dependencies (webpack, Babel, ESLint, etc) right into your project so you have full control over them. All of the commands except `eject` will still work, but they will point to the copied scripts so you can tweak them. At this point you’re on your own.

You don’t have to ever use `eject`. The curated feature set is suitable for small and middle deployments, and you shouldn’t feel obligated to use this feature. However we understand that this tool wouldn’t be useful if you couldn’t customize it when you are ready for it.

## Learn More

You can learn more in the [Create React App documentation](https://facebook.github.io/create-react-app/docs/getting-started).

To learn React, check out the [React documentation](https://reactjs.org/).

## License
Licensed under the [MIT License](LICENSE).
