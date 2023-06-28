# Async

Any request made to API will be an ASYNCHRONOUS request

Crud Routes

  Create -  post
  Read -  get
  Update -  edit-> put
  Delete - Destroy/delete

Mick:
  create model, create place in appstate to store, create controller for update to page
Jeremy API:
  start controller, service to make request to get info for model

    1. Make MonstersController
      export class "
      constructor w/console log

      try/catch: if you make mistake in try, it stops running code in try and goes to catch which has the error (throw error/catch error)

      write function (method) in controller- to GET DATA from somewhere- 
       getMonsters(name) {
        try {
          if(!name) {
            throw new Error("No name supplied")
          }
          Pop.success(`${name} was supplied`)
        } catch (error) {
          console.error(error)
          Pop.error(error.message)
        }
       }

       this.getMonsters() in constructor

    2. Make MonstersService
      class MonstersService

      export const monstersService = new MonstersService()

          *controller in try: monsterService.getMonsters()
                              Pop.success('we got the monsters')

        if anything goes wrong in try in controller, error would print to console

        Service: getMonsters(){
          //fetch allows us to make request to apis
          const response = fetch('url goes here')
          //above takes a bit of time
        }

        
          Service: async getMonsters(){
            *NOTE - the hard way
            //fetch allows us to make request to apis
            const response = await fetch('url goes here')
            //above takes a bit of time
            const jsonData = await.response.json()
          }
          *NOTE - AXIOS BASICALLY DOES ABOVE FOR US!!!!

          bottom of html w/js
          script tag for axios import

          //make instance of axios
      *REVIEW - 
          AxiosService
            export const zeldaApi = axios.create({
              baseURL: 'generic url goes here',
              timeout: 8000,
                //if request takes longer than 8 seconds, throw an error
              
            })

            class MonstersService{
              async getMonsters(){

                *NOTE - AWAIT! see below
                const response = await zeldaApi.get()
                log('got monsters', response)
              }
            }

          Network tab, select fetch/xhr, headers
          200 is good, white is good

        controller: async getMonsters and await monstersService.getMonsters()

        request to async and try/catch in controller,
        and async in service

        **REVIEW - 
          ALWAYS LOG RESPONSE AND LOOK AT DATA!!!!!!!!
          const response = await zeldaApi.get('category/monsters') //this reruns url for only monsters
          // *NOTE - axios always returns the part of request that we care about under data key
          clog('got monsters', response.data)

        *NOTE - got to models and make a class model- /Monster.js
          export class Monster{
            constructor(data){

            }
          }

          const monsterData = (paste copied index from object in console log)

          in constructor: 
          this.commonLocations = data.common_locations // so its not snake case
          this.description = data.description
          this.drops = data.drops
          this.id = data.id
          this.imgUrl = data.image
          this.name = data.name


          map array method can turn array of Pojos into array of monsters
          SERVICE:
            const arrayOfMonsters = response.data.data.map(monsterPojo => new Monster (monsterPojo))
                //how can we look through monsterPojo, ma eka  new monster with the monsterPojo

          save to appstate, bc server never calls draw
          Appstate.monster = arrayOfMonsters

          see drawFunction in service
          we need listeners for draw function, bc we don't have monster in appstate yet besides empty array
          Appstate.on('monsters', _drawMonsters) <--in service controller at bottom>

          make template for monsters to draw to- in index html
            bootstrap card class

            put col w/card in monster model

            get cardtemplate return 

            draw monsters in controllers, for each over monsters 
            set html('monsters', template)

            TODAY: questions controller!
            axios script tag, 
            axios instance

            buttons for diff questions



6/27/23 Notes

MVC Auth Auth-0

1. Auth-0 differences: html has more info- 'authstate'  todo to remove auth template once verified, lots of script tags. Axios tag in there already, as well as cdn for auth-0

2. views > env.js....... OK to copy and paste Jeremy's

3. Axios service is already set up- lots of code in there. env.js is where the url goes now.

4. CRUD Create- the car objects w/make, model, year, etc. BCW sandbox (check slack for url) base url before api/jobs

5. Don't change const 'api' in the axios service

6. Spin up local host

7. Build controller, see if request to api successful, console log.

8. Router- h1 welcome to Gregslist, and add the controller in another object in router (keep other controllers). Change path to cars to test log.

9. Add cars page to nav bar in html

10. method/function in controller- async getCars(){try await {carsService.js}/catch(error){ console.error(error); Pop.error(error.message)}}  (read in crud, bc its getting data from api / get)
  *TODO - Crud routes
    *REVIEW - create
    *REVIEW - read
    *REVIEW - update
    *REVIEW - delete

11. cars service- async getCars(){const res = await api.get('api/cars');<--end of url(from axios)// log 'got cars', res.data}
(res is response)

12. this.getCars in controller constructor!

13. check network preview- make sure you have your cars/objects; array should also be in console

14. go make a car model! car.js- export class Car{ constructor(data){}}; let carData = { *paste from console }; id is handy *no need to store id and _id

15. Turn car pojos into car class objects. go put this.id = data.id etc in constructor in car.js. Keep creatorId; dates: this.createdAt = new Date(data.createdAt); _v isn't needed. creator object: this.creator = data.creator; 
    IF YOU WANTED TO, you could do this.creator = {}, then this.creator.name = date.name. Then you can comment out whole thing of let carData.

16. AppState cars = [] (make sure it was an array you got!) and then steal intellisense line (@type import)

17. *NOTE - Turn pojos into car model!!! CarsService: Map. async getCars() { //; //; const builtCars =  res.data.map(carPojo => new Car(carPojo))  //store in appstate// AppState.cars = builtCars} *you didn't need to drill into anything in console. console log was just an array.
    always log res.data when getting from axios

18. CarsController- set up listener. AppState.on('cars', _drawCars), then create _drawCars function above. let cars=AppState.cars; log ('here are cars', cars)

19. index.html: routerview: .container-fluid > .row > .col-12 > h1 'cars' > .row, id=whipsList >

20. cmd: cd greglist cd app > cd models > cat > grab get cardTemplate

21. Car.js: paste card inside class, change out data accordingly

22. controller > drawCars(){ let template = ''; cars.forEach(car => template+= car.cardTemplate); setHTML('whipsList', template)} *make sure that it draws to page!

23. ADDING CARS:  create!; go get form from cmd gregslist; index.html, paste in button for car form

24. cmd- grab form, put in index.html; custom css: display: block; change form inputs/labels accordingly

25. write createCar() in the controller. async createCar() {try {event.preventDefault(); log'formsubmitted';->test make sure works; const form = event.target; const carData = getFormData(form); log('car data', carData);->ck form/log; ->comes in as object; give to service-> await carsService.createCar(carData); //form.reset later} catch(error){console.error(error)Pop.error(error,message)}};

26. Service: createCar(carData){//still talking to api and expecting response// const res = await api.post('api/cars', {name: 'Jeremy'}<-to test>); log('created car?', res)}

27. Test form, fill out, error- unauth; check network/headers: we sent post and to api/cars, BUT, post request has payload, and name jeremy is in there. 

28. CodeWorks Sandbox: Auth0 settings: domain/audience/clientId: copy domain > env.js- put in domain area., as well as audience and client id

29. login: you can make fake email and pw; temp mail;  makes things; send off post request from form; 400> headers> request headers> bearer token

30. go to index.html and get rid of auth template!

31. network tab: 3 diff requests

32. Car model: add creator name/pic or any other data to template- this.creator.name if drilling into object

33. submit form- 400: network-red-open header: payload: validation error: it says what all is required; caught error with try/catch!

34. Service: const res = await api.post('api/cars', carData)

35. Submit form again! 400- network- red error- read payload, then read preview, OBJECT needs turned to car. make sure name on form is what api wants.

36. Test form again: log from service, open network tab: post request good, payload: object, everything is there, preview looks good. its stored in db, but not on page until refresh of page.

37. Turn object into car in appstate- create car function in service: const builtCar = new Car(res.data) .map exists on ARRAY class, NOT object class. NO MAP for one new car!!!! ; Appstate.cars.push(builtCar) <-bc appstate.cars is an array!>; AppState.emit('cars'); to trigger draw!

38. CRUD Delete: car model: make delete button in template w/onclick- put id inside of parens

39. Controller: async deleteCar(carId){try{await carService.deleteCar(carId)}/catch w/error handling}

40. async deleteCar(carId){log('car id', carId); const res = await api.delete(`api/cars/${carId}`); log('deleted car', res.data); } //id needs to go into the url itself thru api//

41. add const wantsToDelete = await Pop.confirm('Are you sure you want to delete'); in controller under try; if(!wantToDelete) {return}

42. Network tab: head request url: says ok for delete; preview deleted value

43. Service: delete function: const carIndex = AppState.cars.findIndex(car => car.id == carId)  (find me the car where the car id is equal equal to the car Id in parameter); AppState.cars.findIndex(carIndex, 1); if (carIndex == -1) {throw new Error(`no car index found with the id of ${carId}`); AppState.cars.splice(carIndex, 1); AppState.emit('cars');}

44. Car.js: solve button only showing if you're creator of car! cut button out, get ComputeDeleteButton(){if(AppState.account.id == this.creatorId){return `<button></button>`} return ''; }

45. in template above div: ${this.ComputeDeleteButton}

46. in AppState account starts as null. go back to car model: swap return '' and return button; if(!AppState.account || AppState.account.id != this.creatorId)

47. Delete button needs to stay on page! >> redraw templates after we get account; listener on account should fix this.......

48. CarsController: constructor: AppState.on('account', _drawCars)

49. Hide form when not logged in! html: button d-none on class on car form; carFormButton for id; Controller: AppState.on('account', _showFormButton); private function above: _showFormButton(){const account = AppState.account; if(!account){return}; const carFormButton = document.getElementById(elementId); carFormButton.classList.remove(d-none')}

50. CRUD- edit/update/put request to api; Car Model: alt shit down delete button to make edit button. just change button function and text. add string interpolation for edit button in template.

51. another getter editForm(){} in car model; inside collapse in html, copy and add to car model. put return under edit form and paste what is copied (form). to prepopulate inputs w/text: add value on div: see #54.

52. change button to drawEditForm in template; put id on div down from collapse of car-form; 

53. controller: public draw function: drawEditForm(carId) {const foundCar = AppState.cars.find(car > car.id == carId); setHTML('car-form', foundCar.EditForm); }

54. Car model: on inputs: value="${this.make}" etc for all your data. for text area, come INSIDE between textarea open/close tag

55. Car.js- edit form: change onsubmit to editCar(event) instead of createCar!!!

56. Controller: async editCar(event){try {event.preventDefault(); const form = event.target; const carData = getformDate(form); log('car data', carData); await carService.editCar(carData)} / catch(error); {console.error(error); Pop.error(error,message)};}

57. Service: async editCar(carData){const res = await api.put()} (back in car.js editCar(event, `${this.id}`));(carData, carId) controller editCar(event, carId), log w/carId also. back to Service: const res = await api.put(`api/cars/${carId}`, carData); log('edited car', res.data); network tab/put ok/ id on end of url string

58. Update page: Service editCar: const updatedCar = new Car(res.data); //find car in appstate take him out put one in// AppState.cars.splice(carIndex, 1, )// or copy/paste appstate cars find but change to oldcarindex. ;; AppState.cars.splice(oldCarIndex, 1, updatedCar); AppState.emit('cars')

59. CONFUSING: STATIC! edit form replaces create;  index.html: grab regular createCar form, store it in Car.js. under editform funct; static get CreateForm(){return `paste form here`}

60. drawCarForm(){setHTML('car-form', Car.CreateForm)}

61. Controller: constructor: AppState.on('account',this.drawCarForm); this.drawCarForm() on page load

62. ScrollTo: controller: drawEditForm under foundCar/ const carForm = document.getElementById('car-form');//setHTML here// bootstrap.Collapse.getOrCreateInstance('#carCollapse').show(); carForm.scrollIntoView() AFTER setHTML; //do bootstrap collapse on edit and create too

63. Everything in router view copy/comment out/ go to view folder create carsView export const CarsView = /html/ `paste in here`

64. Change view to CarsView in router!

///////////////////////////////!SECTION

6/28/23

1. env.js! use sandbox to fill info. use bcw sandbox for base url

2. Request to dnd api- this will go in axios; create another instance of axios to talk to dnd. leave first export const api. export const dndApi = axios.create({
  baseURL: '//put base here',
  timeout: 8000
})

3. create controller/constructor/log > router- put in controller > html- rid of auth template

4. controller: async getSpells() {
  try{
    await spellsService.getSpells()
  }
  catch(error)
  console.error(error)
  Pop.error(error.message)
}

5. SpellsService.js;  async getSpells()
 {const res = await dndApi.get('api/spells')
 log res.data
 }

6. controller this.getSpells on page load

7. Store pojos in appstate:  spells = [], // @type {Object[]}

8. Service: getSpells: appstate.spells = res.data.results

9. draw to string in controller: let spells = appstate.spells; let template = ''; 
spells.forEach(spell => {; template += `<li class="mb-2 selectable" role="button">Spell</li>`}); setHTML('spellList', template)

10. index: .container-fluid, row, col-3 ul id=spellList; and col-9

11. spells controller/constructor/ AppState.on('spells' drawfunct)'

12. ${spells.name} in li tag

13. grab index from pojo and get to service to make get request
      a. onclick="app.SpellsController.getSpellDetails('${spell.index}')"

14. asnyc getSpellDetails(spellIndex){try/await spellService.getSpellDetails(spellIndex)/catch, error handling}

15. svc above function: async; const res = await dndApi.get(`api/spells/${spellIndex}`); log res.data!; 

16. copy object from log and make spell model! export/constructor(data); let spellData = paste

17. save to sandbox api: change desc to description//*FIXME - chnage [] to string this.description = data.desc
Just store required things from sandbox
this.damage = data.damage ? data.damage.damage_type.name : 'does no damage'
  *copy property path and paste

18. appstate activeSpell = null @type import spell || null

19. const newSpell = new Spell(res.data); AppState.activeSpell = newSpell

20. controller: funct drawActive(){let spell = AppState.activeSpell; log(spell, 'active spell')} call w/AppState.on('activeSpell', drawActiveSpell)

21. target ul spelllist in style css ul{max-height: 85vh; overflow-y auto;}

22. html template: move tos pell model and make get details template function w/string interpolation

23. controll: drawactivespelll sethtml spelldetails spell.detailstemplate

24. button on spell details to saev to SANDBOX API   DETAILS TEMPLATE () button: save to Sandbox
post request! onclick="app.SandboxSpellsController.createSpell()" //only one active spell in appstate at a time

25. createSpell(){constructor(){}; async createSpell(){try/await/sandboxSpellService.createSpell()  /catch/error}}

26. sandboxservice createSpell() { const res = await api.post('api/spells'); log(res.data)}

27. controller in router!

28. no payload/ nothing was sent to api to become spell there; sandboxservice createSpell() {//const spellToSentToApi = AppState.activeSpell;  const res = await api.post('api/spells',// spellToSendToApi); log(res.data)}

29. array of strings into a string: .join: ['sup', 'yall'] 'sup,yall'  .jion(' ') 'sup yall'  // ('\n') <--puts enter in new line character>

30. another page to see our spells> index.html navbar- make another page My Spells; router: add another path, also sandbox controller

31. take whole container fluid from index and put into new view DNDspellsview export consts dndspells view = /*html*/ `paste container`

32. update view in router

33. sandbox control async getMySpells(){try/await sandboxservice.getMySpells()catch/error}

34. service get my spells{} const res = await api.get('api/spells'); log "res.data ; 
//NEED logged into sandbox! 

35. 401: add listener to controller appstate.on('account', this.getmypells)

36. change to spell class; AppState > mySpells = [] // dont forget import

37. sandbox service: get my spells/ const builtSpells = res.data.map(spellPojo => new Spell(spellPojo))
AppState.mySpells = builtSpells (notice map didnt have results!)

38. model descript// this.description = data.description || data.desc.join('\n')

40. typeof()



Checkpoint Hint: 

  change my spells template in view to be actual button/ copy everything in router and copy, make another view (sandboxspellsview)/ they dont draw when you come BACK to page. sscontroller: when loaded, draw my spells in constructors

1. 
  ***property that we can save: 'prepared' property: go to model/spell.js: top: this.prepared = data.prepared || false; now-> get spells be able to edit spell/flip bool to true; CHECKBOX! spelllistitemtemplate: input ckbox, checked attribute chooses whether on page load or not. paste in template. checkbox -> put request to api -> spell now prepared: input onchange="app.SandboxSpellsController.toggleSpellPreparation('${this.id}')"

  controller: async toggleSpellPreparation(spellId){try/await sandboxSpellsService.toggleSpellPreparation(spellId)/catch/error}--->
  const foundSpellIndex = AppState.mySpells.findIndex(spell => spell.id == spellId)

  const foundSpell = AppState.mySpells[foundSpellIndex]
  if(!foundSpell) {
    throw new Error ("INVALID ID")
  }

  const res = await api.put(`api/spells/${spellId}`, {prepared: !foundSpell.prepared}); 
  log'edited spell',res.data; 

  //old one out of appstate and get new back

  //foundSpell.prepared = res.data.prepared

const updatedSpell = new Spell(res.data)

AppState.mySpells.splice(foundSpellIndex, 1, updatedSpell)


html doesn't have checked attribute;get myspelllistitemtemplate() input ${this.prepared ? 'checked' : ' ' }


2. count how many spells and how many are prepared

  view: sandboxspells: insert <p><span id="preparedSpellCount">0</span> / <span id="spellCount">0</span></p> 
ssscontroller
drawMySpells/
const preparedSpells = mySpells.filter(spell => spell.prepared).length
   setText('spellCount', mySpells.length); setText('preparedSpellCount', preparedSpells.length)

ss service: AppState.emit('mySpells')
