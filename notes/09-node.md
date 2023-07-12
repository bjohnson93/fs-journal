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

10. 