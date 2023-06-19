# MVC

Model View Controller
controllers give access to users for our websites

#SECTION - 1. This creates folder
IN CMD:
bcw client in cmd
cd source, codeworks
NO MKDIR
bcw create
  what project: mvc this week
  project name: 
  initialize git rep: n for no
    cd into folder, code .

#!SECTION 2. Open in VS code
many folders, many files!!!

open index html
no link to bootstrap in html, but scss has bootstrap
module- js is broken up into smaller modules,

'follow the bouncing ball' how mvc works
**Never have to come into app.js and change anything**

  Classes
  Constructors
  new / to build out classes/fancy object

encapsulate so people can't access our private data

  extends- inheritance
**REVIEW - AppState File- this is where we store all of our global variables, inside ObservableAppState, inside the curly boys

**Section** import/export; 
export test file
  export const catSound = 'meow'
import test file
  let catNoise = catSound ./ExportTest <--intellisense> will add import from ExportTest file
*NOTE - Let autocomplete complete import statements for you!
  import must have .js or you'll get 404

**NOTE - classes- a class is a big fancy object; you get really good intellisense when you write what they do. they can store variables within the class itself as well as functions, you can export out entire classes to diff pieces of project.

Method is a function written inside an object. all methods are functions but not all functions are methods.

View(index.html) onclick get sent to controller

Service says appState is going to have properties changed on it
  service for every data type- cheese controller, cheese service that controls appstate to manipulate cheese

  another file for upgrades

Service is the *singleton*

State management system- controller is going to talk to service
  models stored in AppState; cheese = 0 stored here.

Controller updates our HTML

Encapsulated to keep data safe!

Register controllers in router to be used from HTML ( the view )

Constructor- when new home-controller, it runs code inside constructor; similar to calling functions at the bottom of JS sheet

*new class within JS is capitalized

3. PlayersController.js new folder in controllers
  1. controller needs to be user by other parts in code (export), 
  2. data type class; export class PlayersController {}
  3. console.log controllers name, reg w/app.js: PlayersController {constructor() {
    console.log('Players controller loaded')
  } }
  //NOTE - first step ALWAYS this week!!!!!
  4. register controller in router- controller: PlayersController
  5. go to PlayersController for button- write method under PlayersController: (under constructor) //NOTE - public methods accessible to the user.:
  sayHello(){
    console.log('Hello Jeremy, ur button works')
    console.log('Good job testing small')
    //app.PlayersController.sayHello()//
  }

  Ctrl+P for file searcher

  6. need button- go to index.html- button- 'do the thing', onclick="app.PlayersController.sayHello()"
  7. Test console log/button!!!!
  8. Models > Value.js
  9. Create new- Player.js 
  export class Player {
    constructor(name){
      this.score = 0
      this.name = name
    }
  }
  10. Set property on AppState. 
  players = [
    new Player()
  ]
  11. Never imported! ctrl+. ./models/Player.js
  12. players = [
    new Player('Jeremy')
  ]
  13. Go inside player model(declared in player.js), put in a debugger after constructor(name) line. Have console open. Step over.
  **Remove debugger after you're done with it**
  14. Go into AppState:
  players = [
    new Player('Jeremy'),
    new Player('Miles')
  ]
  15. want to add image? add another parameter in parens! constructor (name, imageUrl) {this.imgUrl = imageUrl}
  //build out constructors/data in AppState
  new Player('Jeremy', 'url goes here')
  16. from PlayersCtonroller.js console.log(AppState.players)
  <!-- new Player('Jeremy') -->
  17. Show players on page load- ABOVE PlayerControllers.js constructor- function _drawPlayers(){}  <--underscore for functions that are PRIVATE. console.log(), call _drawPlayers() under constructor. ONLY runs once >
  18. Each player class you can store methods/functions from appstate. under player.js
  //getters must return a value
  //getters do not take in any parameters
  get PlayerDetails(){
    let details = `Hello, my name is${this.name} and my score is ${this.score}`
    return details
    
    return 
  }

  PlayersController.js- function drawPLayers(){
    let players = AppState.players

    console.log(players[0].PlayerDetails)
  }
  this// property on the same object
  19. Player.js
  get PlayerCardTemplate(){
    return /*html*/`
    *paste in template from html here* 
    `
  }
  20. PlayerController.js
  utility functions under utils folder- within _drawPlayers function
  setHTML('players', players[0].PlayerDetails)
  21. Put ID in row in html 'players'

function _drawPlayers(){
  let players = 
  let template = ''
  players.forEach(player => template += PlayerCardTemplate)
  setHTML('players', players[0].PlayerCardTemplate + players[1].PlayerCardTemplate)
}
22. css- assets/ style/ style.css
.player-img{
  max-height: 30vh;
}
add class to the right js (player.js)
**REVIEW - 
23. PlayersService.js in service file
new Class //not export
  class PlayersService(){
  //NOTE - services do not generally have a constructor
  }

  export const playersService = new PlayersService()
  //EVERY SERVICE WILL LOOK LIKE THIS**REVIEW - 

  //NOTE - SINGLETON

  -------------------------

  class PlayersService(){

  }

  export const playersService = new PlayersService()
  24. 
  button onclick="app.PlayersController.increasePlayerScore()"
//inside export   -- PlayersController:
  increasePlayerScore(){
    console.log('button clicked');
  playersService(//hit tab).increasePlayerScore()   *REVIEW - ((hold ctrl + ., ctrl + click takes to player svc))
    const players = AppState.players
  }


your controller gets registered in router
first object w/path nothing