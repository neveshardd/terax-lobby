# Terax Lobby

The `terax-lobby` project is a comprehensive Minecraft/Bukkit/Spigot plugin designed to serve as a central lobby or hub for a server network. Its primary purpose is to provide an engaging and highly customizable starting experience for players, facilitating navigation to different game modes or server instances, and offering various interactive elements within the lobby world. It integrates deeply with a custom `Kiwizin` core framework, suggesting it's part of a larger ecosystem by 'slickcollections'.

## Features

*   **Interactive Server Selector GUI**: Seamless server switching through a customizable in-game menu (`MenuLobbies`).
*   **Customizable NPCs**: Create and manage Non-Player Characters (NPCs) with unique skins, hand items, and configurable actions (e.g., `PlayNPC` for server selection, `DeliveryNPC` for item delivery).
*   **Dynamic Holograms**: Display floating text holograms above NPCs or at specific locations to provide information or visual flair.
*   **Configurable Player Hotbar**: Define and customize player hotbar items with associated actions (e.g., opening menus, connecting to servers).
*   **Advanced Player Tagging**: Manage player name tags, prefixes, and suffixes, potentially leveraging Bukkit's team system.
*   **Extensive Configuration**: Comprehensive options for plugin behavior, customizable messages, and in-game elements through various YAML files.
*   **Multi-Lobby Support**: Designed to support multiple lobby instances and server entries, ideal for BungeeCord or Velocity server networks.
*   **Administrative Commands**: Easy in-game management of NPCs, spawn points, and plugin settings (e.g., `/kl build`, `/kl npcplay`, `/kl setspawn`, `/kl give`).
*   **Kiwizin Core Integration**: Leverages a core framework (`Kiwizin Core`) for consistent functionality and data management across a server network.
*   **Comprehensive Event Handling**: Manages a wide range of player interactions, chat, inventory, and entity behavior specific to the lobby environment.

## Installation

To install and run the Terax Lobby plugin on your Minecraft server, follow these steps:

### Prerequisites

*   A running Minecraft server (Spigot, Paper, Purpur, or compatible fork) version 1.8.8 or higher (check `build.gradle` for exact compatibility).
*   Java 8 or newer.

### Steps

1.  **Download the Plugin**:
    *   Obtain the latest `TeraxLobby.jar` file from the [releases page](https://github.com/neveshardd/terax-lobby/releases) (or compile it yourself, see "Building from Source").

2.  **Install Required External Plugins (if not bundled)**:
    *   While many dependencies might be shaded into the main JAR, some core plugins often need to be installed separately for optimal functionality or due to their nature:
        *   **[ProtocolLib](https://dev.bukkit.org/projects/protocollib)**: Required for advanced packet manipulation, used by the Hologram system.
        *   **[Citizens2 / NPCLib](https://www.spigotmc.org/resources/citizens.13811/)**: Essential for the custom NPC system.
        *   **[HolographicDisplays](https://dev.bukkit.org/projects/holographic-displays)** (or similar Hologram library): Potentially used for the Hologram system, though `HologramLibrary` might be an internal abstraction.
    *   Place these `.jar` files into your server's `plugins/` folder.

3.  **Place Terax Lobby**:
    *   Drag and drop the `TeraxLobby.jar` file into your server's `plugins/` folder.

4.  **Restart Your Server**:
    *   Restart your Minecraft server to load the plugin and generate the default configuration files.

5.  **Configure**:
    *   After the first startup, configuration files will be generated in `plugins/TeraxLobby/`.
    *   Edit `config.yml`, `language.yml`, `hotbar.yml`, `entries.yml`, and `lobbies.yml` to customize the plugin to your server's needs.

### Building from Source (for Developers)

If you wish to compile the plugin yourself:

1.  **Clone the Repository**:
    ```bash
    git clone https://github.com/neveshardd/terax-lobby.git
    cd terax-lobby
    ```
2.  **Build with Gradle**:
    ```bash
    ./gradlew clean shadowJar
    ```
3.  **Find the JAR**:
    *   The compiled plugin JAR will be located in the `build/libs/` directory, typically named `TeraxLobby.jar`.

## Usage

Upon successful installation and server restart, the Terax Lobby plugin will be active.

### Administrative Commands

The primary administrative command is `/kl` (aliased from `/lobby` as defined in `plugin.yml`).

*   `/kl help`: Display available commands.
*   `/kl build [on/off]`: Toggle build mode for administrators in the lobby world.
*   `/kl npcplay create <name> <server_key>`: Create a new Play NPC for server selection.
*   `/kl npcplay remove <id>`: Remove an existing Play NPC.
*   `/kl npcdelivery create <name>`: Create a new Delivery NPC.
*   `/kl npcdelivery remove <id>`: Remove an existing Delivery NPC.
*   `/kl setspawn`: Set the main spawn point for the lobby.
*   `/kl give <player> <item_id>`: Give a player a specific item (likely a custom hotbar item).
*   `/kl update`: Reload configurations or update plugin components.

### Player Experience

*   **Server Selector**: Players can access the server selector GUI, often via a hotbar item or a specific command, to navigate to different game modes or servers.
*   **Interactive NPCs**: Players can interact with `PlayNPCs` to join specific servers or with `DeliveryNPCs` for special actions.
*   **Custom Hotbar**: Players will receive a customized hotbar with items configured by the server, allowing quick access to menus, server warps, and other functionalities.
*   **Lobby Environment**: The plugin manages various aspects of the lobby world, including preventing unwanted interactions (breaking blocks, PvP, etc.) and handling player joins/quits.

### Configuration Files

*   `config.yml`: Main plugin settings and general configurations.
*   `language.yml`: Customizable messages for localization and server branding.
*   `hotbar.yml`: Defines the items present in the player's hotbar and their associated actions.
*   `entries.yml`: Configures server entries, including holograms, skins, and hand items for NPCs or menu items.
*   `lobbies.yml`: Defines different lobby instances and their properties.

## Tech Stack

*   **Language**: Java
*   **Build Tool**: Gradle
*   **Minecraft API**: Bukkit/Spigot API
*   **Internal Framework**: Kiwizin (a custom framework by 'slickcollections')
*   **External Libraries/APIs**:
    *   ProtocolLib (for advanced packet manipulation, used by HologramAdapter)
    *   NPCLib (for creating and managing Non-Player Characters)
    *   HologramLibrary (for managing in-game holograms)

## Project Structure

The project is organized into several packages, reflecting its modular design:

```
terax-lobby/
├── gradle/                  # Gradle wrapper files
├── src/
│   └── main/
│       ├── java/
│       │   └── dev/slickcollections/kiwizin/lobby/
│       │       ├── cmd/             # Custom command registration and subcommands (e.g., /kl build, /kl npcplay)
│       │       ├── hook/            # Integrations with external systems (ProtocolLib, Kiwizin Core, Hotbar)
│       │       ├── listeners/       # Event handlers for player, entity, and server events
│       │       ├── lobby/           # Core lobby features: NPCs (PlayNPC, DeliveryNPC), ServerEntry, Lobby management, NPC traits
│       │       ├── menus/           # Interactive GUI menus (e.g., MenuLobbies for server selection)
│       │       ├── utils/tagger/    # Utilities for player name tagging, prefixes, and suffixes
│       │       ├── Language.java    # Manages plugin messages and localization
│       │       └── Main.java        # Primary plugin entry point for Bukkit/Spigot
│       └── resources/
│           ├── config.yml           # Main plugin settings
│           ├── entries.yml          # Server entry configurations
│           ├── hotbar.yml           # Player hotbar item definitions
│           ├── lobbies.yml          # Lobby instance configurations
│           └── plugin.yml           # Plugin metadata (name, version, main class, commands)
└── build.gradle             # Gradle build script
```

## Contributing

Contributions are welcome! If you have suggestions, bug reports, or want to contribute code, please feel free to open an issue or submit a pull request on the [GitHub repository](https://github.com/neveshardd/terax-lobby).

## License

This project is likely distributed under an open-source license, though a specific license file was not found in the provided analysis. Please check the repository for the most up-to-date licensing information.
