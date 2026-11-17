---
layout: default
section-id: petra
page-id: Experiences
---

# Experiences

### Links
*Source*: [![GitHub](https://img.shields.io/badge/GitHub-View_Petra_Experiences-black?style=flat&logo=github)](https://github.com/OpenSourceKingdom/OSK.Petra.Experiences) [![GitHub](https://img.shields.io/badge/GitHub-View_Godot_Experiences-black?style=flat&logo=github)](https://github.com/OpenSourceKingdom/OSK.Petra.Godot.Experiences)

*Packages*: [![NuGet](https://img.shields.io/badge/NuGet-View_Petra_Experiences-blue?style=flat&logo=nuget)](https://www.nuget.org/packages/OSK.Petra.Experiences) [![NuGet](https://img.shields.io/badge/NuGet-View_Godot_Experiences-blue?style=flat&logo=nuget)](https://www.nuget.org/packages/OSK.Petra.Godot.Experiences)

## Summary

A shared set of logic to handle monitoring, progressing, and managing experiences for users during game play. An experience can be a single challenge, a quest, a quest line, etc. Each experience is able to provide a custom enumerator that is able to progress the experience as the user plays through it. Each next step in the experience is then able to coniditionally check for previous outputs or decisions made in previous steps of the current experience or even check other external experiences for their output and decisions. In this way, experiences can be modified to return challenges and objectives to players as they decide how they want to engage with the game. 

Experience enumerators, Challenges, and their objectives are setup to be flexible and only require specific interfaces to be implemented - this allows developers to create their own custom data structures as needed or to use the built-in ones provided by the core libraries. 

There are currently two core types of built-in objectives within the system, though users can create their own custom objectives if these do not meet their needs. Objectives can either be event or time driven. e.g. an enemy is destroyed or an ore is collected, an event is triggered to be processed within the system. Timer based objectives will require updating the service ticker so that it can validate time delta objectives.

Events will be triggered as a player engages with the experiences. Each experience is given a context that is handled internally by the core logic service and is used to start, stop, or retrieve insights into the current state of the experience being undertaken. Applications can listen to the event hooks to quickly respond to a variety of user engagement with an experience or other changes that occur during the runtime of the experience.

### Godot 

The Godot integration provides several scripts and other files to configure and setup experiences via the Godot editor. Additionally, the godot implementations are setup to allow creation via constructors independent of the editor if it is easier to create those via code rather than through an editor directly