# Application Architecture, MVC Design Pattern
01. What are the Pillars of Object Oriented Programming (`OOP`)?
  
  > | Encapsulation and message passing- to hide and protect information, and to transfer needed data/data changes behind the seens to protect the user/their information, as well as organization of code. This makes it easier to change details later or to put new details in. |

02. How does `export` differ from `export default`?
  
  > | Export default is for a single value, while export can be for multiple values. |

03. What is Encapsulation?
  
  > | Encapsulation basically hides and protects your data. This helps with security and overall functionality, as it provides organization needed in some areas, and hides the data you want to remain hidden in others. |

04. What are some of the benefits of the `Proxy` object that we are using in our structure for applications?
  
  > | It allows you to create on object in place of another object- which gives you more control over the interaction of the original object.  |

05. What the difference between a `class` and an instance of a `class`?
  
  > | Your class is your 'blueprint' or template of what your object may be, while your instance of a class is the object itself.  |

06. What is a computed Property?
  
  > | Computed properties allow you to use the values of expressions as property names on an object. Ie the property following a 'getter'. They're used you want to use a value as a property name. |

07. What is the purpose of the `MVC` pattern?
  
  > | To keep information separated from what the users sees, how things work, what values are stored, etc. |

08. What is the job of the `Controller` in the `MVC` Pattern?
  
  > | The controller is kind the middle man- it reports back and forth to what the user sees/interacts with, and then notifies the model of changes that need to be made, which is why the function might begin in the controller, but the logic of the function is in the service. |

09. What is the job of the `Service` in `MVC`?
  
  > | The Service contains the business logic- like what complex changes that need to be made to manipulate the information in the model. |

10. What is the job of the `Model` in `MVC`?
  
  > | Your data structure goes in your model. This might be where you retrieve info from the database (like where you have this.name = data.name, etc) as well as your templates that have string interpolation that gets put into the dom. |
