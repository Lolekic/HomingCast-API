## What is Custom Trajectory?

`Custom Trajectory` is a property in [Properties](Properties.md) called `Trajectory`, which makes the [Caster](Caster.md) follow a predefined path.

---
### How do I get this `Trajectory`?

I created a plugin to simplify this process for you. Here is the [plugin](https://create.roblox.com/store/asset/97281486618608/HomingCast-Plugin).

---
### How to use this Plugin?

Here are all the controls:

- **Double-click** to create a new point. (These points are draggable.)

!!! warning "Reminder!"
    Since these points use `UI Drag Detectors`, you need to enable the beta feature in Roblox Studio called `UI Drag Detectors`

- **Press `E` on a point** to change its state

!!! question "What is `State`?"
    Each point currently has two states:
    
    * **Free**
    * **Locked on Y-axis**
    
    If a point is locked on the Y-axis, its height won't be affected by the start position of the cast or the target's position. 
    The **Free** state is the standard state, allowing height to change during flight

- **Use the mouse wheel** to adjust the maximum height
- **Press `G` on a point** to create a checkpoint

!!! question "What is a `Checkpoint`?"
    A checkpoint contains a name. When the `Caster` reaches this point, it will fire the `CheckpointReached` signal.

---
### Saving and using the `Trajectory`

Once you've created the points, press the **Save** button. This will generate a `script` in `ReplicatedStorage` containing the trajectory table. Copy and paste this table into the `Trajectory` property

!!! example "Example"
    ```lua
    Properties.Trajectory = {
        {Yscale = 0.3, Xscale = 0.12220414727926254, State = "Free", MaxHeight = 150},
        {Yscale = 0.6, Xscale = 0.310281366109848, State = "Free", MaxHeight = 150},
        {Yscale = 0.6, Xscale = 0.903989744186401, State = "Free", CheckPoint = "Above", MaxHeight = 150},
    }
    ```

---

## Modes

There're 2 modes:

- **Trajectory** - To create a custom trajectory curve **(default)**
- **AoA** - To create yaw / pitch angle of attack tables

To change the mode, click ```Mode``` button