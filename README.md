# AoE4 Overlay
 
* **[DOWNLOAD HERE](https://github.com/FluffyMaguro/AoE4_Overlay/releases/download/1.4.0/AoE4_Overlay.zip)** (Windows)
* Or run the script with Python 3.6+ (Windows/Mac/Linux)

![Screenshot](https://i.imgur.com/eN2zJ3c.jpg)

# What does the app do?
* Shows information about players you are in match with.
* Provides additional player statistics in-app.
* Shows an overlay widget for build orders (BO) in two formats:
  * Simple TXT format.
  * Interactive (selecting the BO step) with resources distribution and game pictures.
* Supports a highly customizable streaming overlay (with CSS/JS).

API calls are done through [AoEIV.net](https://aoeiv.net/) and [AoE4World.com](https://aoe4world.com/). For questions and issues visit my [discord server](https://discord.gg/FtGdhqD).


# How to use

* Download and extract the archive.
* Run `AoE4_Overlay.exe`.
* Find your profile by entering your profile ID, Steam ID or player name.
* Set up the hotkey for showing/hiding overlay.
  * Overlay will be automatically shown when a new game starts (or app starts).
* Build orders:
  * Two build orders types are available: *Simple TXT* and/or *Interactive (selecting the BO step) with resources distribution and game pictures*.
  * Add or remove build orders with **Add/Remove build order** (write the content on the left panel, and the title on the top of the right panel).
    * Write anything for the *Simple TXT format*.
    * For the *Interactive format*, you need to have a JSON format compatible with the [RTS_Overlay](https://github.com/CraftySalamander/RTS_Overlay) from CraftySalamander (see examples [here](https://github.com/CraftySalamander/RTS_Overlay/tree/master/build_orders/aoe4)).
    * Many build orders can be downloaded from https://age4builder.com (currently only for *Simple TXT format*, but soon available for both formats).
  * Change their order using with **Move build order up/down**.
  * Set up hotkeys (with **Hotkey for/to...**) for showing/hiding overlay, cycling between build orders and selecting the previous/next step of a build order (only available for the *Interactive build orders with images*).
    * Use the corresponding hotkeys to show/hide/cycle build orders and steps.
  * Change the overlay font size with **Overlay font size**.
  * Change the height of the build order images (irrelevant for the *Simple TXT* version) with **Overlay images height**.
  * Change the position of the build order overlay with **Change BO overlay position**. Once fixed, the upper right corner will never move, but the size of the overlay will be automatically adapted to its content.

*To update the app delete the app folder and extract the new archive elsewhere.*


# Authors
* FluffyMaguro
* CraftySalamander (build order overlay)


# Screenshots

Build order widget:

![Screenshot](https://i.imgur.com/ET6KY5W.png)

Additional civilization stats (currently only for 1v1):

Wintime is the median game length of won games with given civilization (indicates in what game phase the player is the strongest).

![Screenshot](https://i.imgur.com/cpeq8ob.png)

Settings:

![Screenshot](https://i.imgur.com/hhH8R72.png)

Game history:

![Screenshot](https://i.imgur.com/L1V1wp2.png)

Rating history:

![Screenshot](https://i.imgur.com/QqojOJI.png)

Last 24 hours:

![Screenshot](https://i.imgur.com/8ODqTrw.png)

Various stats:

![Screenshot](https://i.imgur.com/aGXRnT2.png)

Build order tab:

![Screenshot](https://i.imgur.com/xPKpaEz.png)

Built-in randomizer:

![Screenshot](https://i.imgur.com/tV4dMfi.png)

# Streaming
To use the custom streaming overlay simply drag the `overlay.html` file to OBS or other streaming software. The file is located in `src/html` directory in the app folder. Move and rescale as necessary once some game information is shown.

![Screenshot](https://i.imgur.com/BK9AC6h.png)

If drag & drop doesn't work, add new source to your scene manually. The source type will be `Browser` and point to a local file `overlay.html`.

Overlay active:

![Screenshot](https://i.imgur.com/gNbxJBY.png)

* Streaming overlay supports team games as well
* The streaming overlay can be fully customized with CSS and JS, see the next section.
* The override tab can be used to change the information on the overlay. This might be useful when casting from replays or changing a player's barcode to their actual name.

![Screenshot](https://i.imgur.com/f1OGmyz.png)

Or change values to something completely different

![Screenshot](https://i.imgur.com/02YsXdI.png)

# Customization

1. **Overlay position and font size** can be changed in the app.

2. **Build order** (BO) font, images size, position and hotkeys can be changed in the app. Other attributes can also be customized in `config.json` (to find the file click `File/config & logs` in the app). You have to close the app before making changes to the config file. What can be changed:

    `"bo_show_title": true ` : true to show the BO title, false otherwise

    `"bo_title_color": [230, 159, 0] ` : color for the BO title

    `"bo_overlay_hotkey_show": "" ` : hotkey to show/hide the BO

    `"bo_overlay_hotkey_cycle": "" ` : hotkey to cycle between the different BO available

    `"bo_overlay_hotkey_previous_step": "" ` : hotkey to go to the previous step of the BO

    `"bo_overlay_hotkey_next_step": "" ` : hotkey to go to the next step of the BO

    `"bo_font_size": 12 ` : font size

    `"bo_text_color": [255, 255, 255] ` : text RGB color

    `"bo_color_background": [30, 30, 30] ` : background RGB color

    `"bo_font_police": 'Arial' ` : police font

    `"bo_opacity": 0.75 ` : opacity of the window

    `"bo_upper_right_position": [1870, 70] ` : position for the upper right corner

    `"bo_image_height": 30 ` : height of the images

    `"bo_border_size": 15 ` : size of the borders

    `"bo_vertical_spacing": 10 ` : vertical space between the BO lines

    The images used in the build order overlay can also be defined in the same file (path relative to `src/img/build_order`).



3. **Team colors** can be changed in the `config.json`. Colors are stored as a list of RGBA colors for team 1, 2, and so on.

    ```json
    "team_colors": [
        [74, 255, 2, 0.35],
        [3, 179, 255, 0.35],
        [255, 0, 0, 0.35]
      ]
    ```
    
4. **Civilization stats color** can be changed in `config.json`.
    ```json
    "civ_stats_color": "#BC8AEA",
    ```

5. **Streaming overlay** customization can be done via `custom.css` and `custom.js` in the `html` folder in app directory. These files will not be overridden with an app update. Look at `main.css` to see what you can change. In `custom.js` you can define this function that runs after each update.

    ```javascript
    function custom_func(data) {
        console.log("These are all the player data:", data);
    }
    ```

# Releases & Changelog

The Releases can be downloaded [here](https://github.com/FluffyMaguro/AoE4_Overlay/releases).

The Changelog is available [here](https://github.com/CraftySalamander/AoE4_Overlay/blob/main/Changelog.md).
