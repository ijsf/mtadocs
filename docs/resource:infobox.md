TextSpeech gives you the ability to get spoken text by Google's TextToSpeech.

Events
------

**Note:** You may have to add the events in your script using addEvent() if you want to use them.

### Server

|          |            |                |
|----------|------------|----------------|
| **Name** | **Source** | **Parameters** |
||

|              |            |                              |
|--------------|------------|------------------------------|
| **onSpeech** | triggerFor | ``` lua                      
                             string text, string language  
                             ```                           |
||

### Client

|                    |      |                              |
|--------------------|------|------------------------------|
| **onClientSpeech** | root | ``` lua                      
                             string text, string language  
                             ```                           |
||

Exported functions
------------------

### Server

|         |           |                                                  |
|---------|-----------|--------------------------------------------------|
| ``` lua 
 boolean  
 ```      | **speak** | ``` lua                                          
                       string text, string language, element triggerFor  
                       ```                                               |
||

### Client

|         |             |                                                         |
|---------|-------------|---------------------------------------------------------|
| ``` lua 
 element  
 ```      | **speak**   | ``` lua                                                 
                         string text, string language                             
                         ```                                                      |
||
| ``` lua 
 element  
 ```      | **speak3D** | ``` lua                                                 
                         string text, string language, float x, float y, float z  
                         ```                                                      |
||
