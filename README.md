# Toucan ZMK configuration

This repository is ready to use with [Nick Coutsos' ZMK Keymap
Editor](https://nickcoutsos.github.io/keymap-editor/) and GitHub Actions. It is
based on the official [beekeeb Toucan firmware
repository](https://github.com/beekeeb/zmk-keyboard-toucan).

The [beekeeb Toucan Keyboard](https://beekeeb.com/toucan-keyboard/) is a
wireless split 42-key column-stagger keyboard with a display and trackpad.

## Set up the GitHub repository

1. Create a GitHub repository and push this repository to its `main` branch.
   Keep the repository public unless you specifically want a private firmware
   configuration.
2. Open the repository's **Actions** tab and enable workflows if GitHub asks you
   to do so. The first build starts automatically after the files are pushed.
3. Wait for the **Build ZMK firmware** workflow to finish successfully.

Do not rename `config/toucan.keymap` or `config/toucan.json`. Their matching
names allow Keymap Editor to pair the keymap with Toucan's physical layout.

## Edit the keymap

1. Open [ZMK Keymap Editor](https://nickcoutsos.github.io/keymap-editor/).
2. Choose **GitHub**, sign in, and grant the editor access to this repository.
   Use **Add/remove repositories** if the repository does not appear.
3. Select this repository, the `main` branch, and `toucan` when prompted for a
   keymap.
4. Change the layout and choose **Save**. The editor commits
   `config/toucan.keymap`, which starts a new firmware build.
5. Wait for the build to pass, then download the firmware artifact from the
   editor's latest-build link or from the repository's **Actions** tab.

The default keymap has four layers: `BASE`, `NAV`, `SYM`, and `ADJ`. Pressing
the `NAV` and `SYM` layer keys together activates `ADJ`.

## Flash the firmware

The downloaded archive contains separate UF2 firmware files for the left and
right halves.

1. Connect one half with a data-capable USB cable.
2. Double-press its reset button. A drive whose name starts with `XIAO` should
   appear.
3. Copy the matching left or right UF2 file to that drive.
4. Repeat for the other half with its matching UF2 file.

The `settings_reset` image in the build artifact is only for clearing stored
settings while troubleshooting; it is not the normal keyboard firmware. See
beekeeb's [Toucan quick-start and flashing
guide](https://docs.beekeeb.com/toucan-keyboard/quick-start-keymap-and-firmware)
for photos and recovery instructions.

## Repository layout

- `config/toucan.keymap` — the file edited by Keymap Editor
- `config/toucan.json` — Toucan's visual 42-key layout metadata
- `build.yaml` — firmware targets for the left half, right half, and settings
  reset image
- `.github/workflows/build.yml` — GitHub Actions firmware build
- `boards/shields/` — the Toucan and display hardware definitions

## License

The code in this repo is available under the MIT license.

The included shield nice_view_gem is modified from https://github.com/M165437/nice-view-gem licensed under the MIT License.

ZMK code snippets are taken from the ZMK documentation under the MIT license.

The embedded font QuinqueFive is designed by GGBotNet, licensed under under the SIL Open Font License, Version 1.1.
