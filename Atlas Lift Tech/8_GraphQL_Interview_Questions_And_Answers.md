### GraphQL Interview Questions and Answers:

1. **What is GraphQL and how does it differ from REST?**
   - **Answer:** GraphQL is a query language for APIs and a runtime for executing those queries by using a type system you define for your data. Unlike REST, which has multiple endpoints for different resources, GraphQL uses a single endpoint and allows clients to specify exactly what data they need, reducing over-fetching and under-fetching of data.

2. **Explain the main components of a GraphQL schema.**
   - **Answer:** The main components of a GraphQL schema include:
     - **Types:** Define the shape of data.
     - **Queries:** Read-only operations to fetch data.
     - **Mutations:** Operations to modify data.
     - **Resolvers:** Functions that populate the data for fields in the schema.
     - **Schemas:** Define the structure and entry points for the API, combining types, queries, and mutations.

3. **What are queries and mutations in GraphQL?**
   - **Answer:** 
     - **Queries:** Used to fetch data from the server.
       ```graphql
       query {
         user(id: "1") {
           name
           email
         }
       }
       ```
     - **Mutations:** Used to modify data on the server.
       ```graphql
       mutation {
         createUser(input: {name: "John", email: "john@example.com"}) {
           id
           name
         }
       }
       ```

4. **How do you handle authentication and authorization in GraphQL?**
   - **Answer:** Authentication and authorization are handled by integrating middleware that checks for authentication tokens (e.g., JWT) and user permissions before executing resolvers. This can be done using context in GraphQL to pass user information to resolvers.

5. **What is the purpose of resolvers in GraphQL?**
   - **Answer:** Resolvers are functions that are responsible for fetching the data for a specific field in the GraphQL schema. They execute the logic required to fetch the data from a database or another API.

6. **How do you handle errors in GraphQL?**
   - **Answer:** Errors in GraphQL are handled by returning error objects in the response, along with the data. This can include validation errors, authentication failures, and server-side exceptions.
     ```json
     {
       "data": null,
       "errors": [
         {
           "message": "User not found",
           "locations": [{ "line": 2, "column": 3 }],
           "path": ["user"]
         }
       ]
     }
     ```

7. **Explain the concept of subscriptions in GraphQL.**
   - **Answer:** Subscriptions in GraphQL are used for real-time updates. They allow clients to subscribe to specific events and receive data updates when those events occur. They typically use WebSockets for communication.
     ```graphql
     subscription {
       userAdded {
         id
         name
       }
     }
     ```

8. **How do you design a GraphQL schema?**
   - **Answer:** Designing a GraphQL schema involves:
     - Identifying the types and relationships in your data.
     - Defining the queries and mutations that clients will need.
     - Creating the type definitions, query, and mutation types.
     - Implementing resolvers for each field.
     - Ensuring the schema is intuitive and follows best practices for clarity and maintainability.

9. **What are fragments in GraphQL and how are they used?**
   - **Answer:** Fragments in GraphQL are reusable units that can be used to share common fields between multiple queries. They help reduce duplication and improve maintainability.
     ```graphql
     fragment userFields on User {
       id
       name
       email
     }

     query {
       user(id: "1") {
         ...userFields
       }
       anotherUser(id: "2") {
         ...userFields
       }
     }
     ```

10. **How do you handle versioning in GraphQL?**
    - **Answer:** Versioning in GraphQL is often handled by deprecating fields and providing clear documentation on their replacements. Instead of creating multiple versions of the API, you evolve the schema and indicate deprecated fields.
      ```graphql
      type User {
        id: ID!
        name: String!
        email: String! @deprecated(reason: "Use 'contactEmail' instead")
        contactEmail: String!
      }
      ```

11. **What are directives in GraphQL?**
    - **Answer:** Directives are used to modify the behavior of fields or types in a schema. Common built-in directives include `@include`, `@skip`, and `@deprecated`.
      ```graphql
      query getUser($withEmail: Boolean!) {
        user(id: "1") {
          id
          name
          email @include(if: $withEmail)
        }
      }
      ```

12. **How do you optimize performance in GraphQL?**
    - **Answer:** Performance optimization in GraphQL can involve:
      - Efficient data fetching with batching and caching.
      - Using DataLoader to batch and cache database or API calls.
      - Optimizing resolver functions.
      - Limiting query complexity and depth to prevent expensive queries.

13. **Explain the concept of introspection in GraphQL.**
    - **Answer:** Introspection is a feature in GraphQL that allows clients to query the schema for information about the types, queries, and mutations it supports. This is useful for tools and IDEs to provide autocomplete and validation.
      ```graphql
      {
        __schema {
          types {
            name
          }
        }
      }
      ```

14. **What is the difference between scalar types and custom types in GraphQL?**
    - **Answer:** 
      - **Scalar Types:** Built-in types like `Int`, `Float`, `String`, `Boolean`, and `ID` used for primitive data.
      - **Custom Types:** User-defined types that combine multiple fields, such as objects, enums, and unions.
      ```graphql
      type User {
        id: ID!
        name: String!
        age: Int
      }
      ```

15. **How do you implement pagination in GraphQL?**
    - **Answer:** Pagination in GraphQL can be implemented using two common approaches:
      - **Offset-based pagination:**
        ```graphql
        query {
          users(offset: 0, limit: 10) {
            id
            name
          }
        }
        ```
      - **Cursor-based pagination:**
        ```graphql
        query {
          users(first: 10, after: "cursor") {
            edges {
              node {
                id
                name
              }
              cursor
            }
            pageInfo {
              hasNextPage
              endCursor
            }
          }
        }
        ```

16. **What are the best practices for securing a GraphQL API?**
    - **Answer:** Best practices for securing a GraphQL API include:
      - Validating and sanitizing inputs to prevent injection attacks.
      - Implementing robust authentication and authorization mechanisms.
      - Limiting query complexity and depth to prevent DoS attacks.
      - Using HTTPS to encrypt data in transit.
      - Regularly auditing and updating dependencies.

17. **How do you implement data fetching in GraphQL?**
    - **Answer:** Data fetching in GraphQL is implemented using resolvers. Resolvers are functions that return the data for a field. They can fetch data from databases, APIs, or other sources.
      ```javascript
      const resolvers = {
        Query: {
          user: (parent, args, context, info) => {
            return context.db.findUserById(args.id);
          }
        }
      };
      ```

18. **What is the purpose of the `GraphQLObjectType` in a schema?**
    - **Answer:** `GraphQLObjectType` is used to define the shape of objects in the schema. It specifies the fields and their types for a particular object type.
      ```javascript
      const UserType = new GraphQLObjectType({
        name: 'User',
        fields: {
          id: { type: GraphQLID },
          name: { type: GraphQLString },
          email: { type: GraphQLString }
        }
      });
      ```

19. **How do you handle file uploads in GraphQL?**
    - **Answer:** File uploads in GraphQL are typically handled using multipart requests. Libraries like `graphql-upload` can be used to process file uploads.
      ```javascript
      const { GraphQLUpload } = require('graphql-upload');

      const resolvers = {
        Upload: GraphQLUpload,
        Mutation: {
          uploadFile: async (parent, { file }) => {
            const { createReadStream, filename } = await file;
            const stream = createReadStream();
            // Save the file or process it
          }
        }
      };
      ```

20. **What are the differences between GraphQL and SQL?**
    - **Answer:** 
      - **GraphQL:** A query language for APIs focused on retrieving and manipulating data from different sources. It allows clients to specify exactly what data they need.
      - **SQL:** A query language for relational databases focused on defining and manipulating structured data within a database. SQL operations include querying, updating, and managing relational data.