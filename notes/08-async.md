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