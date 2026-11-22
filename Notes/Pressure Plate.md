# Required Functionality

1. The script should monitor a designated pressure plate in Workspace.

2. When a specific movable block is placed on the pressure plate, the door should open.

3. The door should remain open for as long as the block remains on the pressure plate.

4. When the block is removed from the pressure plate, the door should close.

5. The script must distinguish between the designated block and other objects or characters.

6. Players standing on the pressure plate should not activate the door unless explicitly configured.

7. The door should move smoothly between its open and closed positions.

8. The script should prevent repeated door animations when the block is moved slightly while remaining on the plate.

## Required Changes you may have to make

* Pressure plate reference.
* Required block name or identifier.
* Door reference.
* Door open position.
* Door closed position.
* Door movement duration.
* Whether the door opens upward, sideways, or through a configured position.

# Please Notice
## Server Security

Server-side detection to determine whether the designated block is occupying the pressure plate. Relying exclusively on Touched events may cause unreliable detection when the block stops moving.
All block detection and door movement must be controlled by the server. Do not trust client-side activation messages.

## Connecting The Scripts

Configure the pressure plate, movable block, and door in Roblox Studio. The script should be easy to reuse for multiple doors by changing its configuration.
