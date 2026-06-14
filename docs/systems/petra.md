---
layout: default
title: Petra
---

# Petra

## Overview

Petra, the 'rock', hearkening to Peter whom God built the church, is meant to serve as a foundation for game development. It provides support for C# style engines for a vast amount of logic in a modular, flexible manner.

Originally designed in Unity but later refactored into an engine agnostic logic layer. The following engines are currently supported with a known implementation:
 - Godot (partial, on-going)

Core features include:
 - Ability/Effect management
 - Game experiences (i.e. objectives, quests, stories over many quests)
 - Asset management (i.e. level loading, instantiation, descriptors)
 - Dependency injection via standard .NET
 - Audio source management
 - Acquisitions (i.e. tech upgrades, tech trees, build queues, etc.)
 - Message event handling
 - Engagements (1v1 damage/armor type handling or RPG style group auto resolve)
 - Provision handling (i.e. calculating resource usage, refunds)
 - Achievements (local, steam, others)
 - Setting management
 - Probabilities
 - In App purchasing [planned]
 - Vision Maps (fog of war) [alpha]
 - Input handling
 - and more!

The goal is to provide a starting point for any game project to simply pull in the required dependency and allow developers to get up and running for their game project needs faster and more efficiently.