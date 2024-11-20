# chrome-webapp-launcher

This script creates and launches desktop files in **linux** that do the following when launched:
 
 - if the app is running, focus the existing window
 - otherwise, open a new browser instance in "app mode".

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
