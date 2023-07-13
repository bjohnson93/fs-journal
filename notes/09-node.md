# Node

Javascript runtime environment

7/10/23

ONE SERVICE

1. new template: bcw create > node-server-auth0

  package.json: express <-'bread and butter'  express- be our library that takes in requests from user and sends back responses to them>, 
  /tomorrow: auto0provider - see if person is allowed, if they exist;

2. Server Folder: similar to mvc setup, utils folder is different, models will look different also

    #NOTE - COMMENT OUT: utils>main.js: connect to atlas mongoDB ; DBConnection.connect()
      utils>Startup: Aut0 ; domain ; clientId ; audience

    Values Controller: super, extends, this.router

3. Run&Debug to 'spin up', click start server in call stack; port 3000; pause/spin/stop server

4. localhost:3000/api/values: sends back array of two strings; 

5. *Always inherit BaseController to whatever controller you're working in
  Server folder: controller: CatsController.js //no need to write controllers in router(automatic)//
      export class CatsController extends BaseController {
        constructor() {
          super('api/cats')  <--calls constructor on base controller that says run this code>
          this.router      <--bringing in router from base controller>
          .get('', this.getCats)  <--'' because we don't want to append to end of super api/cats>; then ctrl . declare method
        }
//request object- payload, request body, bearer token, response object- has methods built in to send back to user, next may be the error//
        getCats(req, res, next){
          try{res.send('You made a request!')}/catch (error); next(error)
        }
      }

6. Re-spin server with green refresh in UR corner menu after every change

7. We want to send back Data! Db folder > new files FakeDB.js; export const cats [{}{}{}]"

8. cats controller res.send(cats) // import from fakedb, respin; JK WE NEED A SERVICE

9. remove cats from res.send: async try{ const cats = await catsService.getCats() /res.send(cats)}

10. CatsService: class CatsService{ async getCats(){return cats //from fakeDB import//}} export const catsService = new CatsService(). save and respin

11. controller: after .get() in constructor; .get('/:id', this.getCatById);; async getCatById(req, res, next) {try{res.send('get cat by id'//for testing//)}/catch}

12. Breakpoints debug: hover over line number and click red dot

13. async getCatById(req, res, next){const catId = req.params.catId / res.send(`get cat by id ${catId}`) <--must match .get/:id> const cat = await catsService.getCatById(catId)<--get cat fromDB>}

14. Service: getCatById(catId){const foundCat = cats.find(cat => cat.id == catId) if(!foundCat){throw new BadRequest(`${catId} was not a valid Id`)} return foundCat}

15. Someone wants to add a cat? controller: after two .get 's, .post('', this.createCat)

16. async createCat(req, res, next){try{const catData = req.body// res.send(catData)}/catch(error){next(error)}}

17. POSTMAN API!; sends on our behalf, makes http requests

18. Get/Post request: Body: raw, Json, { "keys": "values", "name": "Falcon"}

19. async createCat(req, res, next){try{const catData = req.body const cat = await catsService.createCat(catData)// res.send(catData)}/catch(error){next(error)}}

20. catsService  createCat(catData) {catData.id = cats.length + 1; cats.push(catData); return catData}

7/11/23 MongoDB

-BCW Create, ExpressMVC, gregslistNode

Open Workspace
-client folder
-server folder

 THE LITTLE BELL IN VS CODE OPENS WORKPLACE SETTINGS
1. Server: .env: 
MongoDB Atlas page to grab connection string > connect btn > drivers > copy connection string, paste into .env; 
replace <password><Mf61UfRB5E4aGXOf > with mongoDB password, must be url safe!!!
port doesn't need filled in
auth_domain=      *auth0- applications, my app, copy domain/ client id / audience is under apis
auth_audience=
auth_clientId=
**never push this to github^^!!!** .gitignore file- says to not push node_modules and .env to github

2. Client: env.js: domain, audience, client id

3. Ctrl ~ to open command line IN VS CODE, make sure right directory. ls, cd into client folder, then run bcw serve/localhost 8080

4. Debug to spin backend, start server

5. sign into auth0 with whatever

6. If connections are successful, slack .env and slack it to yourself!!!

7. auth0 provides user management/users you can manage users

8. mongodb collections/accounts gives account query results!

**NOTE - Code defensively, always as if you're under attack, as if everyone is malicious or everyone is stupid

9. Write our own Schema > server > model > car.js
export const CarSchema = new Schema( (should auto import schema from mongoose)
  {  
    make: {type: String, required: true, maxlength: 50, minlength: 3},
    model: {type: String, required: true, maxlength: 50, minlength: 1},
    year: {type: Number, required: true, max: 2025, min: 1901},
    color: {type: string, maxlength: 100},
    ownedByGrandma: {type: Boolean, required: true, default: false},
    miles: {type: Number, required: true, max: 400000, min: 1},
    engineType: {type: String, enum: ['v8', 'v6', 'big-block'], default: 'medium'}
    description: {type: String, maxlength: 500}
},<--gives intellisense>{timestamps: true, toJSON: {virtuals: true}}
) imgUrl is type string, no type url
creatorId: {type: Schema.Types.ObjectId, required: true}

10. db folder > DbContext.js , .env--> put title(gregslist) before ? in url in connection string, this saves it in mongo db in folder with that title
DbContext under values and account; Cars = mongoose.model('Car', CarSchema)

11. Server>Controllers> CarsController.js  export class CarsController extends BaseController { 
  constructor(){
    super('api/cars')
    this.router
    .get('', this.getCars)  //to test go to localhost 3000/api/cars
  }
}

12. Postman! 

13. CarsService, send over getCars; dbContext.Cars.find()  <--Mongoose find, not JS>

14. Mongoose is like our translator! our js to binary script to mongodb

15. Postman get request: 200 ok, [] turned info into array, this is good

16. create controller/svc; postman post body raw json

17. postman creatorId copy from mongo. Postman doesn't know we are logged in or not

18. CarsController: constructor: .use(Auth0Provider.getAuthorizedUserInfo) <--you have to have bearer token for any requests to put/post/delete> PUT .use BETWEEN GET A POST!!!!!!

19. local8080 open preview bearer token copy and paste in postman; Authorization type bearer token, paste in token slot

20. #REVIEW - IMPORTANT: breakpoint on res.send on create car to make sure we have correct user
const carData = req.body
carData.creatorId = req.userInfo.id <----this makes sure the person making request matches the user/creatorId>

21. public method in controller: .get('/:carId')

22. .env has to be in server > server

7/12/23

UML CHART: (done by architect)
Book App

Book 
  id               objectid
  title            string(100)
  description      string(500)
  isHardCover      boolean
one-to-many relationship; pages point to the one specific book
    Page
      id               objectid
      chapterNumber    number
      content          string(1000)
      bookId           objectid

*The page is technically a child of the book!

    Account (author) (points to book)
      id               objectid
      name             string(100)
      picture          string(500)
      email            string(100)

    BookAuthor (points to specific book and author)
      id               objectid
      bookId           objectid
      authorId         objectid

many to many keeps track of two different things (author id/book id)

1. start with models or schema
 3 separate controllers- posts and gets
 export const .Schema = new Schema({},{timestamps})

2. Controller

3. Spin up/environment variables in .env (project name), env.js front end

4. cd .., cd into client folder, bcw serve/localhost8080;  debug to start server: if u get error read first line, make sure controller matches!!! (s)

5. test get w/postman- new collection

6. .use(Auth0Provider.getAuthorizedUserInfo), .post

7. Private tab- sign in as something else.

8. one to many: page; new model

9. page model bookId: {ref: 'Book'}

Profiles are public information about a user, Accounts are private info about a user







<!-- **!SECTION Hackathon Prep! 7/13/23 -->
**Everyone will be working on ONE repository**
**Greglist good ref for crud methods**

1. express-mvc, will use client folder today a bit
2. .env remember project name
**For hackathon, we will use one person's .env/env.js auth credentials 
3. open terminal, cd .., cd into client folder, bcw serve
4. debug, start Server
5. Start with model for highest most (schema), don't forget object of {timestamps: true, toJSON: {virtuals: true}}       ; reporterId: {type: Schema.Types.ObjectId, required: true, ref: 'Account'}
6. Write dbContext birds
7. write a controller! (extends BaseController), write get!
8. write a service! getBirds const birds = await dbContext.Birds.find() ; return birds
9. Postman, set up collection, folder, get birds, get your empty array
10. Controller, post request to create birds
11. createBird(r,r,n){const birdData = req.body; const bird= await birdsService.createBird(); res.send(bird)}
12. Service: createBird(birdData){const bird = await dbContext.birds.create(birdData); return bird}
13. Postman: add req create bird post req, add account id
14. Controller: .use(Auth0Provider, getAuthorizedUserInfo)
15. **review** controller create bird: const birdData = req.body; birdData.reporterId = req.userInfo.id
16. localhost 8080 bearer token, set up as variable in postman, add into auth for create bird
17. Controller get request: add query under try: const query = req.query; in postman locahost:3000/api/birds?size=small will query the small birds
18. Service getbirds(query)/ const birds = await dbContext.Birds.find(query) <--also add getBirds(query) in controller to service>
19. team member!!! push: create bird and get bird done on server, commit and sync changes
20. Collaborators and teams, add people, add each - select person and Admin >> pending request to accept, she can accept and push changes to same repository
21. DO NOT FORK!!!! Clone down- git clone, paste what u copied, cd into, code .
22. **IMPORTANT** create a .env in the server folder, copy your partners/starters info into .env; env.js is already there in client
23. terminal: npm i 
24. start server, start client
25. Open Client: Controller, router, comment out auth template
26. async getBirds()try/catch await birdservice
27. birds service getBirds. OPEN AXIOS AFTER api.get to 
28. remember to call function in constructor 
29. make your model
30. appstate, store data []
31. svc getbirds const gotbirds f= res.data.map(b=>new Bird(b)); store in appstate: Appstate.birds= gotBirds; log it
32. draw birds! let birds = AppState.birds; let template = ''; birds.forEach(b => template += **create template**)
33. index: primary viewport create card template, copy and comment out
34. get template in model getBirdCardTemplate(){return `<html></html>`} string interpolation
35. draw function in controller : let birds = AppState.birds; let template = ''; birds.forEach(b => template += b.BirdCardTemplate) setHtml('birds', template)  <----birds is from appstate>
36. call function w/listener
37. make card a selectable function: (template, onclick) setActiveBird; log to test!
38. move to service (pass thru id): const foundBird = Appstate.birds.find(b +> b.id == birdId);  (make active bird null in appstate); Appstate.bird = foundBird
39. data-bs-toggle from modal onto onclick in model, comment out button
40. customize modal
**image-fluid class
41. move modal to template, keep outer html in index
42. _drawActiveBird : let activeBird = AppState.bird setHtml('modal-guts', activeBird.activeBirdTemplate)
43. listener for _drawActiveBird!!! appstate.on('bird', _drawActiveBird)
44. make form! create 'Report Bird' button; uncomment and copy active bird form, paste for report bird form and customize accordingly  *id of input needs to match label for=""
45. Enum: label for// select name=size' id='size'// options value="medium" <-->
label: display:block in css will help
46. put form into model (comment out in index); static get BirdForm(){paste here }
47. write function to setBirdForm(){setHTML('modal-guts', Bird.BirdForm)}
48. put this func on onclick on create button in html
49. async createBird(event) event.preventDefault(); let form = event.target; let formData = getFormDate(form); log(formData, 'passed form data') check to make sure things correct: checkbox says on instead of true; 
if(formData.canFly -- 'on'){formData.canFly = true} else { formData.canFly = false }
NOW it is ready to go to service 😀
50. async createBird(formData){
  const res = await api.post('api/birds', formData)
  log res.data
  const newBird = new Bird(res.data)
  AppState.birds.push(newBird)
  emit('birds')
}
51. form.reset() in controller under await; bootstrap.Modal.getOrCreateInstance('#exampleModal').hide()
52. commit changes
53. SWITCH TO SERVER: Pull down changes: there will be a message down low on vs code with 1 and down arrow (one commit behind on github). click and it will pull down!
54. many to many, add to bird schema
55. Bird model on SERVER: at bottom: 
BirdSchema.virtual('reporter', {
  localField: 'reporterId',
  foreignField: '_id',
  justOne: true,
  ref: 'Account'
})

56. BirdsService: const birds = await dbContext.Birds.find(query).populate('reporter', 'name picture')
57. Start Server
58. cd client folder, bcw serve, localhost8080
59. console array of birds: reporter is now populated
60. bird service, createBird: after 1st line// await bird.populate('reporter', 'name picture')
61. Bird watcher: BirdWatcher.js model/schema: export const birdWatchSchema = new schema// {timestamps: true, toJSON: {virtuals: true}}; put in birdId {type: Schema.Types.ObjectId, required: true, ref: 'Bird}, 
watcherId: {type: Schema.Types.ObjectId, required: true, ref: 'Account'}
62. BirdWatchersController.js super('api/birdWatchers').use(Auth0Provider.getAuthorizedUserInfo) .post('', this.createBirdWatcher)
async createBirdWatcher(req, res, next) {
  try{
    const birdWatcherData = req.body

    birdWatcherData.watcherId = req.userInfo.id

    const birdWatcher = await birdWatchersService.createBirdWatcher(birdWatcherData)      <--svc created line 63>

    return res.send(birdWatcher)
  } catch (error) {
    next(error)
  }
}

63. async irdWatchersService(birdWatcherData) {
  const birdWatcher = await dbContext.BirdWatchers.create(birdWatcherData)      //make BirdWatchers = mongoose.model('BirdWatcher', BirdWatcherSchema)
  return birdWatcher
}

REQ.BODY AND USER INFO FOR CREATES!!!

64. Postman post req: get bird id, put in auth, send off, success!!!
65. You can see same bird twice, no no! BirdWatcherSchema: at bottom: BirdWatcherSchema.index({birdId: 1, watcherId: 1}, {unique: true})
66. Won't reflect in postman: go to MongoDB: sign in, drop collection, respin, try in postman again
67. Schema bottom: 
return watcher info:
BirdWatcherSchema.virtual('watcher', { 
  localField: 'watcherId',
  foreignField '_id',
  justOne: true,
  ref: 'Account'
})
BirdWatcherSchema.virtual('bird', { 
  localField: 'birdId',
  foreignField '_id',
  justOne: true,
  ref: 'Bird'
})
68. birdWatcherService: create: second line: await BirdWatcher.populate('bird')<--comment out later bc it's already in the view card>; await birdWatcher.populate('watcher', 'name picture')
69. find birdWatcherByBirdId! (to show how many watchers) .get('/:birdId/birdWatchers', this.getBirdWatcherByBirdId)
70. async getBirdWatcherByBirdId(req, res, next) {
  try{

    const birdId = req.params.birdId
    const birdWatchers = await birdWatchersService.getBirdWatcherByBirdId(birdId)
    return res.send()
  } catch(error){
    next(error)
  }
}
71. birdWatchersService:
async getBirdWatcherByBirdId(birdId){
  <!-- const birdWatchers = await dbContext.BirdWatchers.find({birdId: birdId}) -->
  const birdWatchers = await dbContext.BirdWatchers.find({birdId}) <--this works fine too>
  return birdWatchers
}
72. populate (same func)// const birdWatchers = await dbContext.BirdWatchers.find({birdId}).populate('watcher', 'name picture')
**HOW MANY PEEPS HAVE SEEN DIS BIRD**
73. Bird Schema
BirdSchema.virtual('birdWatcherCount', {
  localField: '_id',  <--id of bird watcher itself>
  foreignField 'birdId',
  <!-- justOne: false, --> this line not needed
  ref: 'BirdWatcher'   <--matches db context>
  count: true
})

74. BirdsService: get birds .populate('reporter', 'name picture').populate('birdWatcherCount') <--this part new>
RE-SPIN! get all bird in postman

75. push/pull down/ respin server

76. model/ Bird
this.reporter = data.reporter
this.birdWatcherCount = data.birdWatcherCount
<!-- this.reportName = data.reporter.name -->

77. Need to add img of reporter
model, bird card temp: div to hold name of bird, birdWatcherCount; ${this.birdWatcherCount} img src="${this.reporter.picture}"

78. Make: bird watchers controller: getBirdWatchersByActiveBird(){await birdWatchersService.getBirdWatchersByActiveBird}

79. BirdWatchersService: getBirdWatchersByActiveBird(){const bird = AppState.bird; const res = await api.get(`api/birds/${bird.Id}/birdWatchers)} log(res.data)
**go make it in Appstate: birdWatchers = []
AppState.birdWatchers = res.data.map(p => new Profile(p.watcher))  <--passes down watcher object nested inside>
log again AppState.birdWatchers

80. BirdWatchersController function _drawBirdWatchers const birdWatchers = AppState.birdWatchers ; let template = '' //go to model and make get BWTemplate. make template in index, paste in model
bird model, active template, id of bird watchers in div where u want to display them. title${this.name} <--easily displays on hover>

81. BWSERVICE: becomeWatcher() {const bird = AppState.bird <--gives active bird id; const res = await api.post(''api/birdWatchers', {birdId : bird.id}) bird.birdWatcherCount++ ; AppState.birdWatchers.push(new Profile(res.data.watcher)) ; AppState.emit('birdWatchers'); AppState.emit('birds')>}


// Add team members to Trello board, and you can basically 'fork' it, must make trello account, you can assign someone to task

// Build Figma for site; fig-jam for uml







control shift f
