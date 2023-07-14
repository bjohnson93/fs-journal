# Intro to Server side concerns with JavaScript
01. What do the letters of the acronym `CRUD` stand for?

  > | CRUD stands for Create, Read, Update and Delete! |

02. Each action that `CRUD` represents maps to an HTTP request. What HTTP request does each `CRUD` action correspond to?

  > | Create corresponds with Post, Read corresponds with Get, Update corresponds with Put, and Delete corresponds with Delete. |

03. What does `ORM` stand for? Which `ORM` do we use when interacting with MongoDB

  > | Object-Relational Mapping- maps data into objects, essentially. Mongoose is what is used with MongoDB |

04. Which two `HTTP` request types include a body?

  > | Post request and Get |

05. In a/an _asynchronous_ coding model, when you call a function, it returns only when the action has finished and stops your program for the time the action takes. Likewise in a/an _synchronous_ coding model, multiple things are allowed to happen at one time. When you perform an action, your program continues to run.  Fill in the blanks.

  > | Asynchronous, then Synchronous. |

06. What are the three types of data relationships? Provide an example of each.

  > | One to one relationships: One author has one address, or One teacher has one classroom. One to Many: One blog could have many comments, but those comments are only particular to that specific blog, or One teacher has many students. Many to Many: Book written by many authors AND an author writing many books, or Many students have many friends.|

07. What is middleware?

  > | Software that different applications use to communicate with each other... ie, the middle man! I believe Auth0, MongoDB, and Postman would be considered middleware. Possibly Salesforce also? |

08. The ______ pipeline delivers information from the client while the ______ pipeline returns it. Fill in the blanks. 

  > | Continuous Integration; Continuous Deployments |

09. Demonstrate the pattern that is used to include a request query with the client's `HTTP` request providing the property `tag` and the value `winter`.

  > | RESTful conventions req.tag.winter |

10. What is a ***virtual property***?

  > | Virtual properties are additional properties for a given model that are NOT stored in MongoDB. You can have your properties stored in MongoDb, and then have a combination one (for example for this week we wrote them below our model properties). For example, firstName, lastName of a 'person' may be properties in model that are stored in MongoDb- which are STATIC. A virtual could be the fullName where we combine person.firstName + person.lastName to create fullName. |
