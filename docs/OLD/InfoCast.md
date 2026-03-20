## What is InfoCast?

InfoCast is a modified version of [Caster](Caster.md). It contains all properties, the current position, direction, reference to the `Caster`, etc.

---
### Where do I get InfoCast?

InfoCast is returned in all 5 signals. Read more about it [here](Caster.md).

Additionally, when you start a simulation using:

```lua
local InfoCast = Caster:Fire(...)
```

You will receive an `InfoCast`.

---
### Retrieving all active InfoCast

You can retrieve all currently simulated `InfoCast` using the function `HomingCast.GetAllInfoCast()`:

```lua
local HomingCast = require(.../HomingCast)

local PreActiveInfoCasts, PostActiveInfoCasts = HomingCast.GetAllInfoCast()
```

Returns 2 tables that contain all `PreActiveInfoCasts` and all `PostActiveInfoCasts` (PreSimulation and PostSimulation)