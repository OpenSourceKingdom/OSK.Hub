---
layout: default
section-id: petra
page-id: Inputs
---

# Inputs

### Links
*Source*: [![GitHub](https://img.shields.io/badge/GitHub-View_Petra_Inputs-black?style=flat&logo=github)](https://github.com/OpenSourceKingdom/OSK.Petra.Inputs) [![GitHub](https://img.shields.io/badge/GitHub-View_Godot_Inputs-black?style=flat&logo=github)](https://github.com/OpenSourceKingdom/OSK.Petra.Godot.Inputs)

*Packages*: [![NuGet](https://img.shields.io/badge/NuGet-View_Petra_Inputs-blue?style=flat&logo=nuget)](https://www.nuget.org/packages/OSK.Petra.Inputs) [![NuGet](https://img.shields.io/badge/NuGet-View_Godot_Inputs-blue?style=flat&logo=nuget)](https://www.nuget.org/packages/OSK.Petra.Godot.Inputs)

## Summary

An input system is responsible for a wide variety of requirements, ranging from input signaling and receiving to interpreting input state and responding to it, there is a vast amount of logic that can be required to fully configure and implement a good input system. Petra's input framework aims to reduce the complexity of most of the challenging parts and to provide an API and SDK that requires only configuration to get setup and running. 

The input libraries attempt to be flexible while providing as much rich information as possible when interacting and responding to user input, across a wide range of devices. To ensure the libraries are reusable across a wide variety of applications, Petra's input system is split into 4 layers: Abstractions, Core, Configuration Extensions and Device extensions. Additionally, an integration layer is required for it to fully operate within a particular game engine to trigger the required input event to process; i.e. a core tenant of the shared logic is that the application integration layer will handle the actual input reading and that the core logic will merely interpret, track state, and respond to events as needed. The following sections will dive into each layer and their responsibilities.

### Abstractions

The abstractions layer is meant to provide all the needed interfaces  and data models to run an input system implementation. Petra provides an implementation of such an input system, but users can develop their own. Some of the key data structures are:

- `InputSystemConfiguration`: This is meant to be the 'source of truth' for all data that configures and runs the input system. A configuration contains information relating to join and device handling policies, action definitions, input configurations, and custom capability options. 
- `IInputCapability`: A capability is a mechanism to read, interpret, and process inputs received from devices or virtually defined inputs. These are meant to be isolated services that are injected via DI and process any specific `IInputEvent` that they would expect. During processing, the capabilities are provided the input state of the currently processing input and context of the user that initiated it to track and monitor capability-specific details to an input.
- `IInput`: Inputs are anything that a user can interact with to provide information to the input system. These include streams of data like pointers, accelerometers, and similar sensor devices, but can also be physical hardware (e.g. buttons, joysticks, etc.) as well as virtual inputs (e.g. combinations, gestures, etc.). The only requirement is that the inputs are able to provide their own `InputGlyph`, which is a visual representation of the input for a user to see, either while viewing or editing an input scheme or potentially used when a user is being asked for a specific action (e.g. trigger 'A' to interact). 
- `IDeviceProvider`: The device provider is an engine integration that provides data on the specific devices that an application is able to read from. Devices are expected to provide:
 - A DeviceIdentity, which is includes topology of the device (e.g. gamepad, keyboard, etc.), the family (i.e. brand) of device, and the actual name
 - A list of inputs the device actually contains. These are not meant to be virtual inputs as those are defined on a scheme level during configuration setup either by the user or during building of the DI container.
A core concept is that there is a difference between a generic device, which may interpret all inputs of a topology, and an actual device, which may only contain a set of inputs that may or may not be included on the generic device for the topology. So device providers are expected to provide all devices that an input system is expected to see to ensure that appropriate glyphs, identities, etc. are used during scheme editing, glyph rendering, etc. on a UI level. For core logic, a generic device should be all that is necessary.
- `IInputEventContext`: The input event context is the primary tool utilized by an action that is triggered. Actions are registered on `ActionDefinition` objects that are used to trigger an execution of some function within your application. Action defintiions provide a way to describe more than a single style of input that can be received (e.g. infantry, ship, aircraft, etc.). `InputAction` objects can be configured to trigger on specific input phases, and provide extra information for a user (e.g. descriptions, etc.). A context is generated when an input that is received is valid for the action state and then executed. You can register an entire class of actions with the input system at a time and they will be used with the DI container to execute an action.
- `ISchemeRepository`: A scheme repository is utilized to store and retrieve custom input schemes users may generate or to store their preferred input schemes for input configurations. The default implementation that Petra provides is a memory repository that does not support custom schemes.

Input configurations are a collection of supported device configurations. Think of an input configuration as a complete set of controllers that can be used to create input schemes. For example, you can create an input scheme for a keyboard or keyboard & mouse, which would result in 2 different input configurations, one for the single keyboard and one for the keyboard and mouse. The current input system configuration is setup to create the list of known and supported input configurations utilizing the pre-defined input schemes. It is essential that if you want to support more than a single input configuration that you at least define an input scheme with the expected input configurations desired. The reason behind this requirement is to ensure that if a user has not yet defined their own custom scheme for the input configuration that they are able to still interact with the application using a default scheme provided by your application.

As input system configurations can become quite complex, the `InputSystemConfigurationValidator` is a tool that is used to validate that these configurations are valid and sufficient to be the source of truth for the system executing from it. Petra's services will utilize this tool during initialization, but external input systems can and use this tool to validate the configuration they are utilizing is valid.

### Core

The core logic provides an input system that is capable of processing various capabilities, responding to and transmitting application notifications and handling the APIs required to run a complete system - from user and device management to input scheme editing, the Petra input system aims to provide a complete, cohesive set of logic to respond and interact with user input. Some of the key data structures are:

- `IInputSystem`: The input system is the main point of entry into integrating and consuming the APIs, though users can use any of the APIs through DI as the services of the petra system are injected into the DI container separately, the input input system can serve as the single focal point for all needs and interactions
- `IInputSystemNotifier`: The primary component of communication with the input system. The main notification that integrations will need to send is the `DeviceInputNotification` which will transmit the input that was triggered and the related input events that the user intiated with the input. The system will also transmit a wide variety of events (see the [notifications](https://github.com/OpenSourceKingdom/OSK.Petra.Inputs/tree/main/src/OSK.Petra.Inputs/Notifications))
- `ISchemeService`/`ISchemeEditor`: The input system is shipped with the ability to handle user schemes and configuring both custom scheme and preferred schemes for user input configurations. The scheme service is used to create an editor for a specific user and provides the APIs necessary to manage setting and updating scheme data.
- `IUserManager`: This manager handles tracking input users in the system and managing the devices that are associated with them
- `IDeviceCatalogProvider`: The device catalog encompasses all the devices and topologies that the input system supports. When building an input system, the application provides a collection of device providers, which can contain information on any number of devices, topologies, and input support. The device catalog is utilized to consolidate this data into a single place that can be used to quickly get information relating to any device, topology, etc. This is especially helpful for scheme editing or similar support.

Petra's input system comes with some input capabilities built-in and will be updated as the need arises to include others:
- `PowerInputCapability`: Processes power information for inputs that provide ON/OFF or continuous style applied power information
- `PointerInputCapability`: Processes pointer style input motion and related data

Each capability will add various InputDetails and/or InputFeatures that can be used during action execution by an application responding to an input as it may need.

The core logic can be added to any DI container using `AddInputSystem` extension.

### Configuration Extensions

The configuration extension projects provides a more DI friendly and manageable way to create an input system configuration. This can be accessed through the `InputSystemConfigurationFactory`. Using a fluent style approach, various aspects of configuration can be easily created and applied. There are three builders that are available to setup the configuration:

- `IInputSystemConfigurationBuilder`: The main point of entry for the configuration builders, which allows configuring the main components of an input system configuration, either directly or through another builder
- `IActionDefinitionBuilder`: Configures action defintiions and their input actions. There is an extension method for `IInputSystemConfigurationBuilder` that allows registering actions from a class. See [this extension file](https://github.com/OpenSourceKingdom/OSK.Petra.Inputs/blob/main/src/OSK.Extensions.Petra.Inputs.Configuration/InputSystemConfigurationBuilderExtensions.cs) on how to do this and using the related `InputActionAttribute` in conjunction to customize actions from a class file.
- `IInputSchemeBuilder`: Configures input schemes and the related devices

### Device Extensions

The device extensions serves primarily to define concrete and/or base implementations for Devices and their related inputs. Other libraries may define their own sets of these, but Petra comes with Gamepad, Keyboard, and Mouse support provided through base classes that an engine integration may use. The key files here include:

- Device descriptors for Keyboard, Mouse, and Gamepads. Further support for inputs will be added as the need requires.
- Defined base classes for `Digital` (0 or 1), `Analog` (0 to 1, continuous input), and `Pointer`.

## Engine Support

### Godot

Petra provides an integration with the Godot game engine. This is handled utilizing an input manager and configuring an input manager configuration in the Godot editor. Most of the core input manager logic is set within a base class that can be extended by different applications if the implementation provided is insufficient for some reason.

To fully utilize this library in a godot scene:
- Use a DI container and add required services using `AddGodotInputSystem` (see [Petra's Service Module](https://github.com/OpenSourceKingdom/OSK.Petra.Godot.Modules) to utilize a .NET native DI container for Godot)
- Add an input manager to the scene (see `InputEventManager` for one such implementation)
- Configure the input system for your scene's needs (local players, join behavior, action definitions, etc.)
- Enjoy a .NET DI based input system within Godot!