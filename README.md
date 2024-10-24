# starfield-modding-guide
Tips/guidance for modding Starfield; mostly a reference for myself. See my current load order and mod list [on Load Order Library here](https://loadorderlibrary.com/lists/a-better-starfield#modlist.txt).

Make sure you check footnotes for additional info, and I welcome any suggestions or corrections as issues or PRs!

## Setup

1. Download [latest MO2](#mod-organizer-2) and configure a portable instance
1. Copy the entire Starfield directory from Steam into the MO2 directory and rename to `Stock Game Folder`[^1]
1. In the settings, change Paths to point to `Stock Game Folder`
1. In the MO2 directory, create a folder called `tools` and download [all tools](#tools) into here then add each one as an executable in MO2
1. Install the latest [Starfield Script Extender (SFSE)](https://www.nexusmods.com/starfield/mods/106) directly into `Stock Game Folder`
1. Download `StarfieldPrefs.ini` and `StarfieldCustom.ini` and put in `My Games/Starfield` (and in `mo2/profiles/<profile>` for good measure)
1. Download the four "better" default presets, and put in `Stock Game Folder`
1. Replace the Nvidia DLSS plugin inside `Stock Game Folder` with the latest from [TechPowerup](https://www.techpowerup.com/download/nvidia-dlss-dll/)

[^1]: Rationale for using Stock Game Folder rather than Root Builder is that while it uses more storage space, it will maintain the existing version of the game even if an update is released making it much safer

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

### Miscellaneous

- Using `SKK Fast Start` can cause issues with audio loading; supposedly it goes away after awhile or possible reload but starting vanilla is safest
- Ensure that `.asi` mods like `Disk Cache Enabler` sit at the root of their mod folder as they are expected to be at the root of `Data/`; example: `Disk Cache Enabler/diskCacheEnabler.asi`
- The armors `Banshee`, `Exile`, `HyperGuardian`, `Mark M` and `Pathfinder` all contain outdated meshes, and require updating (or [see Luxor's patches](https://www.nexusmods.com/starfield/mods/9468))
- [Luma](https://www.nexusmods.com/starfield/mods/4821) seems to cause black crushing on my OLED displays but likely needs further tweaking; [NaturalLUTs](https://www.nexusmods.com/starfield/mods/1119) plus the default HDR (or Nvidia RTX HDR) seem to be good enough
- [Console Command Runner (CCR)](https://www.nexusmods.com/starfield/mods/7318) mods are no longer relevant as they can be easily recreated natively in the Creation Kit as an `.esm`; for example, I recreated [Instant Scan](https://www.nexusmods.com/starfield/mods/759) this way in about 5 minutes
- [The Dualsense icons mod](https://www.nexusmods.com/starfield/mods/215) apparently needs an update as there are some missing icons in the Creations menu
- Speaking of which, files from the `interface/` folder such as `.swf` files can be edited with [this tool](#jpexs-decompiler)

### Packing/Unpacking Files

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
  - If the mod _also_ contains an `.esm`, then reinstall the mod and add `- Packed` to it which will create a copy of the mod; in this copy, delete the loose files so that only the `.esm` remains, and enable this mod and disable the original. This ensures the `.esm` still loads but prevents the loose files from loading even after we have already packed them
  - The second strategy can be used if the mod contains loose files too as it makes it easier to update the mods
- To ensure a packed BA2 is loaded, add it to the `sResourceIndexFileList` in `Documents/My Games/Starfield/StarfieldCustom.ini`[^2][^3]
- To find _all_ loose files, run `Explorer++` and look at the virtual game directory, then in the `Data` folder - all loose asset folders should be visible here

[^2]: There are other resource file lists in the `[Archive]` section in the ini, and depending on the overrides, you may need to add your packed BA2 to other sections. Needs further investigation.
[^3]: I don't know why, but the Starfield ini files in my MO2 directory were not being loaded, and it was instead loading from my Documents folder still. This may be a config error so needs double-checking. If in doubt, place your ini's in both.

### Repacking Vanilla Archives

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
