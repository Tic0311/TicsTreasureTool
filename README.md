# Tic's Settler Toolkit

An in-game settler, trait, inventory, and world utility mod for **Dungeon Settlers**.

> **Compatibility:** developed and tested with **Dungeon Settlers v0.4.19 Early Access** on Windows x64.  
> **Mod version:** 1.0.0  
> **Loader:** BepInEx 6 IL2CPP  
> **Tested BepInEx build:** 6.0.0-be.788

Dungeon Settlers is in Early Access. A future game update may change internal game systems used by this mod and can partially or completely break compatibility. If the game updates and the toolkit stops working, check for a newer toolkit release before troubleshooting your save.

## Features

Tic's Settler Toolkit opens inside the game with **F8** and provides four sections:

- **Settler** — edit health, energy, hunger, stress, level, experience, and skill points.
- **Traits** — view real equipped recruit traits, edit generated attributes, and add, replace, or remove known Main/Sub traits. Race is intentionally left unchanged.
- **Inventory** — view a settler's carried inventory and edit stack quantities for items the game stores as stackable inventory entries.
- **World** — edit settlement gold and change game speed.

Additional behavior:

- Resizable and draggable in-game window.
- Input is blocked behind the toolkit window while clicks outside the window continue to reach the game.
- Trait lists are learned over time from legitimate recruit/settler traits encountered in gameplay.
- Learned traits are saved locally and remain available across future saves and sessions.
- Trait editing supports up to four displayed Main traits and four displayed Sub traits in the toolkit.

## Requirements

- **Dungeon Settlers v0.4.19 Early Access**
- **Windows x64**
- **BepInEx 6 Unity IL2CPP x64**

The mod was tested with BepInEx **6.0.0-be.788**. BepInEx's official IL2CPP documentation requires a Bleeding Edge build for IL2CPP games.

Official BepInEx resources:

- BepInEx IL2CPP installation guide: https://github.com/BepInEx/bepinex-docs/blob/master/articles/user_guide/installation/unity_il2cpp.md
- BepInEx Bleeding Edge builds: https://builds.bepinex.dev/projects/bepinex_be

## Installing BepInEx

If you already have a working BepInEx 6 IL2CPP installation for Dungeon Settlers, skip to **Installing Tic's Settler Toolkit**.

1. Open the BepInEx Bleeding Edge builds page:
   https://builds.bepinex.dev/projects/bepinex_be

2. Download the Windows 64-bit IL2CPP archive. For the tested configuration, the filename is:

   `BepInEx-Unity.IL2CPP-win-x64-6.0.0-be.788+5b766a3.zip`

3. In Steam, right-click **Dungeon Settlers** and choose:

   **Manage → Browse local files**

4. This opens the game's root folder. It is the folder containing the Dungeon Settlers executable.

5. Extract the contents of the BepInEx ZIP **directly into that root folder**.

   Do not extract BepInEx into a separate subfolder.

6. Start Dungeon Settlers once.

   The first IL2CPP launch can take longer than normal because BepInEx generates the files it needs.

7. Close the game after reaching the main menu.

8. Confirm that BepInEx created folders/files such as:

   ```text
   Dungeon Settlers/
   ├── BepInEx/
   │   ├── config/
   │   ├── plugins/
   │   └── LogOutput.txt
   ├── doorstop_config.ini
   └── ...
   ```

If the `BepInEx` folder and `LogOutput.txt` were created, BepInEx is loading.

## Installing Tic's Settler Toolkit

### Recommended: release ZIP

1. Download the latest `TicsSettlerToolkit-v1.x.x.zip` release.
2. Open the Dungeon Settlers root folder.
3. Extract the ZIP into the game root.
4. Allow the included `BepInEx` folder to merge with the existing `BepInEx` folder.

The final DLL path should be:

```text
Dungeon Settlers/
└── BepInEx/
    └── plugins/
        └── TicsSettlerToolkit/
            └── TicsSettlerToolkit.dll
```

### Manual DLL install

If you only have the DLL:

1. Open `BepInEx/plugins/`.
2. Create a folder named `TicsSettlerToolkit`.
3. Place `TicsSettlerToolkit.dll` inside it.
4. Start the game.

## Confirming the Mod Loaded

Start Dungeon Settlers and load a settlement.

Press **F8**.

If installation is correct, **Tic's Settler Toolkit** will open.

You can also confirm the plugin in:

`BepInEx/LogOutput.txt`

Look for a line similar to:

`Tic's Settler Toolkit loaded. Press F8 in-game.`

## Using the Toolkit

### General controls

- **F8** — open or close the toolkit.
- **Drag the top header** — move the window.
- **Drag the lower-right corner** — resize the window.
- **Clicks inside the toolkit** — interact with toolkit controls.
- **Clicks outside the toolkit** — continue interacting with Dungeon Settlers.
- Game objects physically behind the toolkit window do not receive accidental clicks.

### Settler tab

Use the arrows at the top to choose a settler.

Editable values include:

- Body Health
- Energy
- Hunger
- Stress
- Level
- Experience
- Main Skill Points
- Sub Skill Points

Enter a value and click **SET**.

Changes are written to the live character data. Some game UI elements may update on their own refresh cadence.

### Traits tab

The Traits tab contains two systems.

#### Generated attributes

You can edit:

- Strength
- Constitution
- WillPower
- Intelligence
- Agility
- Perception

Enter a value and click **SET**.

#### Main and Sub traits

The toolkit reads the character's real recruit traits and separates them into Main and Sub trait groups.

For each known trait you can:

- **Add** a new trait.
- **Replace** an existing trait.
- **Remove** an existing trait.

Race is displayed only for context and is not editable.

The toolkit currently supports up to four displayed traits in each category.

### Learned trait catalog

Dungeon Settlers does not expose its complete internal master trait database to the mod through the current IL2CPP interface. To avoid showing unrelated status/gameplay affecters as if they were recruit traits, the toolkit uses a verified learning system.

When the game exposes a legitimate Main or Sub trait on a recruit or settler, the toolkit records it locally.

The learned catalog is stored at:

```text
BepInEx/config/TicsSettlerToolkit/traits.json
```

That file is reused across saves and sessions. As you encounter additional recruit traits in normal gameplay, they can become available in the toolkit's selector.

Deleting `traits.json` resets the learned trait catalog.

### Inventory tab

The Inventory tab displays the selected settler's readable carried inventory.

For stackable entries:

1. Enter the desired quantity.
2. Click **SET**.

The inventory list is scrollable.

Do not use inventory quantity editing as an item-spawning system for equipment or unique/non-stackable objects. Dungeon Settlers handles those objects differently and forcing invalid quantities can create inconsistent inventory states.

### World tab

#### Settlement Treasury

Enter the desired amount of gold and click **SET**.

The underlying gold value changes immediately, but Dungeon Settlers' gold HUD may continue showing the old value until the game naturally refreshes it by **earning or spending gold**.

#### Time Control

Available game-speed controls:

- 0.5x
- 1x
- 2x
- 5x

Return the game to **1x** for normal speed.

## Updating the Toolkit

1. Close Dungeon Settlers.
2. Download the new release.
3. Replace the old `TicsSettlerToolkit.dll` with the new DLL.
4. Keep `BepInEx/config/TicsSettlerToolkit/traits.json` if you want to preserve your learned trait catalog.

Read the release notes before using a new toolkit version with an existing save.

## Uninstalling

1. Close Dungeon Settlers.
2. Delete:

   `BepInEx/plugins/TicsSettlerToolkit/`

3. Optional: delete the learned trait data at:

   `BepInEx/config/TicsSettlerToolkit/`

Removing the plugin does not uninstall BepInEx.

## Troubleshooting

### F8 does nothing

Check `BepInEx/LogOutput.txt`.

Confirm that:

- BepInEx itself loaded.
- `TicsSettlerToolkit.dll` is in the correct plugins folder.
- You installed the **Unity IL2CPP Windows x64** BepInEx build.
- The game version is **Dungeon Settlers v0.4.19**.

### The game updated and the toolkit stopped working

This mod accesses internal Dungeon Settlers classes and methods. Early Access updates can rename or restructure those internals.

Do not assume a release tested on v0.4.19 is compatible with a later game build. Check for an updated toolkit release.

### Gold changed but the HUD did not

Earn or spend gold once. The toolkit changes the live value, while the game's HUD may not redraw the amount until a normal gold transaction occurs.

### A trait I have seen before is missing

The full game trait database is not currently exposed through the interface available to the mod. The toolkit only offers traits it has verified through gameplay.

Encountering the trait on a recruit/settler can add it to the learned catalog for future use.

### I want to report a bug

Include:

- Dungeon Settlers version.
- Tic's Settler Toolkit version.
- BepInEx build number.
- What you were trying to change.
- `BepInEx/LogOutput.txt`.

## Compatibility

| Component | Tested version |
| --- | --- |
| Dungeon Settlers | **v0.4.19 Early Access** |
| Tic's Settler Toolkit | **v1.0.0** |
| BepInEx | **6.0.0-be.788, Unity IL2CPP Windows x64** |
| Platform | **Windows x64** |

Future Dungeon Settlers updates are **not automatically supported**.

## License

MIT. See [LICENSE](LICENSE).

## Disclaimer

Tic's Settler Toolkit is an unofficial community mod and is not affiliated with or endorsed by the developers or publisher of Dungeon Settlers.

Back up important saves before using game-modification tools.
