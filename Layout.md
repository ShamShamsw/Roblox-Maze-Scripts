# How To Structure These Concepts

I wanted to include a section that would go over the layout and folder structure I would design if I was creating this game.

## Layout

ServiceScriptService
├── EnemySystem
│   ├── EnemyAreaConfig (ModuleScript)
│   ├── EnemyManager (ModuleScript)
│   ├── ManagerArea1 (ModuleScript)
│   └── EnemyManagerRunner (Script)
├── PushBlockDoors (Script)
├── SpawnPlate (Script)
├── SpikeCeilingTrap (Script)
└── SpikeWallTrap (Script)

ServerStorage
├── Maze1Enemy
│   ├── Humanoid
│   ├── HumanoidRootPart
│   ├── PrimaryPart
│   └── Enemy AI Script
└── Maze2Enemy
    └── ...

Workspace
├── Maze1SpawnPoints
│   └── Spawn parts or a folder containing multiple parts
├── PressurePlate (Script)
├── KillCube (Script)
├── GreenPlate (Script)
├── SpawnPlate
├── SpikeCeiling
└── SpikeWall

## How the pieces operate

The Manager scripts handle the counting system for all mazes. Add a maze by adding a block in EnemyAreaConfig.

SpawnPlate will be used to spawn more enemies into the maze, up to a specific maximum number. This will need to be set with a new script, for example, "ManagerArea2"

KillCube will kill an enemy, wait 5 seconds, and then ask the manager to check the enemy's maze. The manager will then enforce the min/max.

Everything else is an independent mechanism.

## Creating an enemy

1. Model with "Humanoid" and "HumanoidRootPart", and set the PrimaryPart. (You can use premade workshop options)
2. Parts unanchored.
3. Script for the Enemy AI placed inside the model.
4. Stored in "ServerStorage", with the name matching the config.

## Notes

* Certain parts of your game must be anchored to be properly utilized, like pressure plates, walls, traps, etc. Moving required models use "PivotTo", so all parts are anchored.
* Touched is unreliable, so make sure spike hazards use server-side bounding-box checks.
* Block detection works best with axis-aligned, non-spinning blocks.
* Always test scripts for errors, bugs, and unintended uses.
