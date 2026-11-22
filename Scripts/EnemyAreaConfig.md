-- Script (EnemyAreaConfig) Copy the code into SERVERSCRIPTSERVICE using the name "EnemyAreaConfig". Folder structure and notes are below.

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
