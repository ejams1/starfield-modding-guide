# starfield-modding-guide
Tips/guidance for modding Starfield; mostly a reference for myself. Make sure you check footnotes for additional info, and I welcome any suggestions or corrections as issues or PRs!

See my current load order and mod list [on Load Order Library here](https://loadorderlibrary.com/lists/a-better-starfield-3#modlist.txt).

> [!IMPORTANT]
> I have only used Mod Organizer 2 for Starfield modding and cannot provide much insight into Vortex setup or support; if you have more experience with it, feel free to open a PR and id be glad to include it

## Setup

1. Download [latest MO2](#mod-organizer-2) and configure a portable instance
1. Copy the entire Starfield directory from Steam into the MO2 directory and rename to `Stock Game Folder`; rationale for using Stock Game Folder over Root Builder is that while it uses more storage, it will maintain the existing version of the game even if an update is released so it won't break
1. In the settings, change Paths to point to `Stock Game Folder`
1. In the MO2 directory, create a folder called `tools` and download [all tools](#tools) into here then add each one as an executable in MO2
1. Install the latest [Starfield Script Extender (SFSE)](https://www.nexusmods.com/starfield/mods/106) directly into `Stock Game Folder`
1. Download `StarfieldPrefs.ini` and `StarfieldCustom.ini` and put in `Documents/My Games/Starfield` (and in `mo2/profiles/<profile>` for good measure)
1. Download the `Ultra.ini` preset, and put in `Stock Game Folder` (this is tweaked to have settings more like Medium, but better meshes from Ultra)
1. Replace the Nvidia DLSS plugin inside `Stock Game Folder` with the latest from [TechPowerup](https://www.techpowerup.com/download/nvidia-dlss-dll/)
1. Install all mods, organize order, etc
1. Pack loose files and disable loose file loading - see below
1. Delete shader cache - see below

## Tools

### xEdit
- Create patches, identify conflicts, etc.
- Latest dev version for best Starfield support; `4.1.5k` at the time of writing
- Download from xEdit discord from #xedit-builds

### BSArchPro64
- Pack loose files into BA2 or unpack BA2
- Comes with xEdit

### Mod Organizer 2
- Latest dev version for best Starfield support; `2.5.3dev2` at the time of writing
- Download from MO2 discord from #dev-builds

### BA2Upgrader
- Can upgrade BA2 v2 textures to BA2 v3 including the use of LZ4 compression for better performance in Starfield
- Download from [Nexus Mods](https://www.nexusmods.com/starfield/mods/1192)

### Starfield NIF migration tool
- Can fix meshes that were created for older versions of Starfield that no longer work on newer versions
- Download from [Nexus Mods](https://www.nexusmods.com/starfield/mods/9234)

### Bethini Pie
- ini tweaking tool with useful utilities
- Download from [Nexus Mods](https://www.nexusmods.com/site/mods/631)

### JPEXS-Decompiler

- For editing `.swf` files usually found in `interface/` files such as icons and fonts
- Download from [Github](https://github.com/jindrapetrik/jpexs-decompiler)

## Tips

- Using [SKK Fast Start](https://www.nexusmods.com/starfield/mods/5971) can cause issues with [weapon sound fixes](https://www.nexusmods.com/starfield/mods/10776?tab=posts) resulting in weapons not having sound; supposedly it goes away after awhile or possible reload but starting vanilla is safest if using both of these
  - EDIT: I have also noticed textures not loading in when using quick start and starting in the Lodge - they returned on a subsequent reload similar to the audio issues
- Ensure that `.asi` mods like [Disk Cache Enabler](https://www.nexusmods.com/starfield/mods/2245) sit at the root of their mod folder as the [updated ASI loader](https://www.nexusmods.com/starfield/mods/8055) expect them to be at the root of `Data/`; example: `Disk Cache Enabler/diskCacheEnabler.asi`
  - You will know it is in the right spot and loading correctly if you start the game, exit, and see a line in `Documents\My Games\Starfield\SFSE\Logs\SFSEAsiLoader.log` that says something like `[10/23/24 19:59:10][info](main.cpp:114) Loading C:...\Stock Game Folder\Data\diskCacheEnabler.asi` followed by `Loaded plugin successfully`
- The armors `Banshee`, `Exile`, `HyperGuardian`, `Mark M` and `Pathfinder` all contain outdated meshes, and require updating (or [see Luxor's patches](https://www.nexusmods.com/starfield/mods/9468))
- [Luma](https://www.nexusmods.com/starfield/mods/4821) seems to cause black crushing on my OLED displays but likely needs further tweaking; [NaturalLUTs](https://www.nexusmods.com/starfield/mods/1119) plus the default HDR (or Nvidia RTX HDR) seem to be good enough
- [Console Command Runner (CCR)](https://www.nexusmods.com/starfield/mods/7318) mods are no longer relevant as they can be easily recreated natively in the Creation Kit as an `.esm`; for example, I recreated [Instant Scan](https://www.nexusmods.com/starfield/mods/759) this way in about 5 minutes
- [The Dualsense icons mod](https://www.nexusmods.com/starfield/mods/215) apparently needs an update as there are some missing icons in the Creations menu
- Speaking of which, files from the `interface/` folder such as `.swf` files can be edited with [this tool](#jpexs-decompiler)

## Unofficial Patch vs. Community Patch

### Context

In previous Bethesda games, there always seemed to be a unified unofficial patch mod that many would contribute to resulting in a simple end user experience - install one patch, fix all community-known issues. However, there was drama involving a developer of those patches and so to avoid that further, a community effort was formed resulting in the [Starfield Community Patch (SFCP)](https://www.nexusmods.com/starfield/mods/1). This didn't stop the developer from continuing to create their own patch though, the [Unofficial Starfield Patch (USFP)](https://www.nexusmods.com/starfield/mods/143).

### Which Should I Use?

I liked [this answer from Deebz_](https://www.reddit.com/r/starfieldmods/comments/1fvqnwb/comment/lqa6vnx/?utm_source=share&utm_medium=web3x&utm_name=web3xcss&utm_term=1&utm_content=share_button):

> [Community Patch changelog](https://www.starfieldpatch.dev/changelog)
> 
> [Unofficial Patch changelog](https://www.afkmods.com/Unofficial%20Starfield%20Patch%20Version%20History.html)
>
> I’m on the SFCP team, but I would personally advise looking at both changelogs and coming to your own conclusion about which to use.
>
> Objectively, the Community Patch fixes a lot more right now, but both changelogs have some differences from one another. Up to you to decide which set of fixes you want, or if they are even necessary to you in the first place. Both mods are stable and safe to use, so it really just comes down to that.

That being said, I also appreciate the collaborative effort to build the community patch, so my personal preference is that one.

## Removing BlueprintShips-Starfield.esm As Master

Many mods have `BlueprintShips-Starfield.esm` listed as a master which LOOT will report as an issue. So many mods have this as early versions of xEdit set it as master as it was thought to be necessary at the time - this has since been proven unnecessary. The downside to this is that `BlueprintShips-Starfield.esm` always loads last, so any mods with it listed as master will load after it _even if_ you sort your load order otherwise.

Here is how to remove it:

> [!NOTE]
> Future builds of xEdit will include the ability to remove it as well, but for now we will use the Creation Kit

1. Put the affected `.esm` file in `base game/Data`, where `base game/` is the primary Starfield installation where the Creation Kit is also installed
1. Load the Creation Kit
1. Click `File` -> `Data`
1. Find your mod and select it
1. In the right column, a list of masters will be shown including - select `BlueprintShips-Starfield.esm`
1. Press `Ctrl + Del` which will remove it
1. Repeat for other affected mods
1. Confirm all is good by sorting with LOOT again which should now report no `BlueprintShips-Starfield.esm`

## ini Files Explained

`ini` files are the configuration files that host the in-game settings you choose in the options menu plus more granular settings that are not exposed in-game.

To get the best performance and ensure your settings are loading properly, let's examine what each file is and how it works. This section is [adapted from the fantastic STEP guide here](https://stepmodifications.org/forum/topic/19019-starfield-default-values-for-all-known-valid-ini-settings/).

### StarfieldPrefs.ini

Located in `Documents/My Games/Starfield/`.

Holds options like resolution, camera, controls, difficulty and more; most of what you see in the options menu.

However, the most important section is `[Quality]` - this outlines the render settings for each customizable quality setting. The values map to one of the Low/Medium/High/Ultra files found in `Stock Game Folder` - for example, if you choose `uContactShadows=1`, it will use the value configured in `Low.ini`; likewise, `uContactShadows=3` will load the value from `Ultra.ini`.

This gets confusing fast since this file is really just pointing to each of the other files for different values, so to make this easier, it is suggested to modify one of the base profiles (usually `Ultra.ini`) to exactly what you want, and then in `StarfieldPrefs.ini` you can set each quality setting to `3` so that they all point to just that file. This is how my sample ini's are configured in this repo.

### StarfieldCustom.ini

Located in `Documents/My Games/Starfield/`.

This file holds other configurations such as `[Archive]` which holds the list of all BA2 files to load.

### Low/Medium/High/Ultra.ini

Located in `Stock Game Folder`.

These hold the granular quality settings for each type of rendering option you can set in-game. The `Low.ini` holds the values for everything that would be set in the `Low` profile etc.

## Launch a Mod Organizer 2 Profile Through Steam

> [!NOTE]
> This applies to _all_ Mod Organizer 2 mod lists, not just Starfield.

If you would like Steam functionality to while using mods, you can configure Steam to point to your modded directory. This does not inherently disable achievements unless you have mods that do so, and allows opening the Steam in-game interface, use of Steam input, and easily launching your modded list through Steam Remote Play.

1. Ensure you have the script extender installed in `Stock Game Folder`
1. In MO2, edit the executables and click the `+` to add one
1. Name it `SFSE`, and for the binary, locate the `sfse_loader.exe` and select it
1. Now in Steam, right-click on Starfield, click `Properties`
1. In the `General` tab under `Launch Options`, enter the following:

```
"path\to\ModOrganizer.exe" "moshortcut://:SFSE" %command%
```
where `path\to\ModOrganizer.exe` is the full path to the MO2 executable. For example, here is mine:

```
"G:\Mods\dev-modlists\a-better-starfield\ModOrganizer.exe" "moshortcut://:SFSE" %command%
```

## Deleting The Shader Cache

### Context

Starfield runs on DirectX 12 which compiles shaders into a cache the first time you launch the game, and also as you play the game. After a shader is compiled, it remains in the cache allowing it to be fetched quicker and thus leading to less stutter as you play through the game.

The shader cache becomes invalid when there is a driver update, which will force the game to recompile the shaders on launch and you will likely experience more stutter while playing for awhile after a driver update.

Certain issues can arise from a stale shader cache as you mod your game and make other types of changes - things like flickering or reduced performance.

### Solution

[This guide from Reddit](https://www.reddit.com/r/Starfield/comments/16703yo/guide_how_to_force_recompile_shaders/) explains how to clean your shader cache on each kind of system. Since I use Nvidia, the steps are as follows:

1. In Windows Explorer, enter this: `shell:LocalAppDataLow\NVIDIA\PerDriverVersion\DXCache`
1. Delete all files from here; some may say they are in use, and you can restart your PC in safe mode and try again
1. Then, navigate to `%LOCALAPPDATA%\Starfield\`
1. Delete `Pipeline.cache`

If you can't do those, updating your driver should also wipe the cache.

## Performance Benchmarking

I needed a way to quickly identify possible problematic mods in my load order, so I came up with the following.

### Pre-requisites

- [SKK Fast Start](https://www.nexusmods.com/starfield/mods/5971) - to quickly get in-game
- [CapFrameX](https://www.capframex.com/) - to track performance

### Methodology

1. Download and start up CapFrameX
1. Sort load order to test and start game
1. Start a new game
1. You will load in New Atlantis - leave all options as they are
1. Quickly choose a background and name, and finish character creator
1. Wait a few seconds for everything to load, then go in inventory and back out - SKK should say that it has initialized
1. Once all notifications stop, hit `F11` which begins the recording
1. Run straight through, past the crowds, up the ramp; at the top, turn around to look back down the ramp at the crowd, then turn back and finish by walking to the closest sign
1. Hit `F11` again to stop recording, and exit the game

This is _very_ rough and not ideal, but it provides a reasonable way to get an idea of how your load order performs in a demanding area of the game quickly.

## Packing Loose Files

Steps have been adapted from [this wonderful guide on Nexus](https://www.nexusmods.com/starfield/articles/578), please go endorse!

### Pre-requisites

- There are many tools that can pack/unpack, but the two I found most useful in terms of Starfield support, speed, and function are [BSArchPro64](#bsarchpro64) and [BA2Upgrader](#ba2upgrader); alternatives include `Archive2` (included with the Creation Kit) and [Cathedral Asset Optimizer](https://www.nexusmods.com/skyrimspecialedition/mods/23316)
- Ensure that your load order is configured such that all conflicts are resolved how you would like
- To find _all_ loose files, run `Explorer++` and look at the virtual game directory, then in the `Data` folder - all loose asset folders should be visible here
- I don't know why, but the Starfield ini files in my MO2 directory were not being loaded, and it was instead loading from my Documents folder still
- Pack loose textures using `Starfield - DDS` format, then use `BA2Upgrader` and upgrade to BA2 v3 using LZ4 compression for best performance

### Packing

This guide was adapated from a resource that used Archive2, so feel free to use that or if you are comfortable with it, use BSArchPro64.

1. In Archive2, load all your UI files (i.e. flash files) in your Interface folder and then in Settings set the Type to General and the Compression to None and then save the archive to the game root Data folder as MyMods - Interface.ba2.
1. Again in Archive2, load all your PEX scripts from your Scripts folder and then in Settings once again set the Type to General and the Compression to None and then save the archive to the game root Data folder as MyMods - Misc.ba2.
1. Once again in Archive2, load all your WEM files from your Sound folder and then in Settings set the Type to General and the Compression to None and then save the archive to the game root Data folder as MyMods - WwiseSounds.ba2.
1. Also in Archive2, load all your textures from your Textures folder and then in Settings set the Type to DDS and the Compression to LZ4 and then save the archive to the game root Data folder as MyMods - Textures.ba2.
1. Finally in Archive2 again, load everything left (i.e. Geometries, Materials, Meshes, Strings, etc.) and in Settings set the Type to General and the Compression to Default and then save the archive to the game root Data folder as MyMods - Main.ba2.

### Loading New Archives

Once you have made all of those archives, you then just need a way to load the archives into the game. You can use StarfieldCustom.ini to do this:

1. Place ", MyMods - Textures.ba2" at the end of the line beginning with "sResourceIndexFileList=" (ignore quotation marks).
1. Place ", MyMods - Interface.ba2" at the end of the line beginning with "SResourceArchiveMemoryCacheList=" as well as at the end of the line beginning with "sResourceStartUpArchiveList=" (ignore quotation marks).
1. Place ", MyMods - Misc.ba2" at the end of the line beginning with "SResourceArchiveList=" as well as at the end of the line beginning with "SResourceArchiveMemoryCacheList=" (ignore quotation marks).
1. Place ", MyMods - WwiseSounds.ba2" at the end of the line beginning with "sResourceStartUpArchiveList=" (ignore quotation marks).
1. Finally, place ", MyMods - Main.ba2" at the end of the line beginning with "SResourceArchiveList=" (ignore quotation marks).

### Ensure Loose Files Don't Load

Now we need to prevent the loose files from loading:

1. Open StarfieldCustom.ini
1. Remove these lines from the `[Archive]` section:
```
sResourceDataDirsFinal=
bInvalidateOlderFiles=1
```

By doing this, we don't need to go and manually delete/disable our loose files from each mod that was packed here; they will simply not be loaded.

## Repacking Vanilla Archives

- Only helpful for very large texture overhauls such as [Starfield HD Overhaul](https://www.nexusmods.com/starfield/mods/5124) to save space and possibly load faster due to fewer (large) BA2's
- Loose files shouldn't be repacked into vanilla archives as more custom files in the base archives will create complexity especially if you want to remove a mod

Repacking can be done as follows:

1. Create a folder called `working`, and inside, create a folder called `vanilla unpacked` and another called `hd unpacked`
1. Download all BA2's for the given texture pack
1. Load up [BSArchPro64](#bsarchpro64) and drag each BA2 from the pack on to it
1. Once all BA2's are loaded, extract to `working/hd unpacked`; this may take awhile but after it is complete, you should see a `textures` folder
1. Clear the files in BSArchPro64, then navigate to `Stock Game Folder/Data`
1. Select all texture files for the base game named like `Starfield - Textures01.ba2` and drag on to BSArchPro64
1. Then, drag `Starfield - TexturesPatch.ba2` - this one appears to be a patch (as its name implies) so it will ask to overwrite files; say yes
1. Once all BA2's are loaded, extract to `working/vanilla unpacked`; once complete, you should see a `textures` folder
1. IMPORTANT - Drag `working/hd unpacked/textures` on to `working/vanilla unpacked/textures`, NOT the other way around
1. This will take some time and should ask you to overwrite textures, say yes to all

We now have all of our textures in one place with any redundant vanilla ones replaced, so now we can pack it back up.

1. Clear BSArchPro64, and drag `working/vanilla unpacked/textures` on to it
1. Click `Ctrl + A` to select all, then click Pack
1. In the menu, select `Starfield DDS` since these are textures, and enable Multithreaded Packing and Shared Data
1. Finally, set the Archive File Name to match the original - `Starfield - Textures.ba2`
1. Since each BA2 can only be 4095MB or ~4GB, it will create many archives with a naming scheme like the originals
1. Delete the original texture archives from `Stock Game Folder/Data` like `Starfield - Textures01.ba2`, along with `Starfield - TexturesPatch.ba2`
1. Check the `sResourceIndexFileList` in `Documents/My Games/Starfield/StarfieldCustom.ini` and ensure that all numbered texture archives are there; if not, add any to the end of the line separated by commas

That should be it.
