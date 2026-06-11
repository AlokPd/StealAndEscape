# Steal and Escape

A 3D top-down stealth adventure game built with Unreal Engine 4.27.2 using C++.
The project expands Epic Games' Top-Down C++ template by introducing custom gameplay mechanics,
enemy AI behaviors, user interface systems, and game data saving functionality.

**Course:** CSCI 491 Seminar
**Authors:** Kushal Poudel & Alok Poudel

---

## Game Description

In this game, players assume the role of a thief navigating through a guarded facility.
The goal is to locate and collect all designated valuables before reaching the extraction
zone while avoiding detection from security guards. Enemy guards utilize Unreal Engine's
AI Perception system to monitor both visual and audio stimuli and operate through three
behavioral states: Patrol, Pursuit, and Investigation. Player performance is evaluated
based on collected items and completion time, with results stored in a persistent leaderboard.

### Features

* Character movement using WASD controls with sprint support
* Footstep sound generation that can alert nearby guards
* Built-in click-to-move navigation inherited from the Unreal template
* Item interaction and pickup system activated with the G key
* AI guards equipped with vision and hearing perception systems
* Patrol routes managed through waypoint-based navigation
* Main menu, player name input, pause menu, HUD, and end-game screens
* Interactive tutorial level with guided progression triggers
* Persistent leaderboard implementation using `LeaderboardSaveGame`
* Adjustable master audio settings and UI sound feedback

### Controls

| Input        | Action                |
| ------------ | --------------------- |
| WASD         | Move Character        |
| Shift (Hold) | Sprint                |
| G            | Pick Up Nearby Item   |
| Mouse Click  | Click-to-Move         |
| Esc          | Open/Close Pause Menu |

---

## Software Requirements

* Unreal Engine **4.27.2**
* Visual Studio **2019**

  * Desktop Development with C++
  * Windows 10 SDK
  * .NET Framework 4.6.2 Developer Pack

---

## Project Setup

1. Clone the repository or download the project archive.
2. Install Unreal Engine 4.27.2 and all required development tools.
3. Open the project directory.
4. Right-click on `StealAndEscape.uproject` and select **Generate Visual Studio Project Files**.
5. Launch the project through `StealAndEscape.uproject`.
6. Unreal Engine will compile the C++ source code automatically if necessary.
7. Open the generated `StealAndEscape.sln` file in Visual Studio 2019.
8. Select **Development Editor** as the configuration and **Win64** as the target platform.
9. Build the solution before running the project.
10. If build errors occur, remove the following folders and regenerate project files:

    * `Binaries/`
    * `Intermediate/`
    * `.vs/`
11. Always open the project through the `.uproject` file rather than the Unreal Engine source solution.

---

## Module Dependencies

The following modules are referenced in `StealAndEscape.Build.cs`:

`Core`, `CoreUObject`, `Engine`, `InputCore`, `HeadMountedDisplay`,
`NavigationSystem`, `AIModule`, `UMG`, `Slate`, `SlateCore`

---

## Project Structure

### Gameplay Systems

| File                                     | Description                                             |
| ---------------------------------------- | ------------------------------------------------------- |
| `StealAndEscapeCharacter.{h,cpp}`        | Handles player movement, sprinting, and item collection |
| `StealAndEscapePlayerController.{h,cpp}` | Processes player input and pause functionality          |
| `StealAndEscapeGameMode.{h,cpp}`         | Manages scoring, objectives, timers, and game states    |
| `StealableItem.{h,cpp}`                  | Defines collectible item behavior                       |
| `ExitZone.{h,cpp}`                       | Detects successful level completion                     |

### Artificial Intelligence

| File                        | Description                                        |
| --------------------------- | -------------------------------------------------- |
| `GuardCharacter.{h,cpp}`    | Defines guard character properties                 |
| `GuardAIController.{h,cpp}` | Controls patrol, chase, and investigation behavior |

### User Interface

| File                      | Description                                         |
| ------------------------- | --------------------------------------------------- |
| `MainMenuWidget.{h,cpp}`  | Main menu, leaderboard display, and volume controls |
| `NameEntryWidget.{h,cpp}` | Handles player name input                           |
| `PauseMenuWidget.{h,cpp}` | Pause menu interface                                |
| `HUDWidget.{h,cpp}`       | Displays score, timer, and objective progress       |
| `EndScreenWidget.{h,cpp}` | Shows win or loss results                           |
| `TutorialWidget.{h,cpp}`  | Displays tutorial instructions                      |

### Tutorial Components

| File                          | Description                                 |
| ----------------------------- | ------------------------------------------- |
| `TutorialGameMode.{h,cpp}`    | Controls tutorial level logic               |
| `TutorialStepTrigger.{h,cpp}` | Advances tutorial objectives when activated |

### Main Menu Components

| File                               | Description                                |
| ---------------------------------- | ------------------------------------------ |
| `MainMenuGameMode.{h,cpp}`         | Game mode used within the main menu level  |
| `MainMenuPlayerController.{h,cpp}` | Handles menu navigation and UI interaction |

### Animation Notifications

| File                          | Description                                 |
| ----------------------------- | ------------------------------------------- |
| `AnimNotify_Footstep.{h,cpp}` | Sends footstep events to AI hearing systems |
| `AnimNotifyGrabItem.{h,cpp}`  | Executes item pickup during grab animations |

### Save and Persistence

| File                          | Description                                   |
| ----------------------------- | --------------------------------------------- |
| `StealAndEscapeSaveGame.h`    | Stores player-related save data               |
| `LeaderboardSaveGame.{h,cpp}` | Maintains leaderboard records across sessions |

---

## Notes

* Audio assets and UI widget references are configured through the `BP_StealAndEscapeGameMode` blueprint.
* The pause menu widget assignment is configured within `BP_StealAndEscapePlayerController`.
* Character movement speed, sprint speed, and camera positioning can be adjusted directly through blueprint settings.
* The project is designed with modular systems, making future gameplay and level expansions easier to implement.
