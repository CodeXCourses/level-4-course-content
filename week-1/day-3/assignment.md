# Assignment: Express - Assignment 3

## Objective

- Set up a new Express server.
- Use Express Router to organize routes.
- Handle route parameters.
- Create a basic nested route structure.

## Instructions

1. **Project Initialization**

   - Create a new directory named `express-routing`.
   - Navigate into the directory.
   - Initialize a new Node.js project.
   - Install Express.
   - Create a file named `data.json` and add the following sample data:

     ```json
     [
       {
         "id": 1,
         "name": "John Doe",
         "email": "john.doe@example.com",
         "role": "admin",
         "profile": {
           "age": 30,
           "location": "New York",
           "interests": ["coding", "hiking", "reading"]
         }
       },
       {
         "id": 2,
         "name": "Jane Smith",
         "email": "jane.smith@example.com",
         "role": "user",
         "profile": {
           "age": 25,
           "location": "San Francisco",
           "interests": ["traveling", "music", "sports"]
         }
       },
       {
         "id": 3,
         "name": "Sam Johnson",
         "email": "sam.johnson@example.com",
         "role": "moderator",
         "profile": {
           "age": 28,
           "location": "Chicago",
           "interests": ["gaming", "movies", "technology"]
         }
       },
       {
         "id": 4,
         "name": "Alice Brown",
         "email": "alice.brown@example.com",
         "role": "user",
         "profile": {
           "age": 22,
           "location": "Austin",
           "interests": ["art", "photography", "yoga"]
         }
       },
       {
         "id": 5,
         "name": "Michael Green",
         "email": "michael.green@example.com",
         "role": "user",
         "profile": {
           "age": 35,
           "location": "Seattle",
           "interests": ["cooking", "gardening", "cycling"]
         }
       }
     ]
     ```

2. **Create the Server**

   - Create a file named `index.js` to serve as an entry point.
   - Set up a basic Express server that listens on port 3000.
   - Create a basic route that responds with "Hello, World!" at the root URL.

3. **Use a routes object to organize your routes in a module**

   - Create a directory named `routes` to hold all your routes.
   - Inside the `routes` directory, create a file named `main.js` to define the top level routes.
   - In `main.js`, set up a router that handles:
     - A GET request at the root URL (`/`) that responds with "Hello from the main router!".
     - A GET request at `/about` that responds with "About Us".
   - Import and use the router in the main `main.js` file. Use this router for routes at the base level `/`.

4. **Create Nested Routes for `/user`**

   - Inside the `routes` directory, create a file named `users.js`.
   - Set up the `users.js` router to handle:
     - A GET request at the root URL (`/`) that responds with "List of all users".
     - A GET request at `/:id` that responds with the user ID.
   - Modify the entry point (`index.js`) to use the `users.js` router for all routes starting with `/users`. For example, the route `/users` should respond with "List of all users".
   - Test this route by navigating to URLs like `http://localhost:3000/user/123`.

5. **Test the Routes**
   - Start the server using Nodemon.
   - Test the following routes:
     - `http://localhost:3000/` - Should display "Hello from the main router!".
     - `http://localhost:3000/about` - Should display "About Us".
     - `http://localhost:3000/user/123` - Should display "User ID: 123".
     - `http://localhost:3000/users` - Should display "List of all users".
     - `http://localhost:3000/users/123` - Should display "User ID: 123".

## Submission Guidelines

- Create a new GitHub repository named `express-routing`.
- Push your project to the repository.
- Submit the link to your GitHub repository.

## Rubric

| Criteria                  | Limited (0 pts)                | Partial (3 pts)                          | Complete (5 pts)                                |
| ------------------------- | ------------------------------ | ---------------------------------------- | ----------------------------------------------- |
| Project Initialization    | Significant setup issues       | Minor issues in setup                    | Project setup correctly with `data.json`        |
| Server Creation           | Server does not run            | Server runs but issues with response     | Server runs and responds to root URL            |
| Route Organization        | Routes not organized correctly | Routes organized but minor issues        | Routes organized correctly using Express Router |
| Route Parameters Handling | Route parameters not handled   | Route parameters handled but with issues | Route parameters handled correctly              |
| Nested Routes             | Nested routes not implemented  | Nested routes implemented with issues    | Nested routes implemented correctly             |
