# Required Functionality

1. The script should monitor a designated cube or kill-zone part in Workspace.

2. When an enemy NPC touches the cube, that enemy should immediately die.

3. The script should identify enemies using a designated enemy identifier, tag, or CollectionService tag.

4. Players must not be killed by this cube.

5. The script should prevent an enemy from triggering multiple death events while already being eliminated.

6. After an enemy dies, wait 5 seconds before checking whether a replacement is needed.

7. Check the enemy count in the maze where the enemy originally belonged.

8. If the maze’s living enemy count is below its configured minimum, spawn a replacement enemy.

9. If the minimum enemy count has already been reached, do not spawn another enemy.

10. Never exceed the maze’s configured maximum enemy count.

11. Replacement enemies must spawn at an appropriate spawn location belonging to their original maze.

## Required Changes you may have to make

• Kill cube object or modal.
• Enemy identification method.
• Respawn delay (default: 5 seconds).
• Maze identification.
• Enemy template.
• Whether the cube kills immediately or applies configurable damage.

## Note

Will need to integrate with the server management that handles the enemies. The preferred design is for this script to notify or work with the existing maze enemy manager.

The manager should remain responsible for enforcing minimum and maximum enemy limits.

Avoid creating two independent enemy-counting systems that could conflict.

If no enemy manager exists, explain what additional tracking functionality is needed.

Include protection against duplicate deaths, duplicate respawns, and exceeding the maximum enemy count.

## Server Security

The server must handle all collision detection, enemy elimination, and replacement decisions. (Do not use LocalScripts or client-triggered RemoteEvents.)

# Script
