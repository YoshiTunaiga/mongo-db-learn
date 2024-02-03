# Basic Lessons

- Lesson 01: Introduction to Data Modeling
- Lesson 02: Types of Data Relationships
- Lesson 03: Modeling Data Relationships
- Lesson 04: Embedding Data in Documents
- Lesson 05: Referencing Data in Documents
- Lesson 06: Scaling a Data Model
- Lesson 07: Using Atlas Tools for Schema Help


## Lesson 01: Introduction to Data Modeling

- Defining how data is stored is one function of data modeling. Data modeling helps you use your data effectively to meet information needs.
- Defining the relationships that exist among different entities in your data is one function of data modeling.
- Data modeling enables you to document data requirements for applications and identify errors in development plans before any code is written.

## Lesson 02: Types of Data Relationships

- A one-to-one relationship is one of the most common types of relationships found in a database.
- One-to-one is a relationship where a data entity in one set is connected to exactly one data entity in another set.
- A one-to-many relationship is one of the most common types of relationships found in a database.
- One-to-many is a relationship where a data entity in one set is connected to any number of data entities in another set.
- A many-to-many relationship is one of the most common types of relationships found in a database.
- Many-to-many is a relationship where any number of data entities in one set are connected to any number of data entities in another set.
- Embedding the phone numbers as a subdocument can improve the schema, and it ensures that data that is accessed together is stored together.

## Lesson 03: Modeling Data Relationships

- This is a common way to model a one-to-many relationship with document references. Embedding the customer's information document inside each transaction document would lead to repetition of the customer's information. To avoid repetition of customer information, use references and keep the customer information in a separate collection from the transactions collection.
- This is a common way to model a one-to-many relationship with embedded documents. Embedding connected data in a single document can reduce the number of read operations that are required to obtain data. You should structure your schema so that your application receives all of its required information in a single operation. If your application frequently retrieves the transaction data with the customer's information, you should consider embedding so that your application doesn't need to issue multiple queries to resolve the references. Remember that the maximum size of a document is 16 MB.

## Lesson 04: Embedding Data in Documents

- Embedding data simplifies queries because it avoids application joins. It fulfills the principle that data that is accessed together should be stored together.
- Embedding data provides better performance for read operations. Embedded documents enable you to store all kinds of related information in a single document.

## Lesson 05: Referencing Data in Documents

- **References**: Saves the _id field of one document in another document as a link between the two.
    - They are simple and sufficient.
    - Using references is called linking or data normalization: References save the `_id` field of one document in another document as a link between the two.
    - Avoids duplication of data: Referencing allows you to store data in two different collections and ensure that the collections are related. This avoids duplication of data.
    - Smaller documents: Referencing avoids duplication of data and, in most cases, results in smaller documents.
    - Con: With references we have to query from multiple documents that cost extra resources and impact read performance
    
    [IMAGE ONE][IMAGE TWO]

## Lesson 06: Scaling a Data Model

Data that is accessed together should be stored together for the following: 

- Optimum efficiency of:
    - Query result times
    - Memory usage
    - CPU usage
    - Storage

When creating data models, avoid unbounded documents that are documents that grow infinitely (when using document embedding)

- Embedding data will make the document larger and impact write performance. As more data is added to each document, the entire document is rewritten into MongoDB data storage.
- Unbounded documents caused by embedding will eventually run into storage problems by exceeding the maximum document size of 16 MB.

[IMAGE THREE]

Problems as the array grows larger:

- It will take up more space in memory
- May impact write performance
- Difficult to perform pagination of comments
- A max document size of 16MG will lead to storage problems. (Avoid)

One benefit is the ability to retrieve all comments in a single read

To prevent unbounded document sizes that may result from embedding, you can break up your data into multiple collections and use references to keep frequently accessed data together. 

For example: 
[IMAGE FOUR]

Data that is accessed together should be stored together. How you model your data depends entirely on your particular application's data access patterns. You want to structure your data to match the ways that your application queries and updates it.

## Lesson 07: Using Atlas Tools for Schema Help

### Schema anti-patterns

- Schema design patterns are guidelines that help developers plan, organize, and model data
- The results of schema anti-patterns are :
    - Sub-optimal performance
    - Non-scalable solutions
- The common schema anti-patterns include:
    - Massive arrays
    - Massive number of collections
    - Bloated documents
    - Unnecessary indexes
    - Queries without indexes
    - Data that’s accessed together, but stored in different collections

### Data Explorer

It can help us with Indexes that are not necessary and Schema anti-patterns within the collection

[IMAGE FIVE][IMAGE SIX]

### Performance Advisor

It can tell us which indexes are not necessary, how to improve the schema, and other recommendations that can help with the data and improve the performance on the most active collections.

[IMAGE EIGHT]

### Conclusion

- Atlas allows us to identify and address schema design anti-patterns.
- Data Explorer shows schema anti-patterns and collection and index stats for each collection.
- Performance Advisor: Analyzes the most active collections and recommends schema improvements.
- The Schema Anti-Patterns tab highlights any issues in the collection and provides details to resolve them. You can improve your schema by resolving the anti-patterns that are shown.
- The Performance Advisor tool is available in M10+ cluster tiers.
- Embedded documents store related data in a single document
- Reference relationships store data by linking references in one document to another document
