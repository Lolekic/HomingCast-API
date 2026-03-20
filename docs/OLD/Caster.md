## What is Caster?

This page describes what the `Caster`

---
### How to get Caster

To get `Caster`, you first need to require the module:

```luau
local HomingCast = require(.../HomingCast)
```

Then, create the `Caster`:

```luau
local Caster = HomingCast.new()
```

!!! warning "Remember!"
    The `Caster` must be created only once, as it serves as the base for all casts

---
### What is Caster?

`Caster` is used to start the simulation of a cast

```luau
Caster:Fire(StartPosition: Vector3, StartDirection: Vector3, Speed: number | Vector3, Target: Model | BasePart | Vector3, Properties, PhysicsProperties?)
```

!!! question "How to get Properties?"
    To get `Properties`, use:

    ```lua
    local Properties: {} = HomingCast.NewProperties()
    ```

    Read more about [Properties](Properties.md).

The `Caster:Fire` function returns an [InfoCast](InfoCast.md)

!!! danger "Beware"
    If you use [physics simulation](Physics.md), ```speed``` parameter will become not a constant speed, but an impulse

    If ```Speed``` parameter is number then impluse will be applied in ```StartDirection```

---
## Caster contains 5 signals

### PositionChanged

```luau
PositionChanged(InfoCast, Position: Vector3, Direction: Vector3, Distance: number, Target: Vector3 | BasePart, CosmeticBullet: any?, UserData: {})
```

This signal fires every time the `Caster` moves

!!! tip "Useful Tip!"
    If you want your projectile to follow the path and align with the flight direction, use this code:
    
    ```luau
    Caster.PositionChanged:Connect(function(...) 
        if CosmeticBullet then
            local BulletSize = CosmeticBullet.Size.Z / 2
            local Offset = CFrame.new(0, 0, -(Distance - BulletSize))
            CosmeticBullet.CFrame = CFrame.lookAt(Position, Position + Direction):ToWorldSpace(Offset)
        end
    end)
    ```

---
### RayHit

```luau
RayHit(InfoCast, RayCastResult: RaycastResult, Direction: Vector3, CosmeticBullet: any?, UserData: {})
```

This signal fires when the `Caster` hits something

---
### Terminated

```luau
Terminated(InfoCast, Reason: string, CosmeticBullet: BasePart?, UserData: {})
```

This signal fires when the `Caster` terminates due to exceeding the maximum flight distance, exceeding maximum flight time, or being manually terminated

!!! question "What is `Reason`?"
    The `Reason` parameter indicates why the cast was terminated. Possible values:
    
    * `Custom Reason` - The reason that was defined in ```TerminateCast``` method
    * `Self` - The cast was terminated manually
    * `MaxDistance` - The cast exceeded the maximum flight distance
    * `MaxFlyTime` - The cast exceeded the maximum flight time

---
### TargetLost

```luau
TargetLost(InfoCast, LostTarget: Vector3 | BasePart, Position: Vector3, Direction: Vector3, CosmeticBullet: any?, UserData: {})
```

This signal fires when the `Caster` loses its target

---
### CheckpointReached

```luau
CheckpointReached(InfoCast, CheckpointName: string, Position: Vector3, Direction: Vector3, CosmeticBulletTemplate: any?, UserData: {})
```

This signal fires when the `Caster` reaches a point in the trajectory

!!! info "Custom Trajectory"
    More information about [Custom Trajectories](CustomTrajectories.md).
