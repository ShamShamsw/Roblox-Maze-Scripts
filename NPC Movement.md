# Required Functionality

1. Player detection

2. Chasing behavior

3. Losing the target

4. Pathfinding failure handling

## Player detection

1. The enemy should continuously check for nearby player characters within a configurable detection radius.

2. The enemy should identify valid player characters using their Humanoid and HumanoidRootPart.

3. The enemy should ignore dead players and invalid characters.

4. When a valid player enters the detection radius, the enemy should select that player as its target.

5. The enemy should not automatically detect players anywhere on the map.

## Chasing behavior

1. Once a player is detected, the enemy should begin pursuing them.

2. Use Roblox PathfindingService to calculate a path toward the target.

3. The enemy should follow calculated waypoints using Humanoid:MoveTo().

4. The enemy should be able to navigate around basic obstacles such as walls, corners, and maze corridors.

5. If the player moves, the enemy should periodically recalculate its path.

6. Avoid recalculating the path every frame, as this could cause unnecessary server performance issues.

7. Allow the enemy to jump when necessary if the pathfinding waypoint requires it. (optional: Recommended if players get too comfortable standing on or too close to a cube.)

## Losing the target

1. If the player moves outside the configured detection radius, start a configurable escape timer.

2. If the player returns within detection range before the timer expires, reset the escape timer and continue chasing.

3. If the player remains outside the detection radius for the entire configured duration, stop chasing.

4. When the chase ends, clear the current target and return the enemy to its idle behavior.

## Pathfinding failure handling

1. If the enemy cannot calculate a valid path, wait briefly and attempt to recalculate.

2. If the enemy becomes stuck, detect the problem and attempt to generate a new path (Optional: Recommended if consistent playtesting results in NPCs getting easily stuck; consider a redesign of the maze section or allow a teleport to different spawn areas if no player is found within a specific time.)

3. If the target dies or leaves the game, immediately stop pursuing that target.

4. Prevent multiple simultaneous pathfinding calculations for the same enemy.

## Required Changes you may have to make

* Detection radius.
* Maximum chase distance.
* Time allowed outside detection range before abandoning pursuit.
* Enemy walking speed.
* Enemy chasing speed.
* Path recalculation interval.
* Waypoint arrival tolerance.
* Agent radius.
* Agent height.
* Agent jump capability.
* Agent maximum slope.
* Whether the enemy returns to its spawn position.
* Idle behavior.

# Please Notice
## Server Security

Do not run expensive pathfinding calculations continuously.

Use efficient proximity checks and reasonable update intervals.

Playtest to see if the system can support multiple enemies operating simultaneously without creating unnecessary server load.

Each enemy should maintain its own target, chase timer, and pathfinding state. (As well as handle multiple players)

All target detection, movement decisions, pathfinding, and enemy behavior must run on the server.

Ensure the server retains network ownership of enemy NPC movement where appropriate. (Do not use LocalScripts or RemoteEvents to control enemy AI.)

# Script
