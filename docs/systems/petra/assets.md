---
layout: default
section-id: petra
page-id: Assets
---

# Assets

### Links
*Source*: [![GitHub](https://img.shields.io/badge/GitHub-View_Assets-black?style=flat&logo=github)](https://github.com/OpenSourceKingdom/OSK.Petra.Assets)
  [![GitHub](https://img.shields.io/badge/GitHub-View_Godot_Assets-black?style=flat&logo=github)](https://github.com/OpenSourceKingdom/OSK.Petra.Godot.Assets)

*Packages*: [![NuGet](https://img.shields.io/badge/NuGet-View_Assets-blue?style=flat&logo=nuget)](https://www.nuget.org/packages/OSK.Petra.Assets)
  [![NuGet](https://img.shields.io/badge/NuGet-View_Godot_Assets-blue?style=flat&logo=nuget)](https://www.nuget.org/packages/OSK.Petra.Godot.Assets)

## Summary

Asset management is an integral part within any game application. Being able to quick access both meta data about an asset and the asset itself is an essential piece to game development.

Key concepts to the architecture include:
- `Module Asset`: Represents a larger piece or component of an application that will require dedicated background loading to add into or replace the current module. Module loading will be handled via an `IModuleLoader` that an integrating application will provide and details about the loading will be provided via a loading context. Various settings can be set to customize how the module is deployed into a given module (e.g. replacement, bootstrapping, finalizing load via user input, etc.). 
- `Entity`: An entity (e.g. game object or entity) represents a small piece or component of a module. The expectation is of a game model that will be more quickly than an entire module, though loading can be performed asynchronously or synchronously depending on the asset's reference details
- `Asset Descriptor`: a meta data object that can be used to describe various components of an asset, without needing to load the asset into the scene. These are especially useful when wanting to display lists of data to a user about your assets and provide UI information (e.g. custom weapon attachments, etc.)
- `Asset Instantiator`: an object capable of generating new copies of a game entity that can be quickly loaded into the modules

Petra's asset system utilizes a single point of entry, within the `IAssetService` that can be used to both load game modules (e.g. game levels, scenes, etc.) and to also instantiate game entities in a single location. Game engine or other application integrations will need to implement an `IAssetManager` in order to ensure the shared database context receives the application's known modules and entities.

The system also allows searching for registered game assets using various asset tags, which can be driven by a UI and user selection.

One major design point was to allow for generic descriptors, asset references, and more, so that the inmtegrating application can directly use its own game resources (e.g. descriptors, modules, etc.) rather than needing to map into specific types. This allows more flexibility to utilize the asset system without needing to lock into any concrete implementations.

Further, the library provides cache handling for instantiators that are used frequently to reduce the requirement to load an asset every time it is used. This can be used optionally by providing an asset's identifier when calling to instantiate the asset. After some specified idle interval, the system will clean up the resources that an instantiator possesses in order to limit how much memory is utilized when players are not actively using those instantiators (e.g. user purchases tanks and moves to aircraft, the tank resources can be freed rather than staying in memory for the duration of the game). 

Note: while caching and other helpful logic are only useable by passing in asset identifiers, they are not required to use the asset system. The asset system can be used to instantiate any standard object the integration engine/application supports, but you will lose information relating to the descriptor meta data, caching, and other potentially useful logic.

### Godot

The Godot implementation provides an `AssetManager` and numerous configuration data objects to add various asset packages, collections, modules, and entities using the editor.

A `GameAssetPackage` is an entire package of assets that can be used within the game application. An asset package can be pulled in via the standard asset configuration (e.g. base game assets) or via asset manager discovery of assets pulled in via DLC, In-App purchasing, or other means. Each package will define the collections it possesses as well as the assets that belong to those collections.