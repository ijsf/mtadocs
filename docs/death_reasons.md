The following death reasons are used by event like onPlayerWasted for the killerWeapon argument to describe the reason, why a ped died.
When a player was shot by a weapon, the respective weapon ID is the death reason ID. The weapon IDs can be found [here](/docs/weapons.md "wikilink").
:{|class=“wikitable sortable” style=“width: auto; table-layout: fixed;” |- !ID ! class=“unsortable” |Death reason ! class=“unsortable” |Additional info |- !19 |Rocket |Actual death reason / weapon ID when dying from a rocket launcher |- !37 |Burnt |This is used by a death by fire, even when the fire is created by a rocket explosion or a molotov |- !49 |Rammed | |- !50 |Ranover |This is also called when dying because of helicopter blades |- !51 |Explosion |This may sometimes also be used at an indirect death through an exploding rocket |- !52 |Driveby |This is NOT used for a driveby kill with e.g. the 'realdriveby' resource |- !53 |Drowned | |- !54 |Fall | |- !55 |Unknown |No known information about this death reason |- !56 |Melee |Seems to be never called (?); for an actual melee death, the fist weapon ID (0) is used (see [here](/docs/weapons.md "wikilink")) |- !57 |Weapon |Seems to be never called (?) |- !59 |Tank Grenade | |- !63 |Blown |Actual death reason when dying in a vehicle explosion |- |}

Death Reasons in lua table

``` lua
local deathReasons = {
    [19] = "Rocket",
    [37] = "Burnt",
    [49] = "Rammed",
    [50] = "Ranover/Helicopter Blades",
    [51] = "Explosion",
    [52] = "Driveby",
    [53] = "Drowned",
    [54] = "Fall",
    [55] = "Unknown",
    [56] = "Melee",
    [57] = "Weapon",
    [59] = "Tank Grenade",
    [63] = "Blown"
}
```

[ru:Death Reasons](/docs/ru-death_reasons.md "wikilink") [de:Todesgründe](/docs/de-todesgründe.md "wikilink")

[Category:ID Lists](/docs/category-id_lists.md "wikilink")
