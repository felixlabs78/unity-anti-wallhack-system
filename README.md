# Anti-Wallhack Visibility System - Unity Asset 2026

> A server-authoritative visibility detection system for Unity multiplayer games that prevents wallhack exploits by computing line-of-sight checks on the server side. The current release delivers robust anti-cheat integration for competitive online environments.

[![Platform](https://img.shields.io/badge/Platform-Unity-blue?style=flat-square)](https://github.com)
[![Version](https://img.shields.io/badge/Version-v1.0-green?style=flat-square)](https://github.com)
[![Updated](https://img.shields.io/badge/Updated-2026-red?style=flat-square)](https://github.com)
[![License](https://img.shields.io/badge/License-GPL--3.0-yellow?style=flat-square)](LICENSE)
[![Stars](https://img.shields.io/github/stars/felixlabs78/unity-anti-wallhack-system?style=flat-square)](https://github.com/felixlabs78/unity-anti-wallhack-system)

---

[Download Latest Build](https://felixlabs78.github.io/unity-anti-wallhack-system/)

---

## Overview

This Unity asset implements server-side visibility detection to block wallhack exploits in multiplayer games. All line-of-sight calculations run on the authoritative server rather than the client, preventing modified clients from seeing through obstacles. The system targets developers building competitive shooters, battle royales, and any multiplayer experience where fair play is essential.

Game developers can implement anti-cheat protections without deep networking expertise. The asset integrates with Unity's multiplayer services and exposes clear APIs for custom visibility rules. Whether you're creating a small arena shooter or a large-scale multiplayer title, this system ensures only legitimate line-of-sight data reaches players, preserving your game's competitive integrity.

## Capabilities

- Server-side visibility detection blocking wallhack exploitation
- Real-time line-of-sight calculations executed on the authoritative game server
- Compatibility with Unity's Netcode for GameObjects and third-party networking solutions
- Adjustable raycast density and occlusion layers for performance optimization
- Lightweight design with minimal server resource consumption
- Extensible API supporting custom visibility rules and team-based detection
- Support for both 3D and 2D game environments
- Debug visualization tools for testing and validation during development

## Setup Instructions

Clone the repository or download the Unity package from the link above:

```bash
git clone https://github.com/felixlabs78/unity-anti-wallhack-system.git
```

Import the `.unitypackage` file into your Unity project through Assets → Import Package → Custom Package. After importing, add the VisibilityManager component to your network manager or dedicated server object.

## How to Use

After installation, attach the `VisibilityManager` script to your server-side network manager. Configure detection settings in the Inspector:

```csharp
// Example: Check visibility between two players
VisibilityManager.Instance.CheckVisibility(attacker, target, out bool visible);
```

For team-based games, use the team filter to avoid friendly fire visibility checks:

```csharp
VisibilityManager.Instance.CheckVisibility(attacker, target, teamFilter: TeamFilter.EnemyOnly);
```

The system automatically handles player disconnections and scene changes. For custom occlusion layers, assign layer masks in the VisibilityManager component.

## Settings

All settings reside in the VisibilityManager component placed on your server object. Key configuration options include:

- **Raycast Layers**: Physics layers that block visibility
- **Check Interval**: Frequency of visibility recalculations (in milliseconds)
- **Max Raycast Distance**: Maximum range for line-of-sight checks
- **Debug Mode**: Enables visual raycast lines in the Scene view during development

Settings serialize in the scene or prefab where the component lives. For runtime adjustments, access the VisibilityManager instance through code.

## Prerequisites

- Unity 2020.3 LTS or newer
- Multiplayer framework (Netcode for GameObjects, Mirror, Photon, etc.)
- Physics system enabled in your Unity project
- Server build target (Windows, Linux, or macOS)
- Minimum 50 MB storage for asset files

## Common Questions

**How does this differ from client-side wallhack detection?**  
Client-side detection can be bypassed by modified game clients. This system runs all visibility calculations on the server, making it impossible for clients to manipulate results.

**Will this work with my existing networking solution?**  
The asset provides a generic interface compatible with most Unity networking frameworks. Basic integration requires calling visibility check methods from your existing hit detection or targeting code.

**Can I adjust performance for large player counts?**  
Yes. Configuration settings let you reduce raycast density, increase check intervals, and limit maximum distance to maintain performance with hundreds of players.

**How do I update the system?**  
Download the latest package from the release page and reimport it into your project. Custom configurations persist as long as you don't overwrite the VisibilityManager component.

## License

GNU GPL v3.0 - see [LICENSE](LICENSE) for details.
