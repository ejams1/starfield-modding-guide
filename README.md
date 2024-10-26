# starfield-modding-guide
Tips/guidance for modding Starfield; mostly a reference for myself. Make sure you check footnotes for additional info, and I welcome any suggestions or corrections as issues or PRs!

See my current load order and mod list [on Load Order Library here](https://loadorderlibrary.com/lists/a-better-starfield#modlist.txt).

> [!IMPORTANT]
> I have only used Mod Organizer 2 for Starfield modding and cannot provide much insight into Vortex setup or support; if you have more experience with it, feel free to open a PR and id be glad to include it

> [!IMPORTANT]
> I have not heavily tested this mod list or load order and it likely needs to be tweaked so please only use it as a reference.

## Setup

1. Download [latest MO2](#mod-organizer-2) and configure a portable instance
1. Copy the entire Starfield directory from Steam into the MO2 directory and rename to `Stock Game Folder`; rationale for using Stock Game Folder over Root Builder is that while it uses more storage, it will maintain the existing version of the game even if an update is released so it won't break
1. In the settings, change Paths to point to `Stock Game Folder`
1. In the MO2 directory, create a folder called `tools` and download [all tools](#tools) into here then add each one as an executable in MO2
1. Install the latest [Starfield Script Extender (SFSE)](https://www.nexusmods.com/starfield/mods/106) directly into `Stock Game Folder`
1. Download `StarfieldPrefs.ini` and `StarfieldCustom.ini` and put in `My Games/Starfield` (and in `mo2/profiles/<profile>` for good measure)
1. Download the four "better" default presets, and put in `Stock Game Folder`
1. Replace the Nvidia DLSS plugin inside `Stock Game Folder` with the latest from [TechPowerup](https://www.techpowerup.com/download/nvidia-dlss-dll/)

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

## Packing/Unpacking Files

- There are many tools that can pack/unpack, but the two I found most useful in terms of Starfield support, speed, and function are [BSArchPro64](#bsarchpro64) and [BA2Upgrader](#ba2upgrader); alternatives include `Archive2` (included with the Creation Kit) and [Cathedral Asset Optimizer](https://www.nexusmods.com/skyrimspecialedition/mods/23316)
- The max size of a BA2 should be `4095MB`
- Before packing loose files, ensure that your load order is configured such that all conflicts are resolved how you would like
- Pack loose textures using `Starfield - DDS` format, then use `BA2Upgrader` and upgrade to BA2 v3 using LZ4 compression for best performance
- Pack any other loose assets (interface, meshes, sound, etc) using `Starfield - General` format; BA2 v3 is only for textures, so no further action needed
- Texture archives should be named `<plugin> - Textures.ba2` and everything else should be in `<plugin> - Main.ba2`
- After packing is complete, create a dummy light `.esm` with the same name as `<plugin` above; an example packed directory should look like:
  ```
  overrides - Main.ba2
  overrides - Textures.ba2
  overrides.esm
  ```
- After files are packed into archives, the mods they come from should be disabled to prevent still loading the loose files
  - If the mod ONLY contains loose files like `textures`, you can disable the mod in your load order
  - If the mod _also_ contains an `.esm`, delete the loose files so that only the `.esm` remains; this ensures the `.esm` still loads but prevents the redundant loose files from loading
- To ensure a packed BA2 is loaded, add it to the `sResourceIndexFileList` in `Documents/My Games/Starfield/StarfieldCustom.ini`
  - There are other resource file lists in the `[Archive]` section in the ini, and depending on the overrides, you may need to add your packed BA2 to other sections - needs further investigation
  - I don't know why, but the Starfield ini files in my MO2 directory were not being loaded, and it was instead loading from my Documents folder still; his may be a config error so needs double-checking. If in doubt, place your ini's in both
- To find _all_ loose files, run `Explorer++` and look at the virtual game directory, then in the `Data` folder - all loose asset folders should be visible here

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
