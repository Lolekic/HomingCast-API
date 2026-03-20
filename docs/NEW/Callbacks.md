# Callbacks

Callbacks are functions defined within [settings](Settings.md) that allow you to define custom behavior of a projectile when certain events occur

Each callback is marked with

- `r` for direct read permission
- `w` for direct write permission

There are currently 8 callbacks present

## Callbacks

---
### OnStep [rw]

Fires every time the projectile steps **even if the velocity is `0`**

```lua
OnStep = function(projectile: Projectile, deltaTime: number): nil
```

---
### OnPositionChange [rw]

Fires every time the projectile steps **except when the velocity is `0`**

```lua
OnPositionChange = function(projectile: Projectile, newPosition: Vector3, oldPosition: Vector3): nil
```

---
### OnDestroy [rw]

Fires when the projectile is destroyed

```lua
OnDestroy = function(projectile: Projectile, reason: string | "MaxTime" | "MaxDistance" | "Hit"): nil
```

---
### OnHit [rw]

Fires when the projectile hits something

```lua
OnHit = function(projectile: Projectile, result: RaycastResult, hasPierced: boolean): nil
```

---
### OnTargetLost [rw]

Fires when the projectile exceeds `MaxTrackAngle`

```lua
OnTargetLost = function(projectile: Projectile, target: Vector3 | BasePart): nil
```

!!! warning "Note"
    After `OnTargetLost` is fired, the target is set to `nil`

---
### OnCheckpointReached [rw]

Fires when the checkpoint inside of [trajectory](CustomTrajectories.md) is reached

```lua
OnCheckpointReached = function(projectile: Projectile, checkpoint: string): nil
```

!!! warning "Note"
    After `OnCheckpointReached` is fired, the checkpoint is set to `nil`

---
### PostTransform [r]

Due to the way Motor6D.Transform works we made a PostTransform callback which is called right after .Transform is applied for the first time.
Otherwise the CFrame of the cosmetic part will appear as origin

```lua
PostTransform = function(projectile: Projectile): nil
```

---
### PostTransformSafe [r]

This is the 2nd PostTransform. Basically the second time .Transform is applied. This is helpful to safely toggle vfx on or make parts visible to hide the
pre .Transform phase

```lua
PostTransformSafe = function(projectile: Projectile): nil
```