Custom Variants
---------------

With the introduction of vehicle variants we now have the ability to add custom variants using custom models. Variants can be anything from different adverts to additional parts of the model.. [200px|thumb|left|Custom Infernus Variant](/Image:Infernus.png.md "wikilink")

How to Add Variants
-------------------

Adding variants requires modifying your DFF by adding a part of the model you wish to be a variant and naming it extra1, extra2, extra3, extra4 or extra5 then setting it's parent to the chassis\_dummy this tells GTA it has variant information and after this your variant will work in MTA.

Spawning Custom Variants
------------------------

Spawning custom variants is more complicated as we do not know the variants are there so the random variant spawner (TM) will not spawn the added variant.

A way around this is to implicitly specify which variant you require in createVehicle this will bypass our random variant spawner (TM) and allow you to spawn it.

Any invalid variant will show up as the default model with no variation.

GTA Variants
------------

| Vehicle Name     | Vehicle ID | Variants                                                                                                                             |
|------------------|------------|--------------------------------------------------------------------------------------------------------------------------------------|
| Ambulance        | 416        | Numbers: 0 = 37, 1 = 71                                                                                                              |
| Trailer 1        | 435        | Side Ads: 0 = Cok-o-Pops, 1 = Munky Juice, 2 = Hinterland, 3 = Zip, 4 = RS Haul, 5 = Ranch                                           |
| Trailer 2        | 450        | Contents: 0 = Filled with gravel/coal/stone                                                                                          |
| Bagboxb          | 607        | Contents: 0,1,2 = Various distributions of loose baggage                                                                             |
| Baggage          | 485        | Rear Cargo Items: 0 = Earmuffs, 1 = Small Case, 2 = Large Case                                                                       |
| Barracks         | 433        | Bed Covering: 0 = Opaque Fabric, 1 = Camo Netting                                                                                    |
| Benson           | 499        | Side Ads: 0 = Shady Industries, 1 = LSD, 2 = The Uphill Gardener, 3 = Discount Furniture                                             |
| BF-400           | 581        | Exhausts: 0 = Single Type1, 1 = Single Type2, 2 = Dual Type3 - Fairings (with Windshields): 3 = Half-size, 4 = Full-size             |
| BF Injection     | 424        | Body: 0 = Side Panels                                                                                                                |
| Bloodring Banger | 504        | Numbers/Roof Color: 0 = 328/White, 1 = 464/Check, 2 = 172/Check, 3 = 100/White, 4 = 284/White, 5 = 505/Check                         |
| Bobcat           | 422        | Bed Items: 0 = Spare Tire, 1 = Sprunk Cans                                                                                           |
| Burrito          | 482        | Roof Items: 0 = Roof Lights + Spoiler                                                                                                |
| Caddy            | 457        | Rear Cargo (Driver Side): 0 = Golfbag1, 1 = Satchel1, 2 = Golfbag2, Rear Cargo (Pass Side): 3 = Satchel2, 4 = Golfbag3, 5 = Golfbag4 |
| Camper           | 483        | 0 = Open Curtains & Second Bench Seat, 1 = Open Roof Vent, Closed Curtains, Bed in Back, Peace Sign                                  |
| Cheetah          | 415        | Side Mirrors: 0 = Single, Placed High, 1 = Dual, Placed Normally                                                                     |
| Coach            | 437        | Name on Side: 0 = Big O Tours, 1 = Bikini Line                                                                                       |
| Coastguard       | 472        | Various Items 0 = Items all Over, 1 = Items Grouped in Back, 2 = Items all Over + 2 Oars in Front                                    |
| FCR-900          | 521        | Exhausts: 0 = Single Type1, 1 = Dual Type1, 2 = Dual Type2, Fairings (with Windshields): 3 = Half-size, 4 = Full-size                |
| Fire Truck       | 407        | Numbers: 0 = 64, 1 = 16, 2 = 47                                                                                                      |
| Flatbed          | 455        | Numbers: 0 = 64, 1 = 16, 2 = 47                                                                                                      |
| Hotknife         | 434        | 0 = Partial Engine Cover                                                                                                             |
| Hotring Racer 2  | 502        | Numbers: 0 = 96, 1 = 67, 2 = 73, 3 = 52, 4 = 45, 5 = 14                                                                              |
| Hotring Racer 3  | 503        | Numbers: 0 = 82, 1 = 26, 2 = 65, 3 = 07, 4 = 36, 5 = 60                                                                              |
| Kart             | 571        | Body Panels: 0 = Both Sides, 1 = Steering Column                                                                                     |
| Launch           | 595        | Roofs: 0 = Over passenger section, 1 = Over driver section                                                                           |
| Marquis          | 484        | 0 = Windshield over Cabin Entrance                                                                                                   |
| Mesa             | 500        | 0 = Roof Over Back, 1 = Roll Bar in Back                                                                                             |
| Monster 2        | 556        | 0 = Roof Spoiler, 1 = Roof Lights, 2 = Roll Bar with Lights                                                                          |
| Monster 3        | 557        | 0 = Couldn't Determine 1 = Roof Lights                                                                                               |
| Mr. Whoopee      | 423        | Rear Sign: 0 = Cherry Popping Good, 1 = Slow Children Ahead                                                                          |
| Mule             | 414        | Side Ads: 0 = Toy Corner, 1 = Binco, 2 = Semi, 3 = Shafted Appliances                                                                |
| NRG-500          | 522        | Exhausts: 0 = Single Pair1, 1 = Single Pair2, 2 = Dual Pair2 - Fairings (with Windshields): 3 = Smooth, 4 = With Side Cutouts        |
| Patriot          | 470        | Cargo Area 0 = Low Cover, 1 = Roof/High Cover, 2 = Roll Bar                                                                          |
| Perennial        | 404        | Cargo Area 0 = Low Cover, 1 = Roof/High Cover, 2 = Roll Bar                                                                          |
| Picador          | 600        | Items in Bed: 0 = Planks, 1 = Sprunk Cans                                                                                            |
| Pony             | 413        | 0 = Sound System in Back                                                                                                             |
| Reefer           | 453        | Items in Back: 0 = Boxes of Fish, 1 = Bench                                                                                          |
| Romero           | 442        | Coffins: 0 = Brown Style1, 1 = Black Style2, 2 = Brown Style3                                                                        |
| Rumpo            | 440        | Side Ads: 0 = Cok-o-Pops, 1 = Harry Plums, 2 = Dick Goblin's, 3 = Final Build, 4 = Transfender, 5 = Wheel Arch Angels                |
| Sadler           | 543        | Items in Bed: 0 = Two Propane Tanks & Crate, 1 = Two Barrels, 2 = Sprunk Cans, 3 = Open Crates, 4+ = Empty bed                       |
| Damaged Sadler   | 605        | Items in Bed: 0 = Two Propane Tanks & Crate, 1 = Two Barrels, 2 = Sprunk Cans, 3 = Open Crates, 4+ = Empty bed                       |
| Securicar        | 428        | Side Logo: 0 = Chuff, 1 = Lock&Load                                                                                                  |
| Slamvan          | 535        | Steering Wheel: 0 = Normal, 1 = Chain (Default has none!)                                                                            |
| Stallion         | 439        | Roof: 0 = Hardtop, 1 = Softtop (up), 2 = Softtop (folded)                                                                            |
| Super GT         | 506        | 0 = Full Roof                                                                                                                        |
| S.W.A.T.         | 601        | Number: 0 = 1, 1 = 9, 2 = 6, 3 = 7                                                                                                   |
| Berkley's RC Van | 459        | 0 = Boxes of Toys in Back                                                                                                            |
| Tram             | 449        | 0,1,2,3 = (4 defined extras, but I don't know what they are)                                                                         |
| Trashmaster      | 408        | 0 = Some bits of trash sticking out of the back                                                                                      |
| Tug              | 583        | Case in Back: 0 = Red Case, 1 = Green Case                                                                                           |
| Utility Van      | 552        | 0 = Cones, Barrel in back + Cone lying on passenger side rail, 1 = Cones, Barrel in back + Cone lying on driver side rail            |
| Walton           | 478        | Items in Bed: 0 = Two Propane Tanks, 1 = Open Crates, 2 = Propane Tank and Barrel                                                    |
| Windsor          | 555        | 0 = Roof, 1 = No Roof                                                                                                                |
| Yankee           | 456        | Side Ads: 0 = Big Gas, 1 = RS Haul, 2 = Star Balls, 3 = Flower Power                                                                 |
| ZR-350           | 477        | 0 = Rear Spoiler                                                                                                                     |
| Vehicle Name     | Vehicle ID | Variants                                                                                                                             |
||

Above table serialized in Lua:

``` lua
local vehicleModelVariants={
  [404]={0,1,2},
  [407]={0,1,2},
  [408]={0},
  [413]={0},
  [414]={0,1,2,3},
  [415]={0,1},
  [416]={0,1},
  [422]={0,1},
  [423]={0,1},
  [424]={0},
  [428]={0,1},
  [433]={0,1},                                                                                                                                         
  [434]={0},                                                                                                                                           
  [435]={0,1,2,3,4,5},                                                                                                                                 
  [437]={0,1},                                                                                                                                         
  [439]={0,1,2},                                                                                                                                       
  [440]={0,1,2,3,4,5},                                                                                                                                 
  [442]={0,1,2},                                                                                                                                       
  [449]={0,1,2,3,4},                                                                                                                                   
  [450]={0},                                                                                                                                           
  [453]={0,1},                                                                                                                                         
  [455]={0,1,2},                                                                                                                                       
  [456]={0,1,2,3},                                                                                                                                     
  [457]={0,1,2,3,4,5},                                                                                                                                 
  [459]={0},                                                                                                                                           
  [470]={0,1,2},                                                                                                                                       
  [472]={0,1,2},                                                                                                                                       
  [477]={0},                                                                                                                                           
  [478]={0,1,2},                                                                                                                                       
  [482]={0},                                                                                                                                           
  [483]={0,1},                                                                                                                                         
  [484]={0},                                                                                                                                           
  [485]={0,1,2},                                                                                                                                       
  [499]={0,1,2,3},                                                                                                                                     
  [500]={0,1},                                                                                                                                         
  [502]={0,1,2,3,4,5},                                                                                                                                 
  [503]={0,1,2,3,4,5},                                                                                                                                 
  [504]={0,1,2,3,4,5},                                                                                                                                 
  [506]={0},                                                                                                                                           
  [521]={0,1,2,3,4},                                                                                                                                   
  [522]={0,1,2,3,4},                                                                                                                                   
  [535]={0,1},  
  [543]={0,1,2,3,4},                                                                                                                                       
  [552]={0,1},                                                                                                                                         
  [555]={0,1},                                                                                                                                         
  [556]={0,1,2},                                                                                                                                       
  [557]={0,1},                                                                                                                                         
  [571]={0,1},                                                                                                                                         
  [581]={0,1,2,3,4},                                                                                                                                   
  [583]={0,1},                                                                                                                                         
  [595]={0,1},                                                                                                                                         
  [600]={0,1},                                                                                                                                         
  [601]={0,1,2,3},                                                                                                                                     
  [605]={0,1,2,3,4},                                                                                                                                     
  [607]={0,1,2},                                                                                                                                       
}
```

[Category:ID Lists](/Category:ID_Lists.md "wikilink") [ru:Vehicle variants](/ru:Vehicle_variants.md "wikilink") [de:Fahrzeug Varianten](/de:Fahrzeug_Varianten.md "wikilink")
