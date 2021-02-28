## State-management in React with Context and Hooks

### Get started

```
yarn && yarn start
```

This project uses a JSON-based API, using [My JSON Server](https://my-json-server.typicode.com/), which uses the file `db.json` to create a REST API. You can use GET, POST, PUT, PATCH and DELETE. But keep in mind that changes aren't persisted between calls.

### Libraries used

- [React Router 5](https://reactrouter.com/web/guides/quick-start)


### Excercises

1. Try running this application, what do you see? To display data on this page (`/`), you need to request the data from the API and put it in a local state object e.g. with `useState`.

Hint: the hotel information is available on [https://my-json-server.typicode.com/royderks/react-context-hooks-workshop/hotels](https://my-json-server.typicode.com/royderks/react-context-hooks-workshop/hotels).

2. Now the application is displaying a list of hotels, when you click on one of the hotels you'll navigate to a detail page. You need to fetch the data from an individual hotel on this page by adding one or multiple `useState` Hooks to `Detail.js`.

Hint: Use the `match` object from React Router to get the hotel id from the url.

3. Also, get the reviews for this hotel from the REST API. You can render these inside the `ReviewWrapper` component, and use the already exisiting `ReviewItem` component to display them.

Hint: Have a look at the `db.json` file to find all endpoints for the REST API.











what queries can you use? How can you get the bearer token?

Hint: The credentials are:

```json
{
  "userName": "editor@newline.co",
  "password": "fullstackgraphql"
}
```

2. The schema for our server defines fields for the type `Post`. Add the field `published` for this type and only return unpublished posts for users that are authenticated -- that is, users who pass a user token along with their query. For this you'll use resolver-based authentication.

Hint: How do you get the token in the resolvers? Remember the function `isTokenValid` from the slides?

3. Move the logic for the authentication to the context, and make sure unpublished posts are only visible to authenticated users.

4. In addition to authentication, also add role-based authorization to your GraphQL server. Create a new field called `views` in the schema that's only visible to authenticated users that have the role `ADMIN`.

The admin credentials are:

```json
{
  "userName": "admin@newline.co",
  "password": "fullstackgraphql"
}
```

Hint: Where do you get the id of the user from? How can you use this to get the users' information?

5. Besides the context or the resolvers, we can also use the schema for our authentication logic with a custom directive. Replace the existing logic to make the field `views` only visible to admin users with a custom directive.

To save you some time, the code for the directive itself is already present in the file `src/directive.js`. You need to add the validation logic there.

Hint: You can find more info here https://www.apollographql.com/docs/apollo-server/schema/directives/#using-custom-schema-directives

6. BONUS: Replace the exisiting authentication logic in `authentication.js` with Auth0. For this you can follow the steps in [this article](https://auth0.com/blog/build-and-secure-a-graphql-server-with-node-js/#Securing-a-GraphQL-Server-with-Auth0) I wrote on their blog. The token no longer needs to be created using the `loginUser` mutation, but can be retrieved from the Auth0 Dashboard.

You can use the following `.env` file for your variables:

```
AUTH0_DOMAIN=YOUR_AUTH0_DOMAIN
API_IDENTIFIER=YOUR_API_IDENTIFIER
```

Hint: You need to mock the `userId` as we haven't connected Auth0 with a database!