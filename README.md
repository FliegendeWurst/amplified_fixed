# Amplified world generation without excessive flooded caves

This datapack changes the noise parameters to remove flooded caves in amplified world generation.
It achieves this by increasing the terrain density (= more stone/dirt) around y=46,
which cuts off most surface water from the cave systems.
It shouldn't make it harder to find caves since some seemingly ignore the inital density generation.

```json
"initial_density_without_jaggedness": {
    "type": "minecraft:add",
    "argument1": {
        "type": "minecraft:mul",
        "argument1": 10.0,
        "argument2": {
            "type": "minecraft:min",
            "argument1": {
                "type": "minecraft:y_clamped_gradient",
                "from_value": 1.0,
                "from_y": 46,
                "to_value": 0.0,
                "to_y": 50
            },
            "argument2": {
                "type": "minecraft:y_clamped_gradient",
                "from_value": 0.0,
                "from_y": 42,
                "to_value": 1.0,
                "to_y": 46
            }
        }
    },
    "argument2": {
        ... vanilla noise expression ...
    }
}
```

## Removing all flooded caves

It is also possible to remove normal flooded caves by decreasing the `fluid_level_floodedness` noise.
