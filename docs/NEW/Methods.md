## Methods of HomingCast

These methods are accessed as `HomingCast.YOUR_METHOD`

---
### SpawnProjectile

Creates a projectile and activates it

```lua
HomingCast.SpawnProjectile(constructorArgs: ProjectileConstructorArgs, projectileSettings: ProjectileSettings?, physicsSettings: PhysicsSettings?): Projectile
```

---
### CreateProjectile

Creates a projectile

```lua
HomingCast.CreateProjectile(constructorArgs: ProjectileConstructorArgs, projectileSettings: ProjectileSettings?, physicsSettings: PhysicsSettings?): Projectile
```

---
### ActivateProjectile

Activates a projectile making it start simulating

```lua
HomingCast.ActivateProjectile(projectile: Projectile)
```

---
### DeactivateProjectile

Deactivates a projectile making it stop simulating

```lua
HomingCast.DeactivateProjectile(projectile: Projectile)
```

---
### StepProjectile

Steps a projectile

```lua
HomingCast.StepProjectile(projectile: Projectile, deltaTime: number)
```

---
### TerminateProjectile

Terminates a projectile firing OnProjectileDestroyed callback

```lua
HomingCast.TerminateProjectile(projectile: Projectile, reason: string?)
```

The `Reason` which will be returned in `OnDestroy` callback
The default value is `nil` if omitted

---
### IsRunning

Checks if HomingCast simulation is running

```lua
HomingCast.IsRunning(): boolean
```

---
### Start

Starts HomingCast simulation

```lua
HomingCast.Start()
```

---
### Stop

Stops HomingCast simulation

```lua
HomingCast.Stop()
```

---
### SetProjectilePart

Sets a projectile part for the projectile

```lua
HomingCast.SetProjectilePart(projectile: Projectile, basePart: BasePart?)
```