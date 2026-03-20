# This feature was removed in update 1.7

To enable this feature, do the following:

```luau
local HomingCast = require(game.ReplicatedStorage.HomingCast)

HomingCast.AmountOfActors = 10
HomingCast.PositionSendDelay = 0.1

local caster = HomingCast.new()
```

!!! question "What is PositionSendDelay?"
    **PositionSendDelay** determines how often the **PositionChanged** signal is fired

    The smaller the PositionSendDelay is, the fewer projectiles you can handle

!!! danger "Note!"
    **AmountOfActors** and **PositionSendDelay** must be set before creating a new caster!

    Parallel mode can only be used on server side!

# Recommendation

I don't recommend using this feature, as it **won’t allow significantly more projectiles at once**, and the following features are not available in parallel mode:

1) All methods are unavailable

2) Visualization is unavailable

3) **Offset, Scaler, CosmeticBulletTemplate and SimulateBeforePhysics** properties are unavailable

Additionally, to use signals, you must add **.Event** due to the use of **BindableEvents**

!!! example "Example"
    ```luau
    caster.PositionChanged.Event:Connect()
    ```