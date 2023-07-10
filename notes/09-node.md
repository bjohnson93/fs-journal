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