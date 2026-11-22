# Required Functionality

1. Each area should have its own enemy management configuration.

2. Each area should have a configurable minimum enemy count.

3. Each area should have a configurable maximum enemy count.

4. The script should track how many living enemies currently exist inside each area.

5. If the enemy count falls below the configured minimum, the system should attempt to replenish enemies.

6. The system must never spawn enemies beyond the configured maximum.

7. Enemies should spawn inside their assigned area using designated spawn locations or spawn areas.

8. Enemies should be associated with the area they belong to so that enemies from one area are not counted toward another area's limits.

9. Enemy counts should update when enemies die, are destroyed, or are removed from the area.

10. The system should periodically verify enemy counts to recover from unexpected removals or failed spawn attempts.

## Required Changes you may have to make

* Area name.
* Enemy template in ServerStorage.
* Minimum enemy count.
* Maximum enemy count.
* Spawn area or Spawn points

# Behavior

The minimum and maximum counts must be independent for each maze.

# Please Notice
## Server Security

All enemy tracking, counting, and spawning must happen on the server.

Do not allow clients to modify enemy counts or trigger replacement spawning.

## Connecting The Scripts

You can add additional areas by creating a new configuration rather than duplicating the entire script.

# Script (EnemyAreaConfig)

--[[

This is the ONLY place you edit to add/change the maze/area. The manager script (EnemyManager) reads this table; you never have to copy this code to add a new area.

WHERE TO PUT IT

  ServerScriptService
  |_ EnemySystem           (Folder)
    |- EnemyAreaConfig     (This Script)
    |- EnemyManager        (ModuleScript)
    |- EnemyManagerRunner  (Script)
    |_ (Another: still thinking about how to implement the spawner)

SECURITY

Anything inside ServerScriptService cannot be seen or changed by clients, so players cannot edit these numbers.

]]

local Config = {}

-- GLOBAL Settings (apply to every area)

Config.CheckInterval = 5

--[[
How often, in seconds, the manager re-checks every area and spawns missing enemies.
This recovers from unexpected removals or failed spawn attempts (e.g., another script killed an enemy).
]]

Config.EnemyTag = "Enemy"

-- [[
CollectionService tag placed on every enemy the manager spawns or registers.
Other scripts (e.g. kill cub) use this tag to know "this model is an enemy/target".
]]

Config.AreaAttribute = "EnemyAreaName"

-- [[
Name of the attribute written onto each enemy that records which area it belongs to.
This is how an enemy from Maze1 is never counted towards Maze2's limit
]]

Config.CorpseCleanupDelay = 3

-- [[
How many seconds a dead enemy's body stays before being cleaned up.
]]

-- [[

AREA Settings

To add a new area: copy one block below, change the key name (e.g. "Maze3") and edit the values.

EnemyTemplateName : name of MODEL in ServerStorage to clone. The model needs a humanoid and HumanoidRootPart.

MinEnemies : If living enemies drop BELOW this, the manager spawns more until this number is reached.

MaxEnemies : HARD CAP. The manager never spawns above this.

SpawnLocationName : name of something in workspace. It can be a single part; the enemies can spawn at RANDOM positions inside the part's boundaries (e.g., spawn area). Or a folder/Model; enemies spawn at a RANDOM one of those spawn points

InitialSpawn : true = fill them with up to minEnemies when the server starts.

]]


Config.Areas = {

  Maze1 = {
    EnemyTemplateName = "Maze1Enemy",
    MinEnemies         = 2,
    MaxEnemies         = 5,
    SpawnLocationName  = "Maze1_SpawnPoints",
    InitialSpawn      = true,
  },
  
  Maze2 = {
    EnemyTemplateName = "Maze2Enemy",
    MinEnemies         = 1,
    MaxEnemies         = 3,
    SpawnLocationName  = "Maze2_SpawnArea",
    InitialSpawn      = true,
  },
}

return config

-- [[

You can change Maze1 to match your game's name.
Maze1Enemy should be a Model located solely in ServerStorage.
SpawnLocation Name is a folder or part in Workspace.
Maze2 will be completely independent of Maze1

]]
