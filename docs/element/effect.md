Effects list
------------

There are 82 effects.

``` lua
--A table containing all effect names.
local effectNames = {
"blood_heli","boat_prop","camflash","carwashspray","cement","cloudfast","coke_puff","coke_trail","cigarette_smoke",
"explosion_barrel","explosion_crate","explosion_door","exhale","explosion_fuel_car","explosion_large","explosion_medium",
"explosion_molotov","explosion_small","explosion_tiny","extinguisher","flame","fire","fire_med","fire_large","flamethrower",
"fire_bike","fire_car","gunflash","gunsmoke","insects","heli_dust","jetpack","jetthrust","nitro","molotov_flame",
"overheat_car","overheat_car_electric","prt_blood","prt_boatsplash","prt_bubble","prt_cardebris","prt_collisionsmoke",
"prt_glass","prt_gunshell","prt_sand","prt_sand2","prt_smokeII_3_expand","prt_smoke_huge","prt_spark","prt_spark_2",
"prt_splash","prt_wake","prt_watersplash","prt_wheeldirt","petrolcan","puke","riot_smoke","spraycan","smoke30lit","smoke30m",
"smoke50lit","shootlight","smoke_flare","tank_fire","teargas","teargasAD","tree_hit_fir","tree_hit_palm","vent","vent2",
"water_hydrant","water_ripples","water_speed","water_splash","water_splash_big","water_splsh_sml","water_swim","waterfall_end",
"water_fnt_tme","water_fountain","wallbust","WS_factorysmoke"
}
```

| Name                    | Description                                                               |
|-------------------------|---------------------------------------------------------------------------|
| blood\_heli             | bloody explosion                                                          |
| boat\_prop              | a surf                                                                    |
| camflash                | small flare                                                               |
| carwashspray            | steam, as on a carwash                                                    |
| cement                  | cement                                                                    |
| cloudfast               | fast clouds                                                               |
| coke\_puff              | puff of a coke                                                            |
| coke\_trail             | a pouring water                                                           |
| cigarette\_smoke        | a smoke from a cigarette                                                  |
| explosion\_barrel       | explosion and splinters of a box                                          |
| explosion\_crate        | explosion and splinters of the large box                                  |
| explosion\_door         | a smoke with sparks                                                       |
| exhale                  | a small smoke                                                             |
| explosion\_fuel\_car    | explosion, as from the machine                                            |
| explosion\_large        | the large explosion                                                       |
| explosion\_medium       | average explosion                                                         |
| explosion\_molotov      | explosion, as from a molotov cocktail                                     |
| explosion\_small        | small explosion                                                           |
| explosion\_tiny         | very small explosion                                                      |
| extinguisher            | foam of the fire extinguisher                                             |
| flame                   | small fire                                                                |
| fire                    | fire                                                                      |
| fire\_med               | average fire                                                              |
| fire\_large             | large fire                                                                |
| flamethrower            | fire of the flamethrower                                                  |
| fire\_bike              | fire, as from a burning motorcycle                                        |
| fire\_car               | fire, as from the burning machine                                         |
| gunflash                | as the bullet from a trunk takes off                                      |
| gunsmoke                | a smoke from a gun                                                        |
| insects                 | insects                                                                   |
| heli\_dust              | a dust, as from the helicopter                                            |
| jetpack                 | a jetpacks fire                                                           |
| jetthrust               | fire from the muffler of the machine, as during use of nitrogen           |
| nitro                   | nitro                                                                     |
| molotov\_flame          | fire from a Molotov Cocktail                                              |
| overheat\_car           | smoke from damaged car                                                    |
| overheat\_car\_electric | wrecked electro-machine                                                   |
| prt\_blood              | spark? maybe meant to be a mini red blood splash                          |
| prt\_boatsplash         | foam                                                                      |
| prt\_bubble             | bubble                                                                    |
| prt\_cardebris          | splinters from a box                                                      |
| prt\_collisionsmoke     | a dense white smoke                                                       |
| prt\_glass              | a crashing glass                                                          |
| prt\_gunshell           | shells                                                                    |
| prt\_sand               | sand, which was scattered                                                 |
| prt\_sand2              | there is less sand, than in previous animation                            |
| prt\_smokeII\_3\_expand | a grey smoke                                                              |
| prt\_smoke\_huge        | there is a lot of grey smoke                                              |
| prt\_spark              | of a spark                                                                |
| prt\_spark\_2           | the large sparks                                                          |
| prt\_splash             | burst                                                                     |
| prt\_wake               | a wave                                                                    |
| prt\_watersplash        | sparks                                                                    |
| prt\_wheeldirt          | sparks from wheels of the car                                             |
| petrolcan               | a jet                                                                     |
| puke                    | belch                                                                     |
| riot\_smoke             | there is a lot of smoke                                                   |
| spraycan                | spray                                                                     |
| smoke30lit              | a smoke                                                                   |
| smoke30m                | a rich smoke                                                              |
| smoke50lit              | more richer smoke                                                         |
| shootlight              | a light being shot out (used for searchlights), sparks and glass          |
| smoke\_flare            | a light being shot out, sparks and glass, it makes a good firework effect |
| tank\_fire              | a shot from the tank                                                      |
| teargas                 | gas, as from gas grenade                                                  |
| teargasAD               | gas, as from small gas grenade                                            |
| tree\_hit\_fir          | leaf falling                                                              |
| tree\_hit\_palm         | falling of pair large leafs                                               |
| vent                    | slowly dissipating a smoke                                                |
| vent2                   | practically too most                                                      |
| water\_hydrant          | the large flow of water                                                   |
| water\_ripples          | circles on water                                                          |
| water\_speed            | the large sparks from water                                               |
| water\_splash           | small sparks from water                                                   |
| water\_splash\_big      | average sparks                                                            |
| water\_splsh\_sml       | sparks, only them it is not visible almost                                |
| water\_swim             | small sparks at navigation                                                |
| waterfall\_end          | there is a lot of pair                                                    |
| water\_fnt\_tme         | the large flow of water                                                   |
| water\_fountain         | water of a fountain                                                       |
| wallbust                | a disappearing heap pair                                                  |
| WS\_factorysmoke        | smoke                                                                     |

Related scripting functions
---------------------------

### Client

-   [createEffect](/docs/createeffect.md "wikilink")
-   [setEffectSpeed](/docs/seteffectspeed.md "wikilink")
-   [getEffectSpeed](/docs/geteffectspeed.md "wikilink")
-   [setEffectDensity](/docs/seteffectdensity.md "wikilink")
-   [setEffectDensity](/docs/seteffectdensity.md "wikilink")

[Category:Element Types](/docs/category-element_types.md "wikilink") [ru:Element/Effect](/docs/ru-element/effect.md "wikilink")
