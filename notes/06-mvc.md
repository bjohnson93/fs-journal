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
  1. controller needs to be used by other parts in code (export), 
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

*NOTE - a method is a function() within a class
*NOTE - constructor is a very specifically named method than runs inside of a class. 
class House {

constructor(bedrooms, bathrooms, sqFootage){
  this.bedrooms = bedrooms
  this.bathrooms = bathrooms
  this.sqFootage = sqFootage
  }

}

const myHouse = new House(4, 3, 2500)

when you console.log()
myHouse
House {bedrooms: 4, bathrooms: 3, sqFootage: 2500}

'this' takes place of 'myHouse and otherHouse'
const myHouse = new House()
const otherHouse = new House()


**WHEN DEFINING A CLASS YOU WANT TO USE AN UPPERCASE CHARACTER** and it is singular


6/20/23 Notes

GOALS
-click dispense
-finds random gotchamon
-saves to local storage
CTRL P to go thru files

I. 
Start with Coins/Button

1. 
AppState - data store in between yellow curly braces (coins - 0) like top of js

2. 
HTML- make rows/sections for structure of where things go on page

3. 
Controller- 1st export, export class, name class what file is.
  constuctor() in curly braces followed by more {put your console log here}
  *Go to router, change controller accordingly (CoinsController), and import
button method in Controller INSIDE export, onclick goes from controller to svc

4. 
Service- 
  class CoinsService{}  <--at top>
  export coinsService = new CoinsService()  <--at bottom>

5. 
Go back to Controller and under button addCoin() oput in coinsService.addCoin()

6. 
Service
  under class> addCoin()
    { 
      Appstate.coins++
      log ('did coins go up', Appstate.coins)
      }

Next: update HTML!- draw # to page
Controller > above export/outside of CoinsController (private from user)
  function _drawCoins(){

  }

  6a. html needs ID! go set ID first
  6b. setText in html- setText(id, text)
      function _drawCoins(){
        setText('coinsCount', AppState.coins)
      }

7. Invoke Draw > Controller> addCoin function- call drawCoins()

8. Controller:
    function _drawCoins(){
        let stringOfCoins = ''

        for(let i = 0; i < AppState.coins; i++){
          stringOfCoins += '🪙'
        }

        setText('coinsCount', stringOfCoins //AppState.coins)
      }


II. 
Gachamons

  Need model for Gachamon   
Gachamon.js (new file in model.js)
1. Start with model for Gachamon- go to model and make new Gachamon.js file

  export class Gachamon {

    //add properties to this class//

    constructor(data){
      this.name = data.name
      this.rarity = data.rarity
      this.emoji = data.emoji
    }


  }

2. Go to AppState
  gachamons = [
    new Gachamon({name: 'Mikey', emoji: '', rarity: 'ultra-rare'})
    //make sure gachamon.js model is imported
  ]

3. Gachamon.js (model)
  debugger above constructor

4. AppState- make additional Gachamon

5. log Gachamons from AppState, from Controller > create Controller > GachamonsController.js
    5a. export class GachamonsController.js{

      constructor(){
        console.log('look at these dues', AppState.gachamons)
      }
    }

    oops! 
6. Register in router- pass through ARRAY of controller types
      Intellisense imports GachamonsController

7. Draw Gachamons to page
  Gachamon.js //template so it draws html out
    get GachamonSmallTemplate(){
      return `
      //html goes here//
      `
    }

8. Make template in HTML, then add to Gachamon.js page

9. Go to GachamonsController, private funct _drawGachamons(){}
getters don't need invoked (from Gachamon.js which is the model)

10. id on html, back to controller, set html > id, template

11. Invoke draw in constructor

III. 
Details on Gachamon

1. click on html > run code (onclick)
Gachamon.js, add onclick to div. app.GachamonsController.showcaseGachamon()

2. write showcaseGachamon(){} in GachamonsController IN constructor, log 1st
  back to Gachamons.js and to app.GachamonsController.showcaseGachamon('${this.name})
  add showcaseGachamon(gachamonName){
    console.log('do i work?', gachamonName)
    const gachamons = Appstate.gachamons

    const foundGachamon = gachamons.find(g => g.name == gachamonName)

    log('', foundGachamon)
  }

3. change data in AppState thru SERVICE, see consts above

4. controller- gachamonName in showcase()

-----

register listener in coins controller / constructor
  AppState.on('coins', _drawCoins)
  remove _drawCoins() from addCoin, bc it says if coins changes, update page with drawCoins

*REVIEW - 
//triggers our 'listener' (on)
  GService:
    AppState.emit('myGachamons')



------------------------------------
06/21/23

From router: views are basically different pages
router is an array of objects

a href=" #/about
  says take whatever they have in url, add this to end

your view page from router holds html

make car Model
  constructor take in data

generateId()

move html to car.js/carview.js

new Date()
  encapsulates date and time incl milliseconds
appstate doesn't include list date or id as it isn't in form

log from controller

Date.prototype.toLocaleString()// this.listingDate.toLocaleString()

Bootstrap collapse to hide form

 TERNARY OPERATOR

.on, emit

remove from array with splice

update local storage saveCars()