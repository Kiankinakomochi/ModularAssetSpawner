# Modular Asset Spawner 

## Overview

The ModularAssetSpawner script is a Unity component designed to spawn multiple instances of a modular asset prefab in various configurations and directions. It supports spawning in single or multiple dimensions and allows for custom offsets and pivot points for the spawned instances.

## Scripts

### ModularAssetSpawner

The `ModularAssetSpawner` script is attached to a GameObject in your scene and handles the spawning of modular assets based on specified parameters.

#### Parameters

- **assetPrefab** (`GameObject`): The modular asset prefab to spawn.
- **numberOfInstances** (`int`): The number of instances to spawn.
- **direction** (`SpawnDirection`): The direction in which to spawn the assets. Options include X, Y, Z, XY, XZ.
- **offset** (`Vector3`): The offset for each spawned instance.
- **pivot** (`PivotPoint`): The pivot point of the asset. Options include First, Middle, End. Note that Middle is not supported for XY and XZ directions.
- **dimensions** (`Vector2Int`): Number of instances in the X and Y directions, only used for XY and XZ directions.
- **spawnedObjects** (`List<GameObject>`): A list to keep track of spawned objects.

#### Methods

- **Start()**: Called when the script instance is being loaded. Initializes the size variables based on the asset prefab's BoxCollider.
- **InitializeSizes()**: Initializes the size variables based on the asset prefab's BoxCollider.
- **SpawnAssets()**: Spawns the modular assets based on the specified parameters. Ensures sizes are initialized before spawning and handles the clearing of previously spawned objects.
- **OnValidate()**: Called when the script is loaded or a value is changed in the inspector. Removes null objects from the list and updates offsets if changed.
- **CalculatePivotOffset(Vector3 directionVector)**: Calculates the pivot offset based on the spawn direction and pivot point.
- **GetDirectionVector()**: Returns the direction vector based on the spawn direction.
- **GetSecondaryDirectionVector()**: Returns the secondary direction vector for XY and XZ directions.
- **UpdateOffsets()**: Updates the offsets of the spawned objects.
- **OnDrawGizmos()**: Draws gizmos in the editor to visualize the spawn positions.

#### Usage

1. Attach the `ModularAssetSpawner` script to a GameObject in your scene.
2. Assign a prefab to the `assetPrefab` field.
3. Configure the spawn parameters as needed.
4. Click the "Spawn Assets" button in the custom editor (see below).

### ModularAssetSpawnerEditor

The `ModularAssetSpawnerEditor` script provides a custom inspector for the `ModularAssetSpawner` script. This custom inspector adds a button to the Unity Editor for spawning assets directly from the inspector.

#### Methods

- **OnInspectorGUI()**: Overrides the default inspector GUI to add a "Spawn Assets" button. When clicked, this button calls the `SpawnAssets` method on the target `ModularAssetSpawner` and registers the undo operation.

#### Usage

1. Place the `ModularAssetSpawnerEditor` script in an `Editor` folder in your project.
2. Select a GameObject with the `ModularAssetSpawner` component in the Unity Editor.
3. Use the custom inspector to adjust parameters and click the "Spawn Assets" button to spawn assets.

## Notes

- Ensure that the `assetPrefab` has a `BoxCollider` component to correctly initialize the size variables.
- The `Middle` pivot point is not supported for `XY` and `XZ` directions.
- The custom editor automatically handles undo operations, allowing you to revert changes if needed.

For any issues or questions, please refer to the Unity documentation or contact the script author.
