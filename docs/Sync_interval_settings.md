About player sync
-----------------

Player key sync is always done on demand. i.e. Player presses W, (or pushes forward on the joystick), and the sync for that is sent straight away to the server, and then to the other clients. There is no setting to limit key sync as it is an essential component to minimize latency. The 'player\_sync\_interval' below, is the interval between positional and rotational corrections to key sync. This is in case the movement interpreted by the key sync system on remote clients has introduced any errors.

Default values
--------------

|                                     |                  |                 |                                                                                                                                                                     |
|-------------------------------------|------------------|-----------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Name**                            | **Default (ms)** | **Valid range** | **Description**                                                                                                                                                     |
| player\_sync\_interval              | 100              | 50-300          | Time between key sync correction updates for players. (Note: Player key sync is always done on demand and is not affected by any setting)                           |
| lightweight\_sync\_interval         | 1500             | 150-4000        | Time between updates for very far away players                                                                                                                      |
| camera\_sync\_interval              | 500              | 100-1000        | How often to tell the server of any client side changes to the local players camera position and target.                                                            |
| ped\_sync\_interval                 | 400              | 100-1000        | Time between updates for non-player peds                                                                                                                            |
| unoccupied\_vehicle\_sync\_interval | 1000             | 100-1000        | Time between updates for unoccupied vehicles                                                                                                                        |
| keysync\_mouse\_sync\_interval      | 100              | 50-200          | Minimum gap between mouse movement updates being sent to the server                                                                                                 |
| keysync\_analog\_sync\_interval     | 100              | 50-200          | Minimum gap between joystick partial axes movement updates being sent to the server. (Full axes movement is treated as key sync and is not limited by this setting) |
||

Suggested settings
------------------

### Bandwith and CPU saver

|                             |      |
|-----------------------------|------|
| player\_sync\_interval      | 200  |
| lightweight\_sync\_interval | 3000 |
||

### Bandwith and CPU super saver

|                             |      |
|-----------------------------|------|
| player\_sync\_interval      | 300  |
| lightweight\_sync\_interval | 4000 |
||

### Less annoying unoccupied vehicles

|                                     |     |
|-------------------------------------|-----|
| unoccupied\_vehicle\_sync\_interval | 500 |
||

### Uber sync (bandwidth and CPU intensive)

|                                 |     |
|---------------------------------|-----|
| player\_sync\_interval          | 50  |
| keysync\_mouse\_sync\_interval  | 50  |
| keysync\_analog\_sync\_interval | 50  |
||
