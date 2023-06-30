# Understanding Asynchronous Code, and API's
01. What is the difference between `asynchronous` code and `synchronous` code?

  > | With synchronous code, you wait for it to complete before moving onto the next task. With asynchronous, you can move onto another task before the first one finishes. This can help a lot with creating better user experience. Synchronous is more dependent, asynchronous is independent. |

02. What is an event listener?

  > | AppState.on 'listens' from the controller for any changes that could be made to the global variables that are stored in the AppState, to update to the view. These changes can be 'emitted' from the Service, which the listener picks up. |

03. What does *REST* stand for, and in simple terms what does it mean??

  > | REpresentational State Transfer- the framework of an API that allows specific exchanging of information for the user to get from the server. There will be very specific data, anything the api requires will need to be obtained/provided from the user as well. Think model and the specifics of objects/classes. |

04. What is a callback / higher order function?

  > | A callback function is a function passed as an argument into another function, which can run after another function has finished. They make sure a function is not going to run before a task is completed, but will run after that task.  |

05. What is a `promise`? How do you capture an error from a `promise`?

  > | A promise is an object that is used to obtain data from the server, it is pending until it is either rejected (think catch.error) or resolved. |

06. Name three processes used to make requests over `HTTP`?

  > | Think CRUD- get-retrieve data from server, put- or 'edit' info to the server(replaces), post-sends data to server(like posting new gifs on site), delete- deletes data on server! (Crud is Create, Read, Update, Delete) |

07. What does the `API` acronym stand for?

  > | Application Programming Interface. How we pull data out from server, getting data to user's computer, with limited info that is appropriate for user. API does the checks to make bring user requests to server, then makes sure given info is allowed back to user. (Think waiter in restaurant for customer(user)/chef(server)) |

08. What must you do in order to `await` a promise inside of a function?

  > | You must resolve the promise before you can run the function that follows await. If the promise is rejected, then you don't proceed onto the await part of the function. |

09. What is the purpose of encapsulation in programming?

  > | To hide or protect certain types of data or functions (think service layer and appstate) from a user. It allows a program to run more efficiently also. It helps keep things simple for the user and allows the right amount of access to state values. |

10. What is `HTTP` response code for a successful request?

  > | 200! The big nose cat. It means 'ok'. |

11. What is a 400 error?

  > | Invalid request- for example, if the model you put in data.id instead of data._id, and the server is expecting ._id, this would throw a 400 error. Or if it was expecting a different data type. |
