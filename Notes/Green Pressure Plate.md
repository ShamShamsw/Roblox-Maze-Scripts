# Notice

This mechanism is different from a normal pressure plate. The block initially occupies the plate, and the objective is to push the block away.

# Required Functionality

1. The script should monitor a designated green pressure plate.

2. A specific movable block must initially be detected on the plate.

3. The script should detect when that block is physically pushed completely off the pressure plate.

4. Once the block leaves the designated plate area, activate the connected mechanism.

5. The mechanism could be a door, barrier, bridge, or another configurable object.

6. The activation should only happen once unless the mechanism is explicitly configured to reset or runs on a timer.

7. Moving the block partially off the plate should not activate the mechanism until the block is completely outside the plate’s detection area.

8. The script should ignore players, enemies, and unrelated objects.

## Required Changes you may have to make

* Green pressure plate reference.
* Required movable block.
* Connected mechanism.
* Detection area size.
* Activation behavior.
* Mechanism movement duration.
* Whether the mechanism stays activated permanently or resets.

# Please Notice
## Server Security

Server-side detection to determine whether the designated block is occupying the pressure plate. Relying exclusively on Touched events may cause unreliable detection when the block stops moving.

Use server-side spatial detection to monitor whether the block is still occupying the pressure plate.

The server must independently verify that the correct block has left the designated area. Do not allow clients to activate the mechanism through RemoteEvents.

## Connecting The Scripts

Configure the pressure plate, movable block, and door in Roblox Studio. The script should be easy to reuse for multiple doors by changing its configuration.
