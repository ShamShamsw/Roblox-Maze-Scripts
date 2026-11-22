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

You can change Maze1 to match your game's name.
Maze1Enemy should be a Model located solely in ServerStorage.
SpawnLocation Name is a folder or part in Workspace.
Maze2 will be completely independent of Maze1

]]
