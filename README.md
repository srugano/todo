# ToDo App in `Go`

[![N|Solid](https://cldup.com/dTxpPi9lDf.thumb.png)](https://nodesource.com/products/nsolid)

[![Build Status](https://travis-ci.org/joemccann/dillinger.svg?branch=master)](https://travis-ci.org/joemccann/dillinger)

A full example of how to write a Go web application without using a web framework.

  - `api` (api controllers)
  - `app` (business logic)
  - `cmd` (command line methods)
  - `db` (database operations)
  - `models` (database models)

# Configurations!

  - For application **configuration**, we will use a package called viper which can be used in accordance with The [Twelve-Factor App guidelines](https://12factor.net/config). `Viper` allows for configuration with a config file or with environment variables.
  - **API Layer** : This is a lightweight interface to our business logic. When a client interacts with our application, it will do so through an API. Common interfaces are GraphQL, gRPC, and REST. This layer should contain minimal (if any) application logic. This layer is only responsible for translating the data returned from the business logic layer into a consumable format for clients.
  - **Business logic layer** : We may want to validate a couple of things; for example, the provided TODO text isn't too long & the user hasn't hit their daily limit. All this validation logic should be handled in the business layer. Authorization & authentication are also handled in this layer. This means determining who the current user is when a request is sent to your server (authentication). This determination can be handled in many different ways, ranging from cookies to authentication tokens. Any authorization logic surrounding who has access to what, should be handled in this layer; authorization errors that happen should be handled appropriately in your API layer. Concretely, this means that when an error is thrown or returned in a method here, your API should catch it and return a 403 or 401 error.
  - **Persistence Layer** : This is where data is persisted to a database or other store ("database" from here on). After a request has been authorized and/or validated we need to make some request to our database. Generally, there are four common operations we make to a database, they are commonly referred to as CRUD: Create Read Update Delete. Most databases support these operations in one or many forms. In this layer, our business logic layer makes these requests to our database. The only thing this layer should be responsible for is database operations; there shouldn't be any business logic. 
  - 
# Application structure

There are a few important concepts to understand: Application state and Request state. Application state is our global application state that is loaded once when starting our server. Request state is created whenever a request is made to our server. We will use the term "context" as a name for this per request context (or state). Here is a short list of what is contained in each level:

### Application

- Config (global application config)
- Store (a connection to our database)
- Cache (any caching connection)
- 
### Context

- App (a reference to the global application)
- Store (a reference to our database connection)
- User (a user, if any)
- AccessToken (the user's access token, if any)
- Logger (the logger to use within our context methods, this will have some fields like request_id preset)

### API

- App (a reference to the global application)
- Config (api configuration)
- Logger (the logger to use within api requests) 


### Installation

#### Building for source
For production release:
```sh
$ go build -o todos .
```


Verify the deployment by navigating to your server address in your preferred browser.

```sh
$ ./todo serve
127.0.0.1:9092
```

#### Kubernetes + Google Cloud

See [KUBERNETES.md](https://github.com/joemccann/dillinger/blob/master/KUBERNETES.md)


### Todos

 - Write MORE Tests
 - Add Night Mode

License
----

MIT


**Free Software, Hell Yeah!**

[//]: # (These are reference links used in the body of this note and get stripped out when the markdown processor does its job. There is no need to format nicely because it shouldn't be seen. Thanks SO - http://stackoverflow.com/questions/4823468/store-comments-in-markdown-syntax)


   [todo]: <https://github.com/srugano/todo>
