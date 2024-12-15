# Assignment: Backend - Assignment 1

## Objective

- Set up a new Express project for a coffee shop e-commerce site backend.
- Connect to MongoDB using Mongoose.
- Define the Product model.
- Implement and test basic CRUD operations for products.

## Instructions

### Part 1: Set Up the Project

1. **Initialize the Project and Install Dependencies**:

   ```bash
   mkdir coffee-shop-backend
   cd coffee-shop-backend
   npm init -y
   npm install express mongoose
   ```

2. **Set Up the Server**:

You may use this starter code for the server setup:

Remember to replace `'your-mongodb-connection-string-here'` with your actual MongoDB connection string and use `dotenv` to store sensitive information.

   ```js
   // index.js
   const express = require('express');
   const mongoose = require('mongoose');
   const app = express();
   const port = 3000;

   // Middleware to parse JSON bodies
   app.use(express.json());

   // Connect to MongoDB
   mongoose
     .connect('your-mongodb-connection-string-here', {
       useNewUrlParser: true,
       useUnifiedTopology: true,
     })
     .then(() => {
       console.log('Connected to MongoDB');
     })
     .catch((error) => {
       console.error('Error connecting to MongoDB:', error);
     });

   app.listen(port, () => {
     console.log(`Server is running at http://localhost:${port}`);
   });
   ```

### Part 2: Define the Product Model

1. **Create the Product Schema and Model**:

Create a new file named `Product.js` inside a `models` folder. Define the schema and model for the `Product` collection.

Your product will have the following fields:  

- `name`: String, required
- `description`: String, required
- `price`: Number, required
- `category`: String, required
- `stock`: Number, required
- `imageUrl`: String, required

### Part 3: Implement Basic CRUD Operations

1. **Setup the Routes directory and create the first route for the products.**

Create a new folder named `routes` in the root directory of the project. Create a new file named `products.js` in the `routes` folder. Create a stub route for the `/` path that returns a JSON response.

```js
// routes/products.js

const Router = require('express').Router;
const router = Router();

// Get all products
router.get('/', (req, res) => {
  res.json({
    message: 'Get all products',
  });
});
```

Import the routes to the `index.js` file and use the routes with the `/products` path.

```js
// in index.js
const productRoutes = require('./routes/products');

app.use('/products', productRoutes);
```

Test the route by sending a GET request to `http://localhost:3000/products` using Thunder Client or Postman. You should see the JSON response.

Create a commit after setting up the first route.

1. **Create the Routes**:

Now that you know it works, you can create more routes in the `products.js` file.
Create stub routes the following routes for the products:

- **POST `/`**: Create a new product
- **GET `/`**: Get all products
- **GET `/:id`**: Get a single product by ID
- **PUT `/:id`**: Update a product by ID
- **DELETE `/:id`**: Delete a product by ID

HINT: The GET `/products` route may look like this:

``` js
// Get all products
router.get('/', async (req, res) => {
  // TODO: Implement this route
  res.json({
    message: 'Get all products',
  });
});
```

**Test** the routes in Thunder Client or Postman.

- **POST `/products`**: Create a new product
- **GET `/products`**: Get all products
- **GET `/products/:id`**: Get a single product by ID
- **PUT `/products/:id`**: Update a product by ID
- **DELETE `/products/:id`**: Delete a product by ID

Test them with Thunder Client or Postman.

Create a commit after creating all the stub routes.

2. **Implement the Routes**:

For each route, implement the route handler to perform the CRUD operation on the `Product` model. Then test the route with Thunder Client or Postman.

For example, the GET `/products` route may look like this:

```js
// Get all products
router.get('/', async (req, res) => {
  try {
    const products = await Product.find();  
    res.json(products);
  } catch (error) {
    res.status(500).json({ error: error.message });
  }
});
```

**Bonus**: Add pagination to the GET `/products` route. You can use the `skip()` and `limit()` methods to implement pagination.

Test this route by sending a GET request to `http://localhost:3000/products` using Thunder Client or Postman.

You will need these routes:

- **POST `/products`**: Create a new product
- **GET `/products`**: Get all products
- **GET `/products/:id`**: Get a single product by ID
- **PUT `/products/:id`**: Update a product by ID
- **DELETE `/products/:id`**: Delete a product by ID

These mongoose methods may be useful:

- `Model.find()`: Find all documents
- `Model.findById()`: Find a document by ID
- `Model.findByIdAndUpdate()`: Find a document by ID and update
- `Model.findByIdAndDelete()`: Find a document by ID and delete

**HINT**: Update can be tricky. You may need to use `findByIdAndUpdate` with the `new: true` option to return the updated document.

```js
   // Update a product by ID
   router.put('/:id', async (req, res) => {
     try {
       const product = await Product.findByIdAndUpdate(
         req.params.id,
         req.body,
         { new: true, runValidators: true }
       );
       if (!product) {
         return res.status(404).json({ error: 'Product not found' });
       }
       res.json(product);
     } catch (error) {
       res.status(400).json({ error: error.message });
     }
   });
```

### Part 4: Test the API

1. **Start Your Server**:

   ```bash
   npm run dev
   ```

2. **Test with Thunder Client or Postman**:

NOTE: You should test each route with Thunder Client or Postman AS YOU CREATE them. Don't wait until you have implemented all the routes to test. Always test as you go.

   - **Create a Product**:

     - Method: POST
     - URL: `http://localhost:3000/products`
     - Body: JSON
       ```json
       {
         "name": "Coffee Mug",
         "description": "A large coffee mug.",
         "price": 12.99,
         "category": "mugs",
         "stock": 100,
         "imageUrl": "http://example.com/mug.jpg"
       }
       ```
     - Screenshot the POST request and response.

   - **Get All Products**:

     - Method: GET
     - URL: `http://localhost:3000/products`
     - Screenshot the GET request and response.

   - **Get a Single Product by ID**:

     - Method: GET
     - URL: `http://localhost:3000/products/<product_id>`
     - Screenshot the GET request and response.

   - **Update a Product by ID**:

     - Method: PUT
     - URL: `http://localhost:3000/products/<product_id>`
     - Body: JSON
       ```json
       {
         "name": "Large Coffee Mug",
         "description": "A large coffee mug, perfect for your morning coffee.",
         "price": 14.99,
         "category": "mugs",
         "stock": 50,
         "imageUrl": "http://example.com/mug.jpg"
       }
       ```
     - Screenshot the PUT request and response.

   - **Delete a Product by ID**:
     - Method: DELETE
     - URL: `http://localhost:3000/products/<product_id>`
     - Screenshot the DELETE request and response.

### Submission

- **GitHub Repository**: Create a new repository named `coffee-shop-backend`. Push your project to the repository and submit the URL. Ensure it includes all necessary files to run the server, including the `README.md`.
- **Screenshots**: Include the screenshots of your POST, GET, PUT, and DELETE requests in the `README.md`.

### Rubric

| Criteria                 | Limited (0 pts)                          | Partial (3 pts)                            | Complete (5 pts)                                                |
| ------------------------ | ---------------------------------------- | ------------------------------------------ | --------------------------------------------------------------- |
| **Project Setup**        | Significant setup issues                 | Minor issues in setup                      | Project set up correctly with required packages                 |
| **Schema and Model**     | Schema and model not defined             | Schema and model defined with minor issues | Schema and model defined correctly                              |
| **Route Implementation** | Significant issues or routes not working | Minor issues in route implementation       | All routes are correctly implemented and working                |
| **API Testing**          | Requests and responses not documented    | Some requests and responses documented     | All required requests and responses documented with screenshots |
| **GitHub Repository**    | Repository not set up correctly          | Repository set up with minor issues        | Repository set up correctly with all necessary files            |
