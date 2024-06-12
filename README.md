# ModularAssetSpawner README

## Overview

The ModularAssetSpawner script is a Unity component designed to spawn multiple instances of a modular asset prefab in various configurations and directions. It supports spawning in single or multiple dimensions and allows for custom offsets and pivot points for the spawned instances.

## Features

- Spawn instances in different directions (X, Y, Z, XY, XZ).

- Configure the number of instances to spawn.

- Customize the offset between each instance.

- Choose the pivot point for spawning (First, Middle, End).

- Visualize the spawn positions using gizmos in the Unity Editor.

## Installation

1. Attach the ModularAssetSpawner script to a GameObject in your Unity scene.

2. Assign the modular asset prefab to the assetPrefab field in the Inspector.

## Fields and Properties

- assetPrefab: The modular asset prefab to spawn.

- numberOfInstances: The number of instances to spawn (used for X, Y, Z directions).

- direction: The direction in which to spawn the instances (`X`, Y, Z, XY, XZ).

- offset: The offset for each spawned instance.

- pivot: The pivot point of the asset (`First`, Middle, End).

- dimensions: The number of instances in the X and Y directions (used for XY and XZ directions).

- spawnedObjects: A list to keep track of spawned objects.

## Usage

### Initialization

The script automatically initializes the size variables based on the BoxCollider attached to the assetPrefab. Ensure the prefab has a BoxCollider component.

### Spawning Assets

To spawn assets, call the SpawnAssets() method. This method clears any previously spawned objects and spawns new instances based on the specified parameters.

```csharp

ModularAssetSpawner spawner = GetComponent<ModularAssetSpawner>();

spawner.SpawnAssets();

```

### Updating Offsets

To update the offsets of the spawned objects, call the UpdateOffsets() method. This method repositions the spawned instances based on the new offset values.

```csharp

spawner.UpdateOffsets();

```

## Editor Integration

### OnValidate

The OnValidate() method ensures that changes made in the Inspector are immediately reflected in the scene. It removes null objects from the spawnedObjects list and updates offsets if the offset values have changed.

### Gizmos

The script uses Gizmos to visualize the spawn positions in the Unity Editor. This helps in understanding how the instances will be positioned based on the specified parameters.

## Example

To use the ModularAssetSpawner script, follow these steps:

1. Attach the script to a GameObject.

2. Assign the assetPrefab in the Inspector.

3. Set the desired number of instances, direction, offset, and pivot point.

4. Call the SpawnAssets() method to spawn the instances.

```csharp

public class ExampleUsage : MonoBehaviour

{

    private void Start()

    {

        ModularAssetSpawner spawner = GetComponent<ModularAssetSpawner>();

        spawner.SpawnAssets();

    }

}

```

## Notes

- Ensure the assetPrefab has a BoxCollider component to accurately calculate its dimensions.

- The Middle pivot point is not supported for XY and XZ directions.

- Use the Gizmos visualization to fine-tune the spawning configuration in the Unity Editor.

For any issues or questions, please refer to the Unity documentation or contact the script author.
