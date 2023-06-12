# JavaScript

<!-- #NOTE - groups all console logs together and ends on line 164 -->
console.groupEnd('examples')

JS types: 
Booleans, strings, numbers, objects
camelcasing variables

const cannot be changed as it is constant
  use if you don't want data to change

let cannot be redeclared but can be reassigned
  use let if you want data to change (add to number, etc)

<!-- var badThing = '' #NOTE - do not use var -->

let firstName = 'bailey'
const lastName = 'johnson'
firstName = 'b-dogg'

let fullName = firstName + lastName

#NOTE - log+enter types console log for you
  backticks you can use for string, used for 
string interpolation- BACKTICKS

console.log(`this is the full name: ${fullName}`);
logs: this is the full name: b-doggjohnson

let fullName = firstName + ' ' + lastName
puts space in between

<!-- strings -->

#NOTE - QUOTES:  
  -let stringWithQuotes = 'isn't this cool' doesn't work because it thinks that the apostrophe is an end quote, but you CAN use double quotes

  -let stringWithDoubleQuotes = ""I'm really smart" said Savannah" , thinks that there is string and then variable, so use backticks to put something in quotes as string.

<!-- #!SECTION
<!-- #NOTE - Boolean -->
  let isJeremyCool = false    <--this is declaring>
  let isSavannahSleepy = true
  isSavannahSleepy = false    <--this is changing>
<!-- this was already declared vv -->
  if(isSavannahSleepy){
    console.log('Someone get her some coffee')
  }

let complicatedNumber = (4 + 4) * (75 / 5)
  PMDAS - order of opperations
console.log('this is the complicated number: ' + complicatedNumber)
<!-- #SECTION -Numbers  -->

let number = 3
  number++
  <!-- ^^ adds one -->
  number + 1 
  <!-- ^^ adds, but doesn't change value -->
  number+=
  <!-- ^^runs addition but also changes value -->
  number = number + 1
  <!-- changes value -->

<!-- #NOTE -  -->
JS variables should be camelCased

<!-- #!SECTION Objects -->
#NOTE - bad
  <!-- let catName = 'Gopher'

  let catAge = 2

  let catIsHungry = true
  ^note that this is not string -->

  let isHungry = true

  let cat = { 
    name: 'Gopher', 
    age: 2
    isHungry:    'this is weird'           <---not same as above property>
    favoriteToys: {you can, {put a list,} in here, of favorite toys}
  }
  #NOTE - ^^key value pairsa (key is name, value is 'Gopher')

    console.log(isHungry): // true

    console.log(cat.isHungry): // 'this is weird'

#NOTE - objects within JS are randomized, not necessarily in order


let cat = { 
    name: 'Gopher', 
    age: 2
    isHungry:    'this is weird'           <---not same as above property>
    favoriteToys: {
      thisIsWeird: {
        thisIsCrazy: [
          'You did it!'
        ]
      }
   }
  }

  console.log(cat.favoriteToys.thisIsWeird.thisIsCrazy[0])

*SECTION - Arrays
--  *f*or collections of like things*

-let breakfastItems = ['apple', 'bagel', 'nothing', 'rices krispies']
  <!-- array of strings -->

-let numbers = [1, 2, 3, 1000000. -300, number]
^number above is a value from before

    let batThingYouShouldntDo = [
      1, 
      'SUP DOGGY, 
      {
        name: 'Dudley',
        color: 'Orange
      },
      [1, 2, 3]
      ]
  
-use same data types in your arrays!

-array methods: push, forEach, find, filter

badThingYouShouldntDo. <--dot brings up array methods>

array.length (starts at 0)

<!-- //!SECTION weird stuff -->

let nothing = null

<!-- //NOTE - undefined -->
let thing;

console.log(thing)
  return: undefined

<!-- //!SECTION functions -->
  block of code you can run as many times as needed

function sayHello() {
  console.log("Hello everybody, I'm a function and I love all of you 💕" );
}
<!-- ^^ this does nothing besides save into memory until...... it is invoked -->
sayHello()
  you can also type this into your console log

function sayHello() {
  console.log("Hello everybody, I'm a function and I love all of you 💕" );
  return 1
}

  console log hello statement, and 1

console.groupEnd()

const secretCode = ''

<button onclick="sayHello()" class="fs-1">🥑</button>
how to call function in html

#NOTE - Pseudo coding
  plain text to code:
  // get a console log of the avo emoji
  // store the avo emoji somewhere
  // console log of the emoji stored within js

variables - noun, they are things
functions - verbs, because they DO things

const secretCode = '🧀,🥯,🥓,🥑,☕'

let userInput = ' '

function selectAvocado(){
  userInput += '🥑'
  logUserInput()
}

function selectCoffee(){
  userInput += '☕'
logUserInput()
}
function selectBacon(){
  userInput += '🥓'
logUserInput()
}


<!-- clean it up later like this:  -->

function logUserInput(){
  console.log('this is the userInput: ', userInput, )
}


*NOTE - Parameters and Arguments

<!-- parameter -->
  when someone calls this function, they supply the value for the parameter

<!-- argument -->
  'this is the userInput: '  <--this is the argument>

<!-- parameter below is food -->
function selectFood(food){
  console.log('this is the food:' food);
}

selectFood('something')
this is the food: something

function selectFood(food){
  userInput += food
  logUserInput()
}

**put ID's on things in html that you want javascript to interact with
ie: <h2> this is ur code: <span id="secretCode"></span></h2>

function selectAvocado(){
  userInput += '🥑'
  logUserInput()

  document.getElementById('secretCode')
}

function selectAvocado(){
  userInput += '🥑'
  logUserInput()

  let secretCodeElem = document.getElementById('secretCode')
  console.log('secret code element:' secretCodeElement);
}

//this adds it to page as well as console log

function selectAvocado(){
  userInput += '🥑'
  logUserInput()

  let secretCodeElem = document.getElementById('secretCode')
  console.log('secret code element:' secretCodeElement);
  secretCodeElement.innerText = userInput
}

*NOTE - document.getelementbyid returns value for FIRST object with ID attribute

*NOTE - Don't reuse id's

if all functions have to do inner text/ document get element

you can add to 'selectFood' reusable function

DOM document object model js changing html