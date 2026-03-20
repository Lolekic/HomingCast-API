## At this page, you can see all methods that are currently implemented

!!! info "Remember!"
    These methods must be applied to [InfoCast](InfoCast.md)

## Non-Physics methods

---
### TerminateCast
```lua
InfoCast:TerminateCast(customReason: string?)
```
Terminates the cast.

---
### SetTimer
```lua
InfoCast:SetTimer(duration: number, func(A...) -> (R...), parameters: A...)
```
Sets a timer that runs the given function after the specified time.

---
### GetCosmeticBullet
```lua
InfoCast:GetCosmeticBullet(): any?
```
Retuns copied cosmetic bullet.

---
### SetSpeed
```lua
InfoCast:SetSpeed(Speed: number | Vector3)
```
Sets the speed of the cast.

---
### AddSpeed
```lua
InfoCast:AddSpeed(Speed: number | Vector3)
```
Adds the speed to the cast.

---
### GetSpeed
```lua
InfoCast:GetSpeed(): (number | Vector3)
```
Returns the current speed of the cast.

---
### GetPosition
```lua
InfoCast:GetPosition(): Vector3
```
Returns the current position of the cast.

---
### GetDirection
```lua
InfoCast:GetDirection(): Vector3
```
Returns the current direction of the cast.

---
### SetDirection
```lua
InfoCast:SetDirection(Direction: Vector3)
```
Sets the direction of the cast.

---
### SetPosition
```lua
InfoCast:SetPosition(Position: Vector3)
```
Sets the position of the cast.

---
!!! info "Remember!"
    Angles must not be in radians.

---
### SetRotationSpeed
```lua
InfoCast:SetRotationSpeed(Number: number)
```
Sets the speed of rotation of the cast.

---
### AddRotationSpeed
```lua
InfoCast:AddRotationSpeed(Number: number)
```
Adds the speed of rotation to the cast.

---
### SetMaxAngleToLoseTheTarget
```lua
InfoCast:SetMaxAngleToLoseTheTarget(Angle: number)
```
Sets the angle at which the cast loses its target.

---
### AddMaxAngleToLoseTheTarget
```lua
InfoCast:AddMaxAngleToLoseTheTarget(Angle: number)
```
Adds to the angle at which the cast loses its target.

---
### Pause
```lua
InfoCast:Pause()
```
Pauses the simulation of the cast.

---
### Resume
```lua
InfoCast:Resume()
```
Resumes the simulation of the cast.

---
### IsPaused
```lua
InfoCast:IsPaused(): boolean
```
Returns `true` if the cast is paused, otherwise `false`.

---
### PauseTrajectory
```lua
InfoCast:PauseTrajectory()
```
Pauses the trajectory from advancing.

---
### ResumeTrajectory
```lua
InfoCast:ResumeTrajectory()
```
Resumes the trajectory.

---
### IsPausedTrajectory
```lua
InfoCast:IsPausedTrajectory(): boolean
```
Returns `true` if the trajectory is paused, otherwise `false`.

---
### GetProgress
```lua
InfoCast:GetProgress(): (number, number, number?, number?)
```
Returns the current covered distance and total flight time. If the covered distance is greater than or equal to `0`, it also returns the percentage of how far the cast has traveled. The same applies to the total flight time.

---
### UpdateRaycastParams
```lua
InfoCast:UpdateRaycastParams(Params: RaycastParams)
```
Sets new raycast parameters for the cast.

---
### SetXscale
```lua
InfoCast:SetXscale(index: number, value: number)
```
Sets the X scale of a trajectory point to a given value (from `0` to `1`). The `index` determines the position in the trajectory list.

---
### SetYscale
```lua
InfoCast:SetYscale(index: number, value: number)
```
Sets the Y scale of a trajectory point to a given value (from `-1` to `1`). The `index` determines the position in the trajectory list.

---
### GetDistanceToTarget
```lua
InfoCast:GetDistanceToTarget(): number?
```
Returns the distance to the target if the target is not `nil`, otherwise returns `nil`.

---
### GetTargetInfo
```lua
InfoCast:GetTargetInfo(): (Vector3?, Vector3?)
```
Returns the position and velocity of the target. If the target is a `Vector3`, it only returns the position. If the target is `nil`, both return values will be `nil`.

---
### SetHighPrecision
```lua
InfoCast:SetHighPrecision(value: number)
```
Sets the high precision mode to the given value.

---
### SetTarget
```lua
InfoCast:SetTarget(Target: Vector3 | BasePart | Model | nil)
```
Sets the target to the given value.

!!! info "Remember!"
    The `Model` must have its primary part set; otherwise, an error will occur!

!!! warning "Beware!"
    Setting a new target too frequently can lead to unexpected behaviors!
---

---
### SetOffset
```lua
InfoCast:SetOffset(func: (number, number, Vector3, Vector3) -> (Vector3))
```
Sets the new `Offset` function.

---
### SetOffset
```lua
InfoCast:SetScaler(func: (number, number, Vector3, Vector3) -> (Vector3 | number))
```
Sets the new `Scaler` function.

## Physics methods

### IsPhysics
```lua
Simulation:IsPhysics(): boolean
```
Returns whether projectile has physics

### SetMass
```lua
Simulation:SetMass(Mass: number)
```
Sets the mass used for the physics simulation

---
### AddMass
```lua
Simulation:AddMass(Mass: number)
```
Adds to the mass used for the physics simulation

---
### SetLiftPower
```lua
Simulation:SetLiftPower(LiftPower: number)
```
Sets the lift power used for the physics simulation

---
### AddLiftPower
```lua
Simulation:AddLiftPower(LiftPower: number)
```
Adds to the lift power used for the physics simulation

---
### SetYawPower
```lua
Simulation:SetYawPower(YawPower: number)
```
Sets the yaw power used for the physics simulation

---
### AddYawPower
```lua
Simulation:AddYawPower(YawPower: number)
```
Adds to the yaw power used for the physics simulation

---
### SetDragCoefficient
```lua
Simulation:SetDragCoefficient(DragCoefficient: number)
```
Sets the drag coefficient used for the physics simulation

---
### AddDragCoefficient
```lua
Simulation:AddDragCoefficient(DragCoefficient: number)
```
Adds to the drag coefficient used for the physics simulation

---
### SetInducedDragYaw
```lua
Simulation:SetInducedDragYaw(InducedDragYaw: number)
```
Sets the yaw-induced drag value used for the physics simulation

---
### AddInducedDragYaw
```lua
Simulation:AddInducedDragYaw(InducedDragYaw: number)
```
Adds to the yaw-induced drag value used for the physics simulation

---
### SetInducedDragPitch
```lua
Simulation:SetInducedDragPitch(InducedDragPitch: number)
```
Sets the pitch-induced drag value used for the physics simulation

---
### AddInducedDragPitch
```lua
Simulation:AddInducedDragPitch(InducedDragPitch: number)
```
Adds to the pitch-induced drag value used for the physics simulation

---
### SetThrustPower
```lua
Simulation:SetThrustPower(ThrustPower: number)
```
Sets the thrust power used for the physics simulation

---
### AddThrustPower
```lua
Simulation:AddThrustPower(ThrustPower: number)
```
Adds to the thrust power used for the physics simulation

---
### SetGLimit
```lua
Simulation:SetGLimit(G_Limit: number)
```
Sets the G limit used for the physics simulation

---
### AddGLimit
```lua
Simulation:AddGLimit(MaxAngle: number)
```
Adds to the G limit used for the physics simulation

---
### SetPitchAoA
```lua
Simulation:SetPitchAoA(PitchAoA: {})
```
Sets the angle of attack curve for pitch in the physics simulation

---
### YawAoA
```lua
Simulation:YawAoA(YawAoA: {})
```
Sets the angle of attack curve for yaw in the physics simulation

---
### SetAdditionalForces
```lua
Simulation:SetAdditionalForces(Force: Vector3)
```
Sets the additional forces applied to the physics simulation

---
### AddAdditionalForces
```lua
Simulation:AddAdditionalForces(Force: Vector3)
```
Adds to the additional forces applied to the physics simulation