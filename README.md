# AccountSwitcher189

AccountSwitcher189 is a client-side account switcher mod for **Minecraft Java Edition 1.8.9**, built with **Minecraft Forge 11.15.1.2318** and **Java 8**.

The project adds an account switcher directly to the Minecraft main menu. Its purpose is to let the player authenticate a Microsoft account through Microsoft's official authorization flow and switch the active Minecraft session without closing the game.

## Features

- Account switcher accessible from the Minecraft 1.8.9 main menu
- Microsoft account authentication using Microsoft OAuth Device Code flow
- Xbox Live and XSTS authentication followed by Minecraft Services authentication
- Retrieval of the authenticated Minecraft Java profile (UUID and player name)
- Switching between authenticated sessions without restarting Minecraft
- Preservation of the session that was used to launch Minecraft
- Optional local/offline profiles for offline-mode use
- No Microsoft password is requested or stored by the mod

## Microsoft / Minecraft authentication

For Microsoft accounts, AccountSwitcher189 uses a public-client authentication flow. The user authorizes access on Microsoft's own website using a device code. The mod then performs the standard authentication chain:

1. Microsoft OAuth
2. Xbox Live authentication
3. XSTS authorization
4. Minecraft Services authentication
5. Minecraft Java profile retrieval

The application does **not** embed a client secret and does **not** ask users to enter their Microsoft password into Minecraft.

This repository is also the public project information page associated with the application's Microsoft/Minecraft AppID registration.

## Requirements

- Minecraft Java Edition 1.8.9
- Minecraft Forge 11.15.1.2318
- Java Development Kit 8

## Building

Configure the application's own Microsoft Client ID in the local build configuration, then run:

```bat
gradlew.bat setupDecompWorkspace
gradlew.bat build
```

The compiled mod will be placed in `build/libs/`.

## Security and privacy

AccountSwitcher189 is designed so that Microsoft credentials are entered only on Microsoft's authentication pages. Microsoft passwords are never requested or stored by the mod.

The session used to launch Minecraft is kept in memory for the running game so the user can switch back to it. Authentication tokens and refresh tokens must be treated as sensitive credentials and should never be published in this repository, logs, screenshots, or issue reports.

## Offline profiles

Offline profiles are intended for local/offline-mode environments. They do not grant ownership of Minecraft and cannot bypass authentication on servers configured with `online-mode=true`.

## Project status

The mod is currently under development. Microsoft OAuth, Xbox/XSTS and Minecraft Services integration are being developed for the Minecraft 1.8.9 Forge client.

## Disclaimer

This is an independent community project. It is not affiliated with, endorsed by, or sponsored by Mojang Studios, Microsoft, Minecraft, MultiMC, or Forge.

Minecraft is a trademark of Microsoft Corporation.
