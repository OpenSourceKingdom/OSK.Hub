---
layout: default
section-id: petra
page-id: Roadmap
---

# Roadmap

Petra has on-going development and will eventually encompass a large swath of game logic and services that will hopefully help many developers in creation of their games. Below is a list of projects that are in various stages of development, but is not necessarily completely exhaustive. This list is meant to serve only to what has been considered so far and committed to being provided at some point.

### Status Legend

- Beta: the project is currently in a phase where active development is on-going, but it is in a stable, usable state
- In Progress: The project is in development, and or in an alpha state, and not currently available for public use. Check back again later to see if it has been transitioned into a stable, usable state.
- Planned: The project is considered a viable part of the framework and will likely be designed/created in the future

### Projects

### 🎯 Beta

- **Dependency Injection** — Standard .NET DI integration for game applications
- **Logging** — Structured logging framework for game engines
- **Provisions** — Resource transaction/refund calculation handling and economy style management
- **Modules** — Isolated scenes/levels for a game engine that allows sharing logic and/or DI
- **Inputs** — Input processing and response handling for various action definitions configured by an application
- **Probabilities** — Handles RNG in game applications and simulates dice rolls or chance/luck style checks

### 🚧 In Progress/Alpha

- **Ability/Effect Management** — System for defining and triggering in-game abilities and their effects. Handles targeting various game entities.
- **Game Experiences** — Handles creating and managing game quests, story, etc. style narratives and progressing a game through an experience
- **Acquisitions** — Manages queue systems (build, training, research, etc.) and related tech trees in various configurations (repeated unlock, tech tree unlock, etc.) and providing mechanisms to manage the acquisitions as a user interacts with the application
- **Achievements** — Handles integrating with various achievement provides (Google, Apple, Steam, Xbox, etc.) and managing progress tracking of the achievements in an application
- **Audio** — Provides a mechanism to create and run various audio files in a game application and tracking 3D sounds with game entities. 
- **Settings** — A system that will handle storing, retrieving, and apply settings dynamically across types. Will provide UI capability for user interaction
- **Engagements** — Handles battle logic between multiple game entities (1v1, or multiple combantants) in various ways and determining damage incurred on or deflected from a target
- **Vision Maps** — Performs sight visibility calculations for game entities and teams of players, as well as rendering visibility for fog of war and minimap scenarios
- **Game Runtime** — Provides information about the game runtime as well as helpful game managers to facilitate managing various aspects of a game
- **Asset Management** — Handles instantiating individual game entities and levels, as well as initializing game services
- **Calculators** — Performs various math calculations and data tracking for economy games (e.g inflation logic)
- **Contributions** — Support library to handle defining and displaying credits/contributions of individuals/organizations

### 📐 Planned

- **In-App Purchasing** — unified game store logic for engine agnostic APIs
- **Game AI** — More a defining category, but aspects of smart opponent are being considered