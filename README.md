Unit 14: Full-Stack Reverse Engineering Code
Develop folder: 
    1. Config file: 
        Establishes database connections
        1. isAuthenticated.js: 
            This is the middleware it restricts the routes a user can visit if the are not logged in. If they are not logged in they are returned to the login page.
        2. config.json file: 
            Configures the database.
        3. Passport.js file:
            Passport is middleware authentication for The local authentication strategy authenticates using username and password. 
            usernameField: changes the username credentials to the word ‘email’. When the user tries to sign in the code checks if the email exist in the db, if it does then it checks if the password is correct.
    2. Models: 
        Database or data related functionality
        1. Example.js file:
            Create example model.
        2. Index.js file: 
            Stores configuration variables- exports a JSON object where each key is assigned from an environment variable and a  secondary, contingency value. Settings can differ depending on the environment, whether it is for development or for production. Fs.readdirsync: synchronously reads the directory _dirname of index.js excluding this file and that the files ending in “.js”. Sequelize.import imports the model defined in the file.  The name of the model is mapped on the dictionary db. After that a loop runs that calls associate on each model if that model contains association methods.
        3. Schema.js file: 
            Creates database
        4. User.js: 
            Creates user model. Bcrypt is a cryptographic hash function. It is a mathematical algorithm that maps data of arbitrary size to a string of a fixed size. Before it is exported we use the define method to define a new database called user and the properties create the column names email and password. Some validation is added (allowNull: false, unique: true, validate: {isEmail: true}). User.prototype allows you to add a new method(validPassword) a boolean value when the plain text password is compared against the hashed password. User.addHook adds a function that is called before the user is created. Bcrypt.hashSync generates a hash for user.password adds random data to the hash and the value is returned.
    3. Node-modules: 
        required modules/libraries
    4. Public: 
        Static files can download from the server.
        1. Js:
            1. Index.js file: 
                front-end, API utilizing ajax.
                    1. Gets references to elements on the page.
                    2. Each API object contains a method for each request
                    3. Function expressions to:
                        1. Retrieve examples from the database
                        2. Handle form submissions to database. The event handler also generates an ID for         submitted example.
                        3. Saves new examples.
                        4. Deletes examples from database.
            2. Login.js file: Validates the user and redirects the uer to the login.
                    1. Gets reference to the form and the input values.
                    2. Validates that an email and a password are present when the form is submitted.
                    3. If they are present run login user function and clear the form.
                    4. Post to the api login and if successful redirect to the member page.
            3. Members.js: Does the GET request to figure out which user is logged in and update html on the page.
            4. Signup.js: Validates user and redirects signup.
                    1. Gets reference to form and input values.
                    2. Validate that an email and password are present when the form is submitted.
                    3. If they are present run the login user function and clear form.
                    4. Post to the api signup and if successful redirect to the member page.
        2. Styles:
            Styles.css is a stylesheet
        3. Stylesheets:
            Style.css is a stylesheet
        4. login.html:
            Login html page
        5. members.html:
            Members html page
        6. signup.html:
            Signup html page
    5. Routes:
        1.  apiRoutes.js: 
            Examaple model routes
        2.  htmlRoutes.js: 
            Example model routes
        3.  api-Routes.js: 
            User model routes
            1. /api/login route validates login credentials and redirect the user to the member page
            2. /api/signup route: if the user is created succesfully it redirects to login page
            3. /logout route: logout the user and redirect to the login page
            4. /api/user_data: gets the user email and id if they are logged in.
        4.  html-Routes.js: 
        5.  User model routes
            1. /route: If the user is a member it sends them to the member page or else it sends them to the signup page.
            2. /login: if the user has an account it sends them to the member page or else it sends them to the login page
            3. /members: if a non authenticated user tries to access this route they will be redirected to the signup page
    6. Test:
        1.  Canary.test.js: A canary test is set up to always pass so we know that our testing suite is set up right.
    7. Views: What the user will see.
        1.  Layouts
            1. Main.handlebars: the main html page wrapper. It can be reused for the different views of the app. {{{body}}} is used as a placeholder for the main content.
        2.  404.handlebars
            A route for the example responds with a error page hardcoded in 404.handlebars.
        3.  Example.handlebars
            A template for the example card
        4.  Index.handlebars
            Template for example index page.
    8. Server.js: entry file that starts the application. Dependencies are included and routes are created. Within routes, http methods and URL paths are defined. A handler function is also created to process the request and reply. The handler function first contains information regarding the HTTP call (request) and the second provides a method to handle the call response (reply).
    9.  Package.json: Node.js- Contains all required dependencies and scripts that are to be installed 
    10. Package-lock.json: Node.js- version control 


