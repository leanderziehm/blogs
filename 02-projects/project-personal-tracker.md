# Project: Personal Tracker

word misspell tracker

habit tracker

timer

countdown

spending tracker







## Timer



```

{
   "openapi": "3.1.0",
   "info":{
      "title": "Timer REST API ",
      "description: "Timer to start and stop and list timers. ",
      "version": "0.1.0"
   },
   "paths": {
      "/timers":{
         "get": {
            "description": "list all timers",
            "operationId": "getTimers"
         }  
      },
   "/timer":{
   "post": {
      "description": "creates timer",
      "operationId": "createTimer"
   }
},  
    "/timer/{timer_id}":{
         "get":{
            "description": "get timer",
            "operationId": "getTimer"
         },
         "delete":{
            "description": "deletes timer",
            "operationId": "deleteTimer"
         },
         "put":{
            "description": "idempotently update a timer",
            "operationId": "updateTimer"
            }
      },
    
  
   }
}

```
