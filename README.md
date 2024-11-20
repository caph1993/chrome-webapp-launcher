# chrome-webapp-launcher

This script creates and launches desktop files in **linux** that do the following when launched:
 
 - if the app is running, focus the existing window
 - otherwise, open a new browser instance in "app mode".

There used to be a quickwebapps application for this, but it stopped supporting chrome in october 2024.
For firefox, there's the firefoxpwa extension, but for chrome, there's no such thing, and google docs do not work in offline mode in firefoxwpa.
This motivated the creation of this script.

## Dependencies

Install `wmctrl`.

For GUI mode, it also needs `xdg-open`, but this should always be present by default in all systems.

## Usage

Download it, make it executable and run it:

```sh
curl https://raw.githubusercontent.com/caph1993/chrome-webapp-launcher/refs/heads/main/chrome-webapp-launcher > ./chrome-webapp-launcher
chmod +x ./chrome-webapp-launcher
./chrome-webapp-launcher --gui
```

## How does it work?

If you run `wmctrl -lx`, you'll get the list of open windows and their window-manager class (WM_CLASS) that can be used as an identifier for each app.
The script simply focuses the corresponding window when it's found.

More info on how it works:
   - https://stackoverflow.com/questions/19229235/run-standalone-web-app-in-google-chrome-without-borders-or-toolbars
   - https://askubuntu.com/questions/367396/what-does-the-startupwmclass-field-of-a-desktop-file-represent

## Why isn't it simpler?

Chrome has an issue with handling and setting WM_CLASS in apps mode.

   - https://superuser.com/questions/1457060/how-can-you-start-two-chrome-windows-with-different-wm-class-attributes
   - https://issues.chromium.org/issues/40172351
