<onlyinclude>This branch makes it possible to make your own train tracks.

|                    |                                                                                              |
|--------------------|----------------------------------------------------------------------------------------------|
| **Status**         | <span style="color:orange">Work in progress</span>                                           |
| **Branch**         | [custom-train-tracks](https://github.com/multitheftauto/mtasa-blue/tree/custom-train-tracks) |
| **Branch version** | 1.6                                                                                          |

### Functions

-   [createTrack](/docs/createTrack.md "wikilink")
-   [removeDefaultTrack](/docs/removeDefaultTrack.md "wikilink")
-   [resetDefaultTrack](/docs/resetDefaultTrack.md "wikilink")
-   [setTrackLength](/docs/setTrackLength.md "wikilink")
-   [getTrackLength](/docs/getTrackLength.md "wikilink")

### Media

-   [MTA:SA Custom train tracks \#1](https://www.youtube.com/watch?v=S_Q3Gk4jVr0&user=UCbl-5xYsT5KwnrfGdW9LYPQ)</onlyinclude>

Development
-----------

### API

``` lua
-- trainNode is a Vector3, or table of three coordinates
-- nodes is a table of trainNodes

track = TrainTrack(...nodes) -- createTrack(node1, node2, node3, ...)
track:getNodes() returns a table of Vector3s
track:getLength() -- getTrainTrack(track)
-- Default track functions
TrainTrack.removeDefault(int trackID)
TrainTrack.resetDefault(int trackID)

-- These functions already exist, but I'm not sure how these lengths are used or what they are for
```

### Findings

All information related custom train tracks are stored here.

#### Files

    MTA10/game_sa
    ** CTrainTrackManagerSA.{cpp,h}
    ** CTrainTrackSA.{cpp,h}

    MTA10/mods/shared_logic
    ** CClientTrainTrack.{cpp,h}
    ** luadefs/CLuaTrainTrackDefs.{cpp,h} -- contain definitions for the Lua API

    MTA10/sdk/game
    ** CTrainTrack.h
    ** CTrainTrackManager.h

    MTA10_Server/mods/deathmatch/logic
    ** CTrainTrackManager.{cpp,h}
    ** CTrainTrack.{cpp,h}
    ** luadefs/CLuaTrainTrackDefs.{cpp,h} -- contain definitions for the Lua API

#### m\_OriginalTrainTrackData

The [m\_OriginalTrainTrackData array](https://pastebin.mtasa.com/748483851) contains the same values in CTrainTrackManager.cpp and CTrainTrackManagerSA.cpp.

The Init function is structured like so (pay special attention to the comments):

    typedef struct
    {
        short sX;               // x coordinate times 8
        short sY;               // y coordinate times 8
        short sZ;               // z coordinate times 8
        float fRailDistance;    // on-rail distance ( leave the client to calculate this )
        void Init ( short sX, short sY, short sZ, unsigned short sRailDistance, WORD padding )
        {
            this->sX = sX;
            this->sY = sY;
            this->sZ = sZ;
            this->fRailDistance = sRailDistance;
        }
    } SRailNode;

We need to make sense of the following things:

-   Why is padding an argument here? (It doesn't do anything, and when Init() is called, real values are provided)
-   Why are values repeated several times?
-   Why does the last repeat have slightly different values?

### Issues

-   There may be some issues (relating to infinite loops) if a track runs across another or crosses another
    -   Infinite loop occurs at 006f8fda, see [call stack](http://i.imgur.com/HvBWAFm.png). Occurs when a track of two nodes have same x/y, but different z. Only occurs for tracks that ONLY consist of nodes atop each other.
        -   Possible solution: when creation tracks, ensure that atleast one of the nodes has a different x/y to any other node.
-   Tracks may not be cleaned up -&gt; See CTrainTrackManager::ResetTracks
-   See CTrainTrackManager and CTrainTrackManagerSA - why is this file so big? Why are coordinates provided multiple times for the same track? Which ones are right?
-   ~~int CWorldSA::FindClosestRailTrackNode needs updating. It needs to use MAX\_TOTAL\_TRACKS and the train manager.~~ [See 09e3ee8f25810c17742](https://github.com/multitheftauto/mtasa-blue/commit/09e3ee8f25810c17742728f038786b6a223c5296)

### Re-merge

<section name="This section has been archived" collapse="true">
|                    |                                                                                                                                         |
|--------------------|-----------------------------------------------------------------------------------------------------------------------------------------|
| **Status**         | <span style="color:red">Abandoned</span>                                                                                                |
| **Branch**         | [custom-train-tracks-old](https://github.com/multitheftauto/mtasa-blue/tree/custom-train-tracks-old) (renamed from custom-train-tracks) |
| **Branch version** | 1.4                                                                                                                                     |

The old **custom-train-tracks** branch contains commits cherry-picked and other merges from the 1.4 branch. The first task in updating this branch is to distinguish between merge commits and actual branch commits:

-   new branch [45d1a266e8f3e50d9605610a32210a9a9a6e145a](https://github.com/multitheftauto/mtasa-blue/commit/45d1a266e8f3e50d9605610a32210a9a9a6e145a)
-   Added missing files and fixed compile errors [e2c5fcb83fa7df633f040dc6b0c048e2cd72bbb3](https://github.com/multitheftauto/mtasa-blue/commit/e2c5fcb83fa7df633f040dc6b0c048e2cd72bbb3)
-   Small fix [76248682a3fdf8bf24c5d7e73f2bac4536f93069](https://github.com/multitheftauto/mtasa-blue/commit/76248682a3fdf8bf24c5d7e73f2bac4536f93069)
-   ... Fixed crash 0013368B, 00133606, a memory leak a… [88b64d51526b342e22c4581ad9c2fa6b1632c2e1](https://github.com/multitheftauto/mtasa-blue/commit/88b64d51526b342e22c4581ad9c2fa6b1632c2e1)
-   ... Fixed a crash with applying upgrades to vehicle… [3dd27775c0d371339337a162e59ef8320a6c6bb5](https://github.com/multitheftauto/mtasa-blue/commit/3dd27775c0d371339337a162e59ef8320a6c6bb5)
-   ... Fixed \#5618 - "Heli Rotors are not in ghostmode… [38d4e2da33466fee7f199981db24056a086e3376](https://github.com/multitheftauto/mtasa-blue/commit/38d4e2da33466fee7f199981db24056a086e3376)
-   ... Fixed \#7801 - "warpPedIntoVehicle can cause des… [6a394e0dc265628ba328ab94ce00e40ff3409eff](https://github.com/multitheftauto/mtasa-blue/commit/6a394e0dc265628ba328ab94ce00e40ff3409eff)
-   ... Addendum to previous commit [7489405bbe5d590a3b6a259c5f49784238d1b739](https://github.com/multitheftauto/mtasa-blue/commit/7489405bbe5d590a3b6a259c5f49784238d1b739)
-   ... Fixed a recently introduced server crash when u… [70fa16ea69c398487085ab46dd5970fa723b0e27](https://github.com/multitheftauto/mtasa-blue/commit/70fa16ea69c398487085ab46dd5970fa723b0e27)
-   ... Applied patch from DirtY\_iCE - "vehicle upgrade… [e521b274325f15fc9d2bb0f6830edb15680a9582](https://github.com/multitheftauto/mtasa-blue/commit/e521b274325f15fc9d2bb0f6830edb15680a9582)
-   ... Fixed peds being ejected from vehicles and warp… [d0c6d1f8c4786c4f581ef5546f8ed7db60c401aa](https://github.com/multitheftauto/mtasa-blue/commit/d0c6d1f8c4786c4f581ef5546f8ed7db60c401aa)
-   ... Fixed \#7803 - “spoilers” [191491f2ccdc65157309c561d01c5920867f81c8](https://github.com/multitheftauto/mtasa-blue/commit/191491f2ccdc65157309c561d01c5920867f81c8)
-   ... Merged revisions(s) 5605-6091 from trunk [dc8f3ca4316d5da9212e752841c65fe328d88cf6](https://github.com/multitheftauto/mtasa-blue/commit/dc8f3ca4316d5da9212e752841c65fe328d88cf6)
-   Fixed some crashes [92a1f4290625b07b651166cd333d3c43dad7ab0f](https://github.com/multitheftauto/mtasa-blue/commit/92a1f4290625b07b651166cd333d3c43dad7ab0f)
-   ... Merged revision(s) 6092-6137 from trunk [61976a30a1edda6150d1840833ab8ac2d22ae59a](https://github.com/multitheftauto/mtasa-blue/commit/61976a30a1edda6150d1840833ab8ac2d22ae59a)

This means that there are only four commits that need to be merged into the new branch. ~~There is currently a packet issue introduced by the merge that needs to be fixed.~~

</section>
[Category: Development](/docs/Category:_Development.md "wikilink")
