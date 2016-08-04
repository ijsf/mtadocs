Introduction
------------

This is a list of GTA:SA's vehicle ID numbers, as listed in the vehicles.ide file. These vehicle ID numbers are used for several vehicle scripting functions.

#### Lua table of all the valid vehicle IDs listed on this page

``` lua
vehicleIDS = {
    602, 545, 496, 517, 401, 410, 518, 600, 527, 436, 589, 580, 419, 439, 533, 549, 526, 491, 474, 445, 467, 604, 426, 507, 547, 585, 405, 587,
    409, 466, 550, 492, 566, 546, 540, 551, 421, 516, 529, 592, 553, 577, 488, 511, 497, 548, 563, 512, 476, 593, 447, 425, 519, 520, 460, 417,
    469, 487, 513, 581, 510, 509, 522, 481, 461, 462, 448, 521, 468, 463, 586, 472, 473, 493, 595, 484, 430, 453, 452, 446, 454, 485, 552, 431,
    438, 437, 574, 420, 525, 408, 416, 596, 433, 597, 427, 599, 490, 432, 528, 601, 407, 428, 544, 523, 470, 598, 499, 588, 609, 403, 498, 514,
    524, 423, 532, 414, 578, 443, 486, 515, 406, 531, 573, 456, 455, 459, 543, 422, 583, 482, 478, 605, 554, 530, 418, 572, 582, 413, 440, 536,
    575, 534, 567, 535, 576, 412, 402, 542, 603, 475, 449, 537, 538, 570, 441, 464, 501, 465, 564, 568, 557, 424, 471, 504, 495, 457, 539, 483,
    508, 571, 500, 444, 556, 429, 411, 541, 559, 415, 561, 480, 560, 562, 506, 565, 451, 434, 558, 494, 555, 502, 477, 503, 579, 400, 404, 489,
    505, 479, 442, 458, 606, 607, 610, 590, 569, 611, 584, 608, 435, 450, 591, 594
}
```

#### Lua table of vehicles that are not lockable

``` lua
notLockableVehicles = {
    594, 606, 607, 611, 584, 608, 435, 450, 591, 539, 441, 464, 501, 465, 564, 472, 473, 493, 595, 484, 430, 453, 452, 446, 454, 581, 509, 481,
    462, 521, 463, 510, 522, 461, 448, 468, 586, 425, 520
}
```

#### Lua table of vehicles without number plates

``` lua
noNumberPlates = {
    592, 553, 577, 488, 511, 497, 548, 563, 512, 476, 593, 447, 425, 519, 520, 460, 417, 469, 487, 513, 509, 481, 510, 472, 473, 493, 595, 484,
    430, 453, 452, 446, 454
}
```

Aircrafts
---------

|                                                                                |                                                                                     |
|--------------------------------------------------------------------------------|-------------------------------------------------------------------------------------|
| ### Airplanes                                                                  
                                                                                 
 | Name       | ID  | Image                                                   |  
 |------------|-----|---------------------------------------------------------|  
 | Andromada  | 592 | [Image:Androm.png](/Image:Androm.png.md "wikilink")     |  
 | AT-400     | 577 | [Image:At400.png](/Image:At400.png.md "wikilink")       |  
 | Beagle     | 511 | [Image:Beagle.png](/Image:Beagle.png.md "wikilink")     |  
 | Cropduster | 512 | [Image:Cropdust.png](/Image:Cropdust.png.md "wikilink") |  
 | Dodo       | 593 | [Image:Dodo.png](/Image:Dodo.png.md "wikilink")         |  
 | Hydra      | 520 | [Image:Hydra.png](/Image:Hydra.png.md "wikilink")       |  
 | Nevada     | 553 | [Image:Nevada.png](/Image:Nevada.png.md "wikilink")     |  
 | Rustler    | 476 | [Image:Rustler.png](/Image:Rustler.png.md "wikilink")   |  
 | Shamal     | 519 | [Image:Shamal.png](/Image:Shamal.png.md "wikilink")     |  
 | Skimmer    | 460 | [Image:Skimmer.png](/Image:Skimmer.png.md "wikilink")   |  
 | Stuntplane | 513 | [Image:Stunt.png](/Image:Stunt.png.md "wikilink")       |  | ### Helicopters                                                                     
                                                                                                                                                                       
                                                                                  | Name            | ID  | Image                                                   |  
                                                                                  |-----------------|-----|---------------------------------------------------------|  
                                                                                  | Cargobob        | 548 | [Image:Cargobob.png](/Image:Cargobob.png.md "wikilink") |  
                                                                                  | Hunter          | 425 | [Image:Hunter.png](/Image:Hunter.png.md "wikilink")     |  
                                                                                  | Leviathan       | 417 | [Image:Leviathn.png](/Image:Leviathn.png.md "wikilink") |  
                                                                                  | Maverick        | 487 | [Image:Maverick.png](/Image:Maverick.png.md "wikilink") |  
                                                                                  | News Chopper    | 488 | [Image:Newschop.png](/Image:Newschop.png.md "wikilink") |  
                                                                                  | Police Maverick | 497 | [Image:Polmav.png](/Image:Polmav.png.md "wikilink")     |  
                                                                                  | Raindance       | 563 | [Image:Raindanc.png](/Image:Raindanc.png.md "wikilink") |  
                                                                                  | Seasparrow      | 447 | [Image:Seaspar.png](/Image:Seaspar.png.md "wikilink")   |  
                                                                                  | Sparrow         | 469 | [Image:Sparrow.png](/Image:Sparrow.png.md "wikilink")   |  |

Boats
-----

| Name       | ID  | Image                                                   |
|------------|-----|---------------------------------------------------------|
| Coastguard | 472 | [Image:Coastg.png](/Image:Coastg.png.md "wikilink")     |
| Dinghy     | 473 | [Image:Dinghy.png](/Image:Dinghy.png.md "wikilink")     |
| Jetmax     | 493 | [Image:Jetmax.png](/Image:Jetmax.png.md "wikilink")     |
| Launch     | 595 | [Image:Launch.png](/Image:Launch.png.md "wikilink")     |
| Marquis    | 484 |
| Predator   | 430 | [Image:Predator.png](/Image:Predator.png.md "wikilink") |
| Reefer     | 453 | [Image:Reefer.png](/Image:Reefer.png.md "wikilink")     |
| Speeder    | 452 | [Image:Speeder.png](/Image:Speeder.png.md "wikilink")   |
| Squalo     | 446 | [Image:Squalo.png](/Image:Squalo.png.md "wikilink")     |
| Tropic     | 454 | [Image:Tropic.png](/Image:Tropic.png.md "wikilink")     |

Land vehicles
-------------

|                                                                                   |                                                                                    |                                                                                      |
|-----------------------------------------------------------------------------------|------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------|
| ### Bikes                                                                         
                                                                                    
 | Name          | ID  | Image                                                   |  
 |---------------|-----|---------------------------------------------------------|  
 | BF-400        | 581 | [Image:Bf400.png](/Image:Bf400.png.md "wikilink")       |  
 | Bike          | 509 | [Image:Bike.png](/Image:Bike.png.md "wikilink")         |  
 | BMX           | 481 | [Image:Bmx.png](/Image:Bmx.png.md "wikilink")           |  
 | Faggio        | 462 | [Image:Faggio.png](/Image:Faggio.png.md "wikilink")     |  
 | FCR-900       | 521 | [Image:Fcr900.png](/Image:Fcr900.png.md "wikilink")     |  
 | Freeway       | 463 | [Image:Freeway.png](/Image:Freeway.png.md "wikilink")   |  
 | Mountain Bike | 510 | [Image:Mtbike.png](/Image:Mtbike.png.md "wikilink")     |  
 | NRG-500       | 522 | [Image:Nrg500.png](/Image:Nrg500.png.md "wikilink")     |  
 | PCJ-600       | 461 | [Image:Pcj600.png](/Image:Pcj600.png.md "wikilink")     |  
 | Pizza Boy     | 448 | [Image:Pizzaboy.png](/Image:Pizzaboy.png.md "wikilink") |  
 | Sanchez       | 468 | [Image:Sanchez.png](/Image:Sanchez.png.md "wikilink")   |  
 | Wayfarer      | 586 | [Image:Wayfarer.png](/Image:Wayfarer.png.md "wikilink") |  | ### 2-Door & Compact cars                                                          
                                                                                                                                                                         
                                                                                     | Name           | ID  | Image                                                   |  
                                                                                     |----------------|-----|---------------------------------------------------------|  
                                                                                     | Alpha          | 602 | [Image:Alpha.png](/Image:Alpha.png.md "wikilink")       |  
                                                                                     | Blista Compact | 496 | [Image:Blistac.png](/Image:Blistac.png.md "wikilink")   |  
                                                                                     | Bravura        | 401 | [Image:Bravura.png](/Image:Bravura.png.md "wikilink")   |  
                                                                                     | Buccaneer      | 518 | [Image:Buccanee.png](/Image:Buccanee.png.md "wikilink") |  
                                                                                     | Cadrona        | 527 | [Image:Cadrona.png](/Image:Cadrona.png.md "wikilink")   |  
                                                                                     | Club           | 589 | [Image:Club.png](/Image:Club.png.md "wikilink")         |  
                                                                                     | Esperanto      | 419 | [Image:Esperant.png](/Image:Esperant.png.md "wikilink") |  
                                                                                     | Euros          | 587 | [Image:Euros.png](/Image:Euros.png.md "wikilink")       |  
                                                                                     | Feltzer        | 533 | [Image:Feltzer.png](/Image:Feltzer.png.md "wikilink")   |  
                                                                                     | Fortune        | 526 | [Image:Fortune.png](/Image:Fortune.png.md "wikilink")   |  
                                                                                     | Hermes         | 474 | [Image:Hermes.png](/Image:Hermes.png.md "wikilink")     |  
                                                                                     | Hustler        | 545 | [Image:Hustler.png](/Image:Hustler.png.md "wikilink")   |  
                                                                                     | Majestic       | 517 | [Image:Majestic.png](/Image:Majestic.png.md "wikilink") |  
                                                                                     | Manana         | 410 | [Image:Manana.png](/Image:Manana.png.md "wikilink")     |  
                                                                                     | Picador        | 600 | [Image:Picador.png](/Image:Picador.png.md "wikilink")   |  
                                                                                     | Previon        | 436 | [Image:Previon.png](/Image:Previon.png.md "wikilink")   |  
                                                                                     | Stallion       | 439 | [Image:Stallion.png](/Image:Stallion.png.md "wikilink") |  
                                                                                     | Tampa          | 549 | [Image:Tampa.png](/Image:Tampa.png.md "wikilink")       |  
                                                                                     | Virgo          | 491 | [Image:Virgo.png](/Image:Virgo.png.md "wikilink")       |  | ### 4-Door & Luxury cars                                                             
                                                                                                                                                                                                                                                                
                                                                                                                                                                          | Name             | ID  | Image                                                   |  
                                                                                                                                                                          |------------------|-----|---------------------------------------------------------|  
                                                                                                                                                                          | Admiral          | 445 | [Image:Admiral.png](/Image:Admiral.png.md "wikilink")   |  
                                                                                                                                                                          | Damaged Glendale | 604 | [Image:Glenshit.png](/Image:Glenshit.png.md "wikilink") |  
                                                                                                                                                                          | Elegant          | 507 | [Image:Elegant.png](/Image:Elegant.png.md "wikilink")   |  
                                                                                                                                                                          | Emperor          | 585 | [Image:Emperor.png](/Image:Emperor.png.md "wikilink")   |  
                                                                                                                                                                          | Glendale         | 466 | [Image:Glendale.png](/Image:Glendale.png.md "wikilink") |  
                                                                                                                                                                          | Greenwood        | 492 | [Image:Greenwoo.png](/Image:Greenwoo.png.md "wikilink") |  
                                                                                                                                                                          | Intruder         | 546 | [Image:Intruder.png](/Image:Intruder.png.md "wikilink") |  
                                                                                                                                                                          | Merit            | 551 | [Image:Merit.png](/Image:Merit.png.md "wikilink")       |  
                                                                                                                                                                          | Nebula           | 516 | [Image:Nebula.png](/Image:Nebula.png.md "wikilink")     |  
                                                                                                                                                                          | Oceanic          | 467 | [Image:Oceanic.png](/Image:Oceanic.png.md "wikilink")   |  
                                                                                                                                                                          | Premier          | 426 | [Image:Premier.png](/Image:Premier.png.md "wikilink")   |  
                                                                                                                                                                          | Primo            | 547 | [Image:Primo.png](/Image:Primo.png.md "wikilink")       |  
                                                                                                                                                                          | Sentinel         | 405 | [Image:Sentinel.png](/Image:Sentinel.png.md "wikilink") |  
                                                                                                                                                                          | Stafford         | 580 | [Image:Stafford.png](/Image:Stafford.png.md "wikilink") |  
                                                                                                                                                                          | Stretch          | 409 | [Image:Stretch.png](/Image:Stretch.png.md "wikilink")   |  
                                                                                                                                                                          | Sunrise          | 550 | [Image:Sunrise.png](/Image:Sunrise.png.md "wikilink")   |  
                                                                                                                                                                          | Tahoma           | 566 | [Image:Tahoma.png](/Image:Tahoma.png.md "wikilink")     |  
                                                                                                                                                                          | Vincent          | 540 | [Image:Vincent.png](/Image:Vincent.png.md "wikilink")   |  
                                                                                                                                                                          | Washington       | 421 | [Image:Washing.png](/Image:Washing.png.md "wikilink")   |  
                                                                                                                                                                          | Willard          | 529 | [Image:Willard.png](/Image:Willard.png.md "wikilink")   |  |

|                                                                                 |                                                                                   |                                                                                       |                                                                                      |                                                                                 |
|---------------------------------------------------------------------------------|-----------------------------------------------------------------------------------|---------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------|---------------------------------------------------------------------------------|
| ### Civil service                                                               
                                                                                  
 | Name        | ID  | Image                                                   |  
 |-------------|-----|---------------------------------------------------------|  
 | Baggage     | 485 | [Image:Baggage.png](/Image:Baggage.png.md "wikilink")   |  
 | Bus         | 431 | [Image:Bus.png](/Image:Bus.png.md "wikilink")           |  
 | Cabbie      | 438 | [Image:Cabbie.png](/Image:Cabbie.png.md "wikilink")     |  
 | Coach       | 437 | [Image:Coach.png](/Image:Coach.png.md "wikilink")       |  
 | Sweeper     | 574 | [Image:Sweeper.png](/Image:Sweeper.png.md "wikilink")   |  
 | Taxi        | 420 | [Image:Taxi.png](/Image:Taxi.png.md "wikilink")         |  
 | Towtruck    | 525 | [Image:Towtruck.png](/Image:Towtruck.png.md "wikilink") |  
 | Trashmaster | 408 | [Image:Trash.png](/Image:Trash.png.md "wikilink")       |  
 | Utility Van | 552 | [Image:Utility.png](/Image:Utility.png.md "wikilink")   |  | ### Government vehicles                                                           
                                                                                                                                                                      
                                                                                   | Name          | ID  | Image                                                   |  
                                                                                   |---------------|-----|---------------------------------------------------------|  
                                                                                   | Ambulance     | 416 | [Image:Ambulan.png](/Image:Ambulan.png.md "wikilink")   |  
                                                                                   | Barracks      | 433 | [Image:Barracks.png](/Image:Barracks.png.md "wikilink") |  
                                                                                   | Enforcer      | 427 | [Image:Enforcer.png](/Image:Enforcer.png.md "wikilink") |  
                                                                                   | FBI Rancher   | 490 | [Image:Fbiranch.png](/Image:Fbiranch.png.md "wikilink") |  
                                                                                   | FBI Truck     | 528 | [Image:Fbitruck.png](/Image:Fbitruck.png.md "wikilink") |  
                                                                                   | Fire Truck    | 407 | [Image:Firetruk.png](/Image:Firetruk.png.md "wikilink") |  
                                                                                   | Fire Truck    | 544 | [Image:Firela.png](/Image:Firela.png.md "wikilink")     |  
                                                                                   | HPV1000       | 523 | [Image:Hpv1000.png](/Image:Hpv1000.png.md "wikilink")   |  
                                                                                   | Patriot       | 470 | [Image:Patriot.png](/Image:Patriot.png.md "wikilink")   |  
                                                                                   | Police LS     | 596 | [Image:Policels.png](/Image:Policels.png.md "wikilink") |  
                                                                                   | Police LV     | 598 | [Image:Policelv.png](/Image:Policelv.png.md "wikilink") |  
                                                                                   | Police Ranger | 599 | [Image:Policeru.png](/Image:Policeru.png.md "wikilink") |  
                                                                                   | Police SF     | 597 | [Image:Policesf.png](/Image:Policesf.png.md "wikilink") |  
                                                                                   | Rhino         | 432 | [Image:Rhino.png](/Image:Rhino.png.md "wikilink")       |  
                                                                                   | S.W.A.T.      | 601 | [Image:Swatvan.png](/Image:Swatvan.png.md "wikilink")   |  
                                                                                   | Securicar     | 428 | [Image:Securica.png](/Image:Securica.png.md "wikilink") |  | ### Heavy & Utility trucks                                                            
                                                                                                                                                                                                                                                              
                                                                                                                                                                       | Name              | ID  | Image                                                   |  
                                                                                                                                                                       |-------------------|-----|---------------------------------------------------------|  
                                                                                                                                                                       | Benson            | 499 | [Image:Benson.png](/Image:Benson.png.md "wikilink")     |  
                                                                                                                                                                       | Black Boxville    | 609 | [Image:Boxburg.png](/Image:Boxburg.png.md "wikilink")   |  
                                                                                                                                                                       | Boxville          | 498 | [Image:Boxville.png](/Image:Boxville.png.md "wikilink") |  
                                                                                                                                                                       | Cement Truck      | 524 | [Image:Cement.png](/Image:Cement.png.md "wikilink")     |  
                                                                                                                                                                       | Combine Harvester | 532 | [Image:Combine.png](/Image:Combine.png.md "wikilink")   |  
                                                                                                                                                                       | DFT-30            | 578 | [Image:Dft30.png](/Image:Dft30.png.md "wikilink")       |  
                                                                                                                                                                       | Dozer             | 486 | [Image:Dozer.png](/Image:Dozer.png.md "wikilink")       |  
                                                                                                                                                                       | Dumper            | 406 | [Image:Dumper.png](/Image:Dumper.png.md "wikilink")     |  
                                                                                                                                                                       | Dune              | 573 | [Image:Dune.png](/Image:Dune.png.md "wikilink")         |  
                                                                                                                                                                       | Flatbed           | 455 | [Image:Flatbed.png](/Image:Flatbed.png.md "wikilink")   |  
                                                                                                                                                                       | Hotdog            | 588 | [Image:Hotdog.png](/Image:Hotdog.png.md "wikilink")     |  
                                                                                                                                                                       | Linerunner        | 403 | [Image:Linerun.png](/Image:Linerun.png.md "wikilink")   |  
                                                                                                                                                                       | Mr. Whoopee       | 423 | [Image:Mrwhoop.png](/Image:Mrwhoop.png.md "wikilink")   |  
                                                                                                                                                                       | Mule              | 414 | [Image:Mule.png](/Image:Mule.png.md "wikilink")         |  
                                                                                                                                                                       | Packer            | 443 | [Image:Packer.png](/Image:Packer.png.md "wikilink")     |  
                                                                                                                                                                       | Roadtrain         | 515 | [Image:Rdtrain.png](/Image:Rdtrain.png.md "wikilink")   |  
                                                                                                                                                                       | Tanker            | 514 | [Image:Tanker.png](/Image:Tanker.png.md "wikilink")     |  
                                                                                                                                                                       | Tractor           | 531 | [Image:Tractor.png](/Image:Tractor.png.md "wikilink")   |  
                                                                                                                                                                       | Yankee            | 456 | [Image:Yankee.png](/Image:Yankee.png.md "wikilink")     |  | ### Light trucks & Vans                                                              
                                                                                                                                                                                                                                                                                                                                                     
                                                                                                                                                                                                                                                               | Name             | ID  | Image                                                   |  
                                                                                                                                                                                                                                                               |------------------|-----|---------------------------------------------------------|  
                                                                                                                                                                                                                                                               | Berkley's RC Van | 459 | [Image:Topfun.png](/Image:Topfun.png.md "wikilink")     |  
                                                                                                                                                                                                                                                               | Bobcat           | 422 | [Image:Bobcat.png](/Image:Bobcat.png.md "wikilink")     |  
                                                                                                                                                                                                                                                               | Burrito          | 482 | [Image:Burrito.png](/Image:Burrito.png.md "wikilink")   |  
                                                                                                                                                                                                                                                               | Damaged Sadler   | 605 | [Image:Sadlshit.png](/Image:Sadlshit.png.md "wikilink") |  
                                                                                                                                                                                                                                                               | Forklift         | 530 | [Image:Forklift.png](/Image:Forklift.png.md "wikilink") |  
                                                                                                                                                                                                                                                               | Moonbeam         | 418 | [Image:Moonbeam.png](/Image:Moonbeam.png.md "wikilink") |  
                                                                                                                                                                                                                                                               | Mower            | 572 | [Image:Mower.png](/Image:Mower.png.md "wikilink")       |  
                                                                                                                                                                                                                                                               | News Van         | 582 | [Image:Newsvan.png](/Image:Newsvan.png.md "wikilink")   |  
                                                                                                                                                                                                                                                               | Pony             | 413 | [Image:Pony.png](/Image:Pony.png.md "wikilink")         |  
                                                                                                                                                                                                                                                               | Rumpo            | 440 | [Image:Rumpo.png](/Image:Rumpo.png.md "wikilink")       |  
                                                                                                                                                                                                                                                               | Sadler           | 543 | [Image:Sadler.png](/Image:Sadler.png.md "wikilink")     |  
                                                                                                                                                                                                                                                               | Tug              | 583 | [Image:Tug.png](/Image:Tug.png.md "wikilink")           |  
                                                                                                                                                                                                                                                               | Walton           | 478 | [Image:Walton.png](/Image:Walton.png.md "wikilink")     |  
                                                                                                                                                                                                                                                               | Yosemite         | 554 | [Image:Yosemite.png](/Image:Yosemite.png.md "wikilink") |  | ### SUVs & Wagons                                                               
                                                                                                                                                                                                                                                                                                                                                                                                                                       
                                                                                                                                                                                                                                                                                                                                                      | Name        | ID  | Image                                                   |  
                                                                                                                                                                                                                                                                                                                                                      |-------------|-----|---------------------------------------------------------|  
                                                                                                                                                                                                                                                                                                                                                      | Huntley     | 579 | [Image:Huntley.png](/Image:Huntley.png.md "wikilink")   |  
                                                                                                                                                                                                                                                                                                                                                      | Landstalker | 400 | [Image:Landstal.png](/Image:Landstal.png.md "wikilink") |  
                                                                                                                                                                                                                                                                                                                                                      | Perennial   | 404 | [Image:Peren.png](/Image:Peren.png.md "wikilink")       |  
                                                                                                                                                                                                                                                                                                                                                      | Rancher     | 489 | [Image:Rancher.png](/Image:Rancher.png.md "wikilink")   |  
                                                                                                                                                                                                                                                                                                                                                      | Rancher     | 505 | [Image:Rnchlure.png](/Image:Rnchlure.png.md "wikilink") |  
                                                                                                                                                                                                                                                                                                                                                      | Regina      | 479 | [Image:Regina.png](/Image:Regina.png.md "wikilink")     |  
                                                                                                                                                                                                                                                                                                                                                      | Romero      | 442 | [Image:Romero.png](/Image:Romero.png.md "wikilink")     |  
                                                                                                                                                                                                                                                                                                                                                      | Solair      | 458 | [Image:Solair.png](/Image:Solair.png.md "wikilink")     |  |

|                                                                               |                                                                           |                                                                                     |
|-------------------------------------------------------------------------------|---------------------------------------------------------------------------|-------------------------------------------------------------------------------------|
| ### Lowriders                                                                 
                                                                                
 | Name      | ID  | Image                                                   |  
 |-----------|-----|---------------------------------------------------------|  
 | Blade     | 536 | [Image:Blade.png](/Image:Blade.png.md "wikilink")       |  
 | Broadway  | 575 | [Image:Broadway.png](/Image:Broadway.png.md "wikilink") |  
 | Remington | 534 | [Image:Remingtn.png](/Image:Remingtn.png.md "wikilink") |  
 | Savanna   | 567 | [Image:Savanna.png](/Image:Savanna.png.md "wikilink")   |  
 | Slamvan   | 535 | [Image:Slamvan.png](/Image:Slamvan.png.md "wikilink")   |  
 | Tornado   | 576 | [Image:Tornado.png](/Image:Tornado.png.md "wikilink")   |  
 | Voodoo    | 412 | [Image:Voodoo.png](/Image:Voodoo.png.md "wikilink")     |  | ### Muscle cars                                                           
                                                                                                                                                            
                                                                                 | Name    | ID  | Image                                                 |  
                                                                                 |---------|-----|-------------------------------------------------------|  
                                                                                 | Buffalo | 402 | [Image:Buffalo.png](/Image:Buffalo.png.md "wikilink") |  
                                                                                 | Clover  | 542 | [Image:Clover.png](/Image:Clover.png.md "wikilink")   |  
                                                                                 | Phoenix | 603 | [Image:Phoenix.png](/Image:Phoenix.png.md "wikilink") |  
                                                                                 | Sabre   | 475 | [Image:Sabre.png](/Image:Sabre.png.md "wikilink")     |  | ### Street racers                                                                   
                                                                                                                                                                                                                                                  
                                                                                                                                                             | Name            | ID  | Image                                                   |  
                                                                                                                                                             |-----------------|-----|---------------------------------------------------------|  
                                                                                                                                                             | Banshee         | 429 | [Image:Banshee.png](/Image:Banshee.png.md "wikilink")   |  
                                                                                                                                                             | Bullet          | 541 | [Image:Bullet.png](/Image:Bullet.png.md "wikilink")     |  
                                                                                                                                                             | Cheetah         | 415 | [Image:Cheetah.png](/Image:Cheetah.png.md "wikilink")   |  
                                                                                                                                                             | Comet           | 480 | [Image:Comet.png](/Image:Comet.png.md "wikilink")       |  
                                                                                                                                                             | Elegy           | 562 | [Image:Elegy.png](/Image:Elegy.png.md "wikilink")       |  
                                                                                                                                                             | Flash           | 565 | [Image:Flash.png](/Image:Flash.png.md "wikilink")       |  
                                                                                                                                                             | Hotknife        | 434 | [Image:Hotknife.png](/Image:Hotknife.png.md "wikilink") |  
                                                                                                                                                             | Hotring Racer   | 494 | [Image:Hotring.png](/Image:Hotring.png.md "wikilink")   |  
                                                                                                                                                             | Hotring Racer 2 | 502 | [Image:Hotrina.png](/Image:Hotrina.png.md "wikilink")   |  
                                                                                                                                                             | Hotring Racer 3 | 503 | [Image:Hotrinb.png](/Image:Hotrinb.png.md "wikilink")   |  
                                                                                                                                                             | Infernus        | 411 | [Image:411.png](/Image:411.png.md "wikilink")           |  
                                                                                                                                                             | Jester          | 559 | [Image:Jester.png](/Image:Jester.png.md "wikilink")     |  
                                                                                                                                                             | Stratum         | 561 | [Image:Stratum.png](/Image:Stratum.png.md "wikilink")   |  
                                                                                                                                                             | Sultan          | 560 | [Image:Sultan.png](/Image:Sultan.png.md "wikilink")     |  
                                                                                                                                                             | Super GT        | 506 | [Image:Supergt.png](/Image:Supergt.png.md "wikilink")   |  
                                                                                                                                                             | Turismo         | 451 | [Image:Turismo.png](/Image:Turismo.png.md "wikilink")   |  
                                                                                                                                                             | Uranus          | 558 | [Image:Uranus.png](/Image:Uranus.png.md "wikilink")     |  
                                                                                                                                                             | Windsor         | 555 | [Image:Windsor.png](/Image:Windsor.png.md "wikilink")   |  
                                                                                                                                                             | ZR-350          | 477 | [Image:Zr350.png](/Image:Zr350.png.md "wikilink")       |  |

|                                                                               |                                                                                     |                                                                                           |
|-------------------------------------------------------------------------------|-------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------|
| ### RC Vehicles                                                               
                                                                                
 | Name      | ID  | Image                                                   |  
 |-----------|-----|---------------------------------------------------------|  
 | RC Bandit | 441 | [Image:Rcbandit.png](/Image:Rcbandit.png.md "wikilink") |  
 | RC Baron  | 464 | [Image:Rcbaron.png](/Image:Rcbaron.png.md "wikilink")   |  
 | RC Cam    | 594 | [Image:Rccam.png](/Image:Rccam.png.md "wikilink")       |  
 | RC Goblin | 501 | [Image:Rcgoblin.png](/Image:Rcgoblin.png.md "wikilink") |  
 | RC Raider | 465 | [Image:Rcraider.png](/Image:Rcraider.png.md "wikilink") |  
 | RC Tiger  | 564 | [Image:Rctiger.png](/Image:Rctiger.png.md "wikilink")   |  | ### Trailers                                                                        
                                                                                                                                                                      
                                                                                 | Name            | ID  | Image                                                   |  
                                                                                 |-----------------|-----|---------------------------------------------------------|  
                                                                                 | Baggage Trailer | 606 | [Image:Bagboxa.png](/Image:Bagboxa.png.md "wikilink")   |  
                                                                                 | Baggage Trailer | 607 | [Image:Bagboxb.png](/Image:Bagboxb.png.md "wikilink")   |  
                                                                                 | Farm Trailer    | 610 | [Image:Farmtr1.png](/Image:Farmtr1.png.md "wikilink")   |  
                                                                                 | Petrol trailer  | 584 | [Image:Petrotr.png](/Image:Petrotr.png.md "wikilink")   |  
                                                                                 | Trailer         | 611 | [Image:Utiltr1.png](/Image:Utiltr1.png.md "wikilink")   |  
                                                                                 | Trailer         | 608 | [Image:Tugstair.png](/Image:Tugstair.png.md "wikilink") |  
                                                                                 | Trailer 1       | 435 | [Image:Artict1.png](/Image:Artict1.png.md "wikilink")   |  
                                                                                 | Trailer 2       | 450 | [Image:Artict2.png](/Image:Artict2.png.md "wikilink")   |  
                                                                                 | Trailer 3       | 591 | [Image:Artict3.png](/Image:Artict3.png.md "wikilink")   |  
                                                                                 ||                                                                                   | ### Trains & Railroad cars                                                                
                                                                                                                                                                                                                                                                  
                                                                                                                                                                       | Name                  | ID  | Image                                                   |  
                                                                                                                                                                       |-----------------------|-----|---------------------------------------------------------|  
                                                                                                                                                                       | Box Freight           | 590 | [Image:Freibox.png](/Image:Freibox.png.md "wikilink")   |  
                                                                                                                                                                       | Brown Streak          | 538 | [Image:Streak.png](/Image:Streak.png.md "wikilink")     |  
                                                                                                                                                                       | Brown Streak Carriage | 570 | [Image:Streakc.png](/Image:Streakc.png.md "wikilink")   |  
                                                                                                                                                                       | Flat Freight          | 569 | [Image:Freiflat.png](/Image:Freiflat.png.md "wikilink") |  
                                                                                                                                                                       | Freight               | 537 | [Image:Freight.png](/Image:Freight.png.md "wikilink")   |  
                                                                                                                                                                       | Tram                  | 449 | [Image:Tram.png](/Image:Tram.png.md "wikilink")         |  |

Recreational
------------

| Name             | ID  | Image                                                   |
|------------------|-----|---------------------------------------------------------|
| Bandito          | 568 | [Image:Bandito.png](/Image:Bandito.png.md "wikilink")   |
| BF Injection     | 424 | [Image:Bfinject.png](/Image:Bfinject.png.md "wikilink") |
| Bloodring Banger | 504 | [Image:Bloodra.png](/Image:Bloodra.png.md "wikilink")   |
| Caddy            | 457 | [Image:Caddy.png](/Image:Caddy.png.md "wikilink")       |
| Camper           | 483 | [Image:Camper.png](/Image:Camper.png.md "wikilink")     |
| Journey          | 508 | [Image:Journey.png](/Image:Journey.png.md "wikilink")   |
| Kart             | 571 | [Image:Kart.png](/Image:Kart.png.md "wikilink")         |
| Mesa             | 500 | [Image:Mesa.png](/Image:Mesa.png.md "wikilink")         |
| Monster          | 444 | [Image:Monster.png](/Image:Monster.png.md "wikilink")   |
| Monster 2        | 556 | [Image:Monstera.png](/Image:Monstera.png.md "wikilink") |
| Monster 3        | 557 | [Image:Monsterb.png](/Image:Monsterb.png.md "wikilink") |
| Quadbike         | 471 | [Image:Quad.png](/Image:Quad.png.md "wikilink")         |
| Sandking         | 495 | [Image:Sandking.png](/Image:Sandking.png.md "wikilink") |
| Vortex           | 539 | [Image:Vortex.png](/Image:Vortex.png.md "wikilink")     |

Vehicle Functions
-----------------

See Also
--------

[ID Lists](/id.md "wikilink") [tr:Araç ID'leri](/tr:Araç_ID'leri.md "wikilink") [it:ID Veicoli](/it:ID_Veicoli.md "wikilink") [ru:Vehicle IDs](/ru:Vehicle_IDs.md "wikilink") [de:Fahrzeug IDs](/de:Fahrzeug_IDs.md "wikilink")

[Category:ID Lists](/Category:ID_Lists.md "wikilink")
