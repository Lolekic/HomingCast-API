Settings are now passed as a first parameter of `HomingCast.SpawnProjectile`/`HomingCast.CreateProjectile` methods as a table structure

!!! example "Example"
    ```lua
    local HomingCast = require(.../HomingCast)

    HomingCast.SpawnProjectile({YOUR SETTINGS})
    ```

!!! question "How do I reuse common `settings`?"
    In order to reuse common properties and don't pass the table everytime you can use `HomingCast.ProjetileSettings.new({YOUR COMMON SETTINGS})`

    And pass it as the second parameter of `HomingCast.SpawnProjectile`/`HomingCast.CreateProjectile` methods

---

Settings can be accessed inside of `projectile` and `changed`/`read` during the runtime

Each setting is marked with

- `r` for direct read permission
- `w` for direct write permission
- `b` for built-in function to edit

---

There are a lot of settings and they all are listed here!

## Settings

---
### MaxFlyDistance [rw] (number) 

If the projectile covers this distance, it will be terminated

!!! info "Terminated"
    This will fire `OnDestroy` callback:
    ```lua
    OnDestroy = function(projectile: Projectile, reason: string)
    ```
    The `Reason` will be `"MaxDistance"`

Default value is `math.huge` if omitted

---
### MaxFlyTime [rw] (number)

If the projectile flies longer than this value, it will be terminated

!!! info "Terminated"
    This will fire `OnDestroy` callback:
    ```lua
    OnDestroy = function(projectile: Projectile, reason: string)
    ```
    The `Reason` will be `"MaxTime"`

Default value is `math.huge` if omitted

---
### MaxPiercesPerStep [rw] (number)

Defines how many times projectile can pierce the objects before continuing its movement

Default value is `1` if omitted

---
### MaxTrackAngle [rb] (number)

If the target moves outside this angle, the projectile will lose track of it and set the target to **nil**

Value must be given in **degrees**

Default value is `180` if omitted

If the value is `180` it means that projectile will never lose its target

!!! info "Target lost"
    This will fire `OnTargetLost` callback:
    ```lua
    OnTargetLost = function(projectile: Projectile, target: Vector3 | BasePart)
    ```

!!! warning "Note"
    In order to properly set the value of this property you can use: `HomingCast.SetMaxTrackAngle(projectile: Projectile, angle: number)`
    
    Can be set manually by following this formula `math.clamp(math.cos(math.rad(angle)), -1, 1)` where `angle` is your desired value in **degrees**

---
### Prediction [rw] (boolean)

Defines if the projectile tries to predict the future position of the given target based on its velocity and position using [proportional navigation](https://en.wikipedia.org/wiki/Proportional_navigation) (PN)

Default value is `false` if omitted

---
### Target [rb] (Model | BasePart | Vector3 | nil)

The target to which the projectile will try to rotate towards

Default value is `nil` if omitted

If the value is `nil` the projectile will continue its movement towards the direction of the projectile's velocity

!!! warning "Note"
    In order to properly set the value of this property you can use: `HomingCast.SetTarget(projectile: Projectile, target: Model | BasePart | Vector3 | nil)`

!!! info "Remember"
    The projectile's target can be set to `nil` automatically if the projectile exceeded `MaxTrackAngle`

---
### Offset [rw] (Vector3)

The offset which is applied to target's position

Can be a funtion in order to give unique behaviour for the projectile

```lua
Offset = function(projectile: Projectile, deltaTime: number, targetPosition: Vector3, targetVelocity: Vector3): Vector3
```

Default value is `Vector3.zero` if omitted

---
### RotationSpeed [rb] (number)
Defines the speed at which the projectile turns

Default value is `30` if omitted

!!! warning "Note"
    In order to properly set the value of this property you can use: `HomingCast.SetRotationSpeed(projectile: Projectile, angle: number)`
    
    Can be set manually by following this formula `math.rad(angle)` where `angle` is your desired value in **degrees**

---
### RaycastParams [rw] (RaycastParams)

Defines the `RaycastParams` for the cast

Default value is `nil` if omitted

---
### Trajectory [rw] ({TrajectoryNode})
The projectile will attempt to follow the given trajectory

For more information, see [Custom Trajectories](CustomTrajectories.md)

Default value is `nil` if omitted

---
### RaycastFunction [rw] (RaycastFunction)

Defines which type of cast will be used to detect the hit of the projectile

For more information, see [Raycast Functions](RaycastFunctions.md)

Default value is `Default (Raycast)` if omitted

---
### ProjectilePart [rb] (BasePart)

The projectile's cosmetic part

Default value is `nil` if omitted

!!! warning "Note"
    In order to properly set the value of this property you can use: `HomingCast.SetProjectilePart(projectile: Projectile, basePart: BasePart?)`

---
### ProjectilePartRotation [rw] (CFrame)

The projectile's part's rotation

Default value is `CFrame.identity` if omitted and no projectile part

---
### CanPierce [rw] (boolean)

The value which defines if the projectile can pierce the object and continue its movement

Can be a funtion in order to give unique behaviour for the projectile

```lua
CanPierce = function(projectile: Projectile, result: RaycastResult): boolean
```

Default value is `false` if omitted

!!! warning "Note"
    If CanPierce returns `true`, it will fire `OnHit` callback
    
    ```lua
    OnHit = function(projectile: Projectile, result: RaycastResult, hasPierced: boolean)
    ```

    The `hasPierced` **in this specific case** will be `false`

---
### Userdata [rw] (any)

User's custom data

Default value is `nil` if omitted

---
### BlockcastSize [rw] (number)

The value which is used for specific type of cast

Default value is `nil` if omitted

**Can cause an warning if nil and the raycast function is used**

---
### SpherecastRadius [rw] (number)

The value which is used for specific type of cast

Default value is `nil` if omitted

**Can cause an warning if nil and the raycast function is used**

---
### ShapecastPart [rw] (BasePart)

The value which is used for specific type of cast

Default value is `nil` if omitted

**Can cause an warning if nil and the raycast function is used**