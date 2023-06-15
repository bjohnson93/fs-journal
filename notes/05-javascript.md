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

**Section Arrays**
let cats = [
  {
    name: 'Gopher',
    age: 2,
    hasTail: true,
    favoriteToys: ['mouse']
  },
  {
    name: 'Iron Man',
    age: 3,
    hasTail: true,
    favoriteToys: ['shoe lace', 'tube', 'laser pointer']
  },
  {
    name: 'Frankie',
    age: 5,
    hasTail: true,
    favoriteToys: ['cheese', 'laser pointer']
  },
]

**#!SECTION for loops**
// for loop to work through array
// run once and pull out gopher, if i is less than one, and increment by 1, or i +=3 jumps ahead

for (let i = 0; i < 1; i++) {

}

// middle portion is the condition, third (i++) is the initializer

console.log('cats length', cats.length)
//length is the actual length (3), although it goes 0, 1, 2
//less than the array.length because the length will always be one more than the last index of the array

**NOTE - for (let i = 0; i < cats.length; i++) {
  let cat = cats[i]
  console.log('🐈', cat)
}

**NOTE - //to grab just the name:
for (let i = 0; i < cats.length; i++) {
  let cat = cats[i]
  console.log('🐈', cat.name)
}
**NOTE - //this is a function called forEach
// => is called a Landa
//make sure semicolon is removed after console.log();
cats.forEach(cat => console.log('🐈 for each!', cat))


**NOTE - //if cats name is gopher set foundCat to that value
//Finds: returns FIRST thing that it finds and then it stops running function
let foundCat = cats.find(cat => cat.name == 'Gopher')

  console.log('🐈 found cat: ', foundCat);

Find is good for the UNIQUE property, not for anything shared.

things in array will have an id which are completely unique

**NOTE - filter function to target cats with tails true only
//makes brand new array with hasTail == true only
  let filteredCats = cats.filter(cat => cat.hasTail == true)
  console.log('filter', filteredCats)
//didn't replace or destory former array, but made copy with only tails

//to target cats older than four and less than 10
  let filteredCats = cats.filter(cat => cat.age > 4 && cat.age < 10)
  console.log('filter', filteredCats)

**NOTE - sort
//sorted by age
//sort takes in comparing function, compares 2 things in array at a time
//subtracts cat 1 and cat 2 age, whichever is 0/-1/-2
let sortedCats = cats.sort((cat1, cat2) => cat1.age - cat2.age)

  console.log('sort', sortedCats)

for and forEach do the same thing

  console.group() at top of screen
  console.groupEnd() collapses every console between

**NOTE - another array method - map
  let numbers = [1, 2, 3, 4]

run thru array and change value
.map
(for each number in this array, id like to multiply by two)

  let changedNumbers = numbers.map(numbers => number*2)

  console.log('changed', changedNumbers);

  output: 2, 4, 6, 8

Primitive types: numbers, booleans

Reference types: arrays, objects

find something random in array:
    function makeAMurderer() {
      let randomNumber = Math.random()
      console.log('random', randomNumber);
    }
find something random in array:
    function makeAMurderer() {
      let randomNumber = Math.floor(Math.random() * 10)
      console.log('random', randomNumber);
    }
//math.floor gives whole numbers
find something random in array:
    function makeAMurderer() {
      let randomNumber = Math.floor(Math.random() * animals.length)
      console.log('random', randomNumber);
    }
//accesses array
    function makeAMurderer() {
      let randomNumber = Math.floor(Math.random() * animals.length)
      console.log('random number', randomNumber);
      let randomAnimal = animals[randomNumber]
      console.log('random animal', randomAnimal);
    }
//single = reassigns
**NOTE - math equation to remember below
    function makeAMurderer() {
      let randomNumber = Math.floor(Math.random() * animals.length)
      console.log('random number', randomNumber);
      let randomAnimal = animals[randomNumber]
      console.log('random animal', randomAnimal);
      randomAnimal.guilty = true
    }
//accesses array
    makeAMurderer()

button onclick to access js; draw; write filter array 

bang operator: !animal.mammal means mammal property is false

filter method animal.diet.includes('') to access inner array

<!-- 6/14/23 Notes -->
