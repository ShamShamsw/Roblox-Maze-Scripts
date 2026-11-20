# Required Functionality

1. The script should detect when a player character physically steps onto a designated pressure plate.

2. When activated, the pressure plate should spawn an enemy NPC from a designated enemy template stored in ServerStorage.

3. The enemy should spawn inside a configurable spawn area in Workspace.

4. The spawn area should allow enemies to spawn at randomized positions within its boundaries.

5. Only player characters should activate the pressure plate. NPCs and other objects should not activate it.

6. The script should include a configurable activation cooldown to prevent repeated spawning when a player remains on the plate.

7. Multiple players should not cause duplicate activations during the cooldown.

8. The script should verify that the enemy template and spawn area exist before attempting to spawn an enemy.

## Required Changes you may have to make

* Enemy template name.
* Spawn area name.
* Maximum number of enemies this particular plate or maze can spawn.
* Activation cooldown.
* Whether the plate can be activated once or multiple times.
* Whether the plate visually changes appearance when activated.

# Please Notice
## Server Security

All detection, validation, and enemy creation must happen on the server. Do not use RemoteEvents or LocalScripts for activation.

## Connecting The Scripts

Place the Script in Roblox Studio; instructions for the required objects and for configuring the enemy template and spawn area are included. Follow every step.

# Script


