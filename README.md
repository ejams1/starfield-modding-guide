# starfield-modding-guide
Tips/guidance for modding Starfield; mostly a reference for myself.

## Tools

- **xEdit**
  - Create patches, identify conflicts, etc.
  - Latest dev version for best Starfield support; `4.1.5k` at the time of writing
  - Download from xEdit discord from #xedit-builds
- **BSArchPro64**
  - Pack loose files into BA2 or unpack BA2
  - Comes with xEdit
- **Mod Organizer 2**
  - Latest dev version for best Starfield support; `2.5.3dev2` at the time of writing
  - Download from MO2 discord from #dev-builds
- **BA2Upgrader**
  - Download from [Nexus Mods](https://www.nexusmods.com/starfield/mods/1192)
- **Starfield NIF migration tool**
  - Download from [Nexus Mods](https://www.nexusmods.com/starfield/mods/9234)
- **Bethini Pie**
  - Download from [Nexus Mods](https://www.nexusmods.com/site/mods/631)

## Tips

### Packing Loose Files

- Pack loose textures using `Starfield - DDS` format, then use `BA2Upgrader` and upgrade to BA2 v3 using LZ4 compression for best performance
- Pack any other loose assets using `Starfield - General` format; BA2 v3 is only for textures, so no further action needed
- Texture archives should be named `<plugin> - Textures.ba2` and everything else should be in `<plugin> - Main.ba2`
- After packing is complete, create a dummy light `.esm` with the same name as `<plugin` above; an example packed directory should look like:
  ```
  overrides - Main.ba2
  overrides - Textures.ba2
  overrides.esm
  ```
- After files are packed into archives, the mods they come from should be disabled to prevent still loading the loose files
- To ensure a packed BA2 is loaded, add it to the `sResourceIndexFileList` in `Documents/My Games/Starfield/StarfieldCustom.ini`
> [!NOTE]
> There are other resource file lists in the `[Archive]` section in the ini, and depending on the overrides, you may need to add your packed BA2 to other sections. Needs further investigation.

> [!NOTE]
> I don't know why, but the Starfield ini files in my MO2 directory were not being loaded. This may be a config error so double-check
- To find _all_ loose files, run `Explorer++` and look at the virtual game directory, then in the `Data` folder - all loose asset folders should be visible here