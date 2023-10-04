# Basic Courses

The followings are basic units you can learn from MongoDB:

- Unit 1: Getting Started with MongoDB Atlas.
- Unit 2: Overview of MongoDB and the Document Model
- Unit 3: Connecting to a MongoDB Database
- Unit 4: MongoDB CRUD Operations: Insert and Find Documents
- Unit 5: MongoDB CRUD Operations: Replace and Delete
- Unit 6: MongoDB CRUD Operations: Modifying Query Results
- Unit 7: MongoDB Aggregation
- Unit 8: MongoDB Indexing
- Unit 9: MongoDB Atlas Search
- Unit 10: Introduction to MongoDB Data Modeling
- Unit 11: MongoDB Transactions
- Unit 12: MongoDB Compass

Driver: It works in tandem with the built-in Node.js BSON package to interact with your MongoDB

## Saving and running the application

1. Save your app.js file.
2. Run the application by running the following command in the `node-mongo-lab` directory:
   ```jsx
   node app.js
   ```
   After running the application, you should see the following output:
   ```jsx
    Connected to MongoDB
    -------------------------------------------------
    | (index) |      name      | sizeOnDisk | empty |
    |    0    | 'sample_airbnb'| 55205888   | false |
    |    1    |    'admin'     | 344064     | false |
    |    2    |    'local'     | 6696173568 | false |
    ------------------------------------------------
   ```

## Troubleshooting

Network Access Error
User Auth Errors

- Connectivity issues are common when starting out
- Connectivity issues may result from systems put in place to protect the database
- MongoDB has resources to help
- Network access tab on Atlas UI
  - Allow access from anywhere: security risks
  - Add IP address: less security risks
- Fixing a network error by adding IP address to the allow list
- Fix auth errors caused by an incorrect pass or user
- Check that your password is populated and correct
- Include correct database user on the string
