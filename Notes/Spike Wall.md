# Required functionality

1. The script should reference a designated spike wall model in Workspace.
 
2. The wall should have a designated trigger area that detects when a player enters its proximity.

3. When a player activates the trigger, the spike wall should begin its attack sequence.

4. The wall should move across a designated path or corridor to create a dangerous obstacle.

5. The wall should move smoothly using server-controlled movement.

6. If a player touches the active spikes, the player should receive configurable damage or be eliminated immediately.

7. The wall should stop at its designated endpoint.

8. After reaching the endpoint, the wall should wait for a configurable amount of time.

9. The wall should return to its original position.

10. The trap should have a cooldown to prevent repeated activation while it is already operating.

11. The wall should not damage players while inactive or resetting unless explicitly configured.

## Required Changes you may have to make

* Spike wall model.
* Trigger area.
* If Movement (Starting position, Ending position, Movement speed, Activation cooldown.)
* Damage amount. (Instant death.)
* Warning sound and Activation sound.

# Please Notice
## Server Security

Use server-controlled movement so all players see the same wall movement.

Handle the script to ensure the wall does not become detached, misaligned, hidden, or stuck during movement.

Any activation detection, movement, and damage calculations must happen on the server.

Players must not be able to activate the trap remotely or manipulate its movement through client-side scripts.
