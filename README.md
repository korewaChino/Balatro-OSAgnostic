# Balatro-OSAgnostic

This simple Lovely mod simply bypasses the OS check in Balatro, allowing Steamworks API integration in the game while running natively on Linux

## Installation

1. Install Lovely Injector and LOVE (For now, you'll need to build the latest version of LOVE from source from a [PR](https://github.com/ethangreen-dev/lovely-injector/pull/66)), copy `liblovely.so` into the same directory as `Balatro.exe`

2. Download [luasteam](https://github.com/uspgamedev/luasteam) and the [Steamworks SDK](https://partner.steamgames.com/downloads/steamworks_sdk.zip)

3. Copy `linux64_luasteam.so` into `luasteam.so`, and `sdk/redistributable_bin/linux64/libsteam_api.so` from the Steamworks SDK into the same directory as `Balatro.exe`

4. Clone this repository into the Lovely Injector mods directory

    ```bash
    cd ~/.config/love/Mods
    git clone https://github.com/korewaChino/Balatro-OSAgnostic.git
    ```

5. Run Balatro with Lovely Injector, make sure to also set `LD_LIBRARY_PATH` to the directory containing `libsteam_api.so` and `luasteam.so` (The game directory). In this example we'll just `cd` to the game directory and run the game

    ```bash
    cd /path/to/Balatro
    LD_LIBRARY_PATH=. LD_PRELOAD=liblovely.so love Balatro.exe
    ```

6. Enjoy Balatro natively on Linux! Now with achievements.

## Notes

Cloud saves will probably not work, as they rely on the Steam app manifest to determine the save directory. You can manually symlink the save directory to the Steam cloud save directory if you want to use cloud saves.

Steamodded should also handle the OS-agnostic changes out of the box if need be (as of <https://github.com/Steamopollys/Steamodded/commit/ec7c5c9337bc9cded055e721ce33351c1977fe1b>), so you may skip installing this mod and follow the rest of the instructions on how to load
the Steam API libraries.

```bash
ln -sf ~/.steam/steam/steamapps/compatdata/2379780/pfx/drive_c/users/steamuser/AppData/Roaming/Balatro ~/.local/share/love/Balatro
```

For Lovely Injector mods, the directory is different (for now), so you'll need to symlink the mods directory as well

```bash
ln -sf ~/.steam/steam/steamapps/compatdata/2379780/pfx/drive_c/users/steamuser/AppData/Roaming/Balatro ~/.config/love/Mods
```
