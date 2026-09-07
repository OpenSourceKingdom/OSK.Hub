---
layout: default
section-id: petra
page-id: Framework
---

# Framework

### Links
*Source*: [![GitHub](https://img.shields.io/badge/GitHub-View_Framework-black?style=flat&logo=github)](https://github.com/OpenSourceKingdom/OSK.Petra.Godot.Framework)

*Packages*: [![NuGet](https://img.shields.io/badge/NuGet-View_Framework-blue?style=flat&logo=nuget)](https://www.nuget.org/packages/OSK.Petra.Godot.Framework.Build)

## Summary

The overall framework of Petra is split into numerous, isolated packages and shared logic, but in game engine implementations, it may be necessary to provide a mechanism to do a bit more and include a set of logic to build, inject source files, etc. The aim of the framework libraries is to encompass any required build processes that are needed to get a game engine integration working.

The standard package hierarchy is an engine agnostic logic library with potential game engine specific libraries. In the cases where engine specific libraries are used, they will mostly serve as configuration style libraries, but they coudl potentially offer logic enhancements where it makes sense to do so. Naming convention follows `OSK.Petra.{LibraryName}` as a core logic library with game engine integrations utilizing `OSK.Petra.{EngineName}.{LibraryName}` as the moniker.

As of now, the framework build libraries are integration specific, and there is not an agnostic version.

### Godot

Godot has a unique issue in that several of the main engine classes (Node/Resource/etc.) can not be easily shared across a nuget package, because for Godot to pick up the file(s) and show them as usable in a scene it must be available in the godot `res://` file system. This does cause a small issue because any shared logic that is a Node or Resource will inherently be non-shareable via a standard nuget package. 

There is a way around this problem, although it does require an extra framework build package which has an expected format for C# libraries to work. We'll utilize a `.targets` file and a shared build script to copy the package files into the local project's `res://` direectory, in a well-known, expected directory name: `PetraFramework`.

Petra's godot projects will typically set `Resource` style, configuration data structures in a `Data` directory, while placing `Node` style, game runtime, assets into a `Scripts` directory.

#### Integrating Build Targets

Petra expects a build target file that will inject code into Godot projects for use with the Godot inspector and other engine functions. This utilizes a shared directory path for all petra related godot projects to help maintain a clean project space for godot applications.

A .targets file should be added to any Petra godot project expecting to be injected via the build process:

<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

	<ItemGroup Condition="Exists('$(ProjectDir)project.godot')">
		<PetraPackages Include="$(MSBuildThisFileName)" />
		<PetraGodotFiles Include="$(MSBuildThisFileDirectory)..\godot\**\*.*">
			<DestFolder>$(ProjectDir)PetraFramework\$(MSBuildThisFileName)\</DestFolder>
		</PetraGodotFiles>
	</ItemGroup>

</Project>

The build target will utilize any package added to a Godot application to inject the needed code for Godot functionality.

Due to Godot's requirement of needing the node, resource, and other godot specific types to physically exist within the `res://` filesystem in order for Godot to register them within its inspector, 
Petra Godot's framework implementation utilizes a common, dedicated `PetraFramework` directory:
```
your-project/
└── PetraFramework/
    └── OSK.Petra.Godot.Provisions/
        ├── Data/
        └── Scripts/
    └── ... // Other petra projects
```

To ensure the Petra framework and suite works with your project, please note the following:
- *Do Not Modify Injected Files*: The files inside the PetraFramework directory are completely transient. Any manual edits, refactors, or changes you make will be overwritten during the next project build.
- *The petra system is setup to pull in transitive dependencies automatically*: installing Package B and building should pull in Package A and its related Godot specific assets. If you encounter issues with this, please file a bug on the repository.
- **GitIgnore Recommended:** The Petra Godot implementation automatically injects a dedicated directory alongside your codebase during builds. To keep your source control true to your codebase, add the folder to your `.gitignore` file, as an example:
  ```text
  **/PetraFramework/
  ```

Note: Petra Godot packages will be dependent on the shared build script, so you do not need to pull in any specific dependencies outside of a single Godot package from the framework for it to work, however if there is a build script update, you will need to pull in the framework's build dependency to ensure you are building with the latest framework build scripts.