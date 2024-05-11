# GlazeWM_config
GlazeWM is a tiling window manager for Windows inspired by i3 and Polybar.

All keybindings are similar to vim (h, j , k , l), while $mod key is Alt

Inspired by design of : https://gist.github.com/alexanderi96

scroll down for config file
<hr>
 

https://github.com/omprakashpaudel125/glazewm_config/assets/73826330/ce6331de-8851-4355-a682-1a1d57d0f21e

<hr>

# config.yaml
(Usage of Alt+F Alt+X are swapped 😊)
```plaintextgaps:
  inner_gap: 0
  outer_gap: 0

general:
  # Whether to show floating windows as always on bottom.
  show_floating_on_bottom: true

bar:
  height: "30px"
  position: "bottom"
  opacity: 1.0
  background: "#101010c4"
  foreground: "#ffffff"
  font_family: "Cascadia Code"
  font_size: "13px"
  padding: "4px 6px"
  offset_x: "10px"
  offset_y: "10px"
  border_radius: "0"
  components_left:
    - type: "workspaces"
      focused_workspace_background: "#00b3b3"
      displayed_workspace_background: "#42403e33"
      default_workspace_background:
        "transparent"
        #  components_center:
        #- type: "window title"
  components_right:
    - type: "tiling direction"
      label_horizontal: "⮂"
      label_vertical: "⮁"
      background: "#8192B333"
      margin: "0 4px"
      padding: "0 8px"
    - type: "binding mode"
      background: "#8192B333"
      margin: "0 4px 0 0"
      padding: "0 8px"
    - type: "clock"
      time_formatting: "hh:mm:ss tt  ddd d MMM yyyy"
      margin: "0 10px 0 10px"
    - type: "battery"
      label_draining: "🔋{battery_level}%"
      label_power_saver: "🔋{battery_level}% (power saver)"
      label_charging: "⚡{battery_level}% (charging)"
      margin: "0 2px 0 2px"
    - type: "volume"
      label_low: "🔊{volume_level}%"
      label_medium: "🔊{volume_level}%"
      label_high: "🔊{volume_level}%"
      label_mute: "🔊{volume_level}%"
      margin: "0 2px 0 2px"
    - type: "memory"
      label: "RAM:{percent_usage}%"
      margin: "0 2px 0 2px"
      # How often this counter is refreshed.
      refresh_interval_ms: 1000
    - type: "network"
      label_no_internet: "NC"
      label_ethernet: "Eth"
      label_wifi_name: "{wifi_name}%"
      label_wifi_strength_0: "WiFi: 0%"
      label_wifi_strength_25: "WiFi: 25%"
workspaces:
  - name: "0"
    display_name: "0 "
  - name: "1"
    display_name: "1  "
  - name: "2"
    display_name: "2  "
  - name: "3"
    display_name: "3  "
  - name: "4"
    display_name: "4  "
  - name: "5"
    display_name: "5  "
  - name: "6"
    display_name: "6  "
  - name: "7"
    display_name: "7  "
  - name: "8"
    display_name: "8  "
  - name: "9"
    display_name: "9  "

window_rules:
  # Task Manager requires admin privileges to manage and should be ignored unless running
  # the WM as admin.
  - command: "ignore"
    match_process_name: "Taskmgr"

  - command: "set maximized"
    match_process_name: "acsW"

  # Launches system dialogs as floating by default (eg. File Explorer save/open dialog).
  - command: "set floating"
    match_class_name: "(#32770|SunAwtDialog)"

  - command: "set floating"
    match_process_name: "(steam|Content Manager Safe)"

  # Some applications (eg. Steam) have borders that extend past the normal border size.
  - command: "resize borders 0px -7px -7px -7px"
    match_process_name: "steam"

  # Custom app behaviour
  # when I open an application it should go to specified workspace!!
  #- command: "move to workspace 3"
  #  match_process_name: "firefox"

binding_modes:
  - name: "resize"
    keybindings:
      # Resize focused window by a percentage or pixel amount.
      - command: "resize width -2%"
        bindings: ["H", "Left"]
      - command: "resize width +2%"
        bindings: ["L", "Right"]
      - command: "resize height +2%"
        bindings: ["K", "Up"]
      - command: "resize height -2%"
        bindings: ["J", "Down"]
      # Press enter/escape to return to default keybindings.
      - command: "binding mode none"
        bindings: ["Escape", "Enter"]

keybindings:
  # Flow Launcher which is equivalent to Rofi in linux!! LOL
  # Download Flow Launcher https://www.flowlauncher.com/
  # Add path for your application Launcher here
  - command: "exec 'C:\\Users\\opaudel\\AppData\\Roaming\\Microsoft\\Windows\\Start Menu\\Programs\\Flow Launcher\\Flow Launcher.lnk'"
    bindings: ["Alt+D"]
  # Shift focus in a given direction.
  - command: "focus left"
    bindings: ["Alt+H", "Alt+Left"]
  - command: "focus right"
    bindings: ["Alt+L", "Alt+Right"]
  - command: "focus up"
    bindings: ["Alt+K", "Alt+Up"]
  - command: "focus down"
    bindings: ["Alt+J", "Alt+Down"]

  # Move focused window in a given direction.
  - command: "move left"
    bindings: ["Alt+Shift+H", "Alt+Shift+Left"]
  - command: "move right"
    bindings: ["Alt+Shift+L", "Alt+Shift+Right"]
  - command: "move up"
    bindings: ["Alt+Shift+K", "Alt+Shift+Up"]
  - command: "move down"
    bindings: ["Alt+Shift+J", "Alt+Shift+Down"]

  # Resize focused window by a percentage or pixel amount.
  - command: "resize width -2%"
    binding: "Alt+U"
  - command: "resize width +2%"
    binding: "Alt+P"
  - command: "resize height +2%"
    binding: "Alt+O"
  - command: "resize height -2%"
    binding: "Alt+I"

  # As an alternative to the resize keybindings above, resize mode enables resizing via
  # HJKL or arrow keys. The binding mode is defined above with the name "resize".
  - command: "binding mode resize"
    binding: "Alt+R"

  # Change tiling direction. This determines where new tiling windows will be inserted.
  - command: "tiling direction toggle"
    binding: "Alt+V"

  # Change focus between floating / tiling windows.
  # Disabled because of conflicts with PowerToys Run
  #- command: "toggle focus mode"
  #  binding: "Alt+Space"

  # Change the focused window to be floating / tiling.
  - command: "toggle floating"
    binding: "Alt+Shift+Space"

  # Change the focused window to be maximized / unmaximized.
  - command: "toggle maximized"
    binding: "Alt+F"

  # Minimize focused window.
  - command: "set minimized"
    binding: "Alt+M"

  # Close focused window.
  - command: "close"
    binding: "Alt+Shift+Q"

  # Kill GlazeWM process safely.
  - command: "exit wm"
    binding: "Alt+Shift+E"

  # Re-evaluate configuration file.
  - command: "reload config"
    binding: "Alt+Shift+R"

  # Launch CMD terminal (alternatively `exec wt` or `exec %ProgramFiles%/Git/git-bash.exe`
  # to start Windows Terminal and Git Bash respectively.
  - command: "exec wt"
    binding: "Alt+Enter"

  # Focus the workspace that last had focus.
  - command: "focus workspace recent"
    binding: "Alt+Y"

  # Focus the next/previous workspace defined in `workspaces` config.
  - command: "focus workspace next"
    binding: "Alt+T"
  - command: "focus workspace prev"
    binding: "Alt+Shift+T"

  # Change focus to a workspace defined in `workspaces` config.
  - command: "focus workspace 0"
    binding: "Alt+0"
  - command: "focus workspace 1"
    binding: "Alt+1"
  - command: "focus workspace 2"
    binding: "Alt+2"
  - command: "focus workspace 3"
    binding: "Alt+3"
  - command: "focus workspace 4"
    binding: "Alt+4"
  - command: "focus workspace 5"
    binding: "Alt+5"
  - command: "focus workspace 6"
    binding: "Alt+6"
  - command: "focus workspace 7"
    binding: "Alt+7"
  - command: "focus workspace 8"
    binding: "Alt+8"
  - command: "focus workspace 9"
    binding: "Alt+9"

  # Move focused workspace to a monitor in a given direction.
  - command: "move workspace left"
    binding: "Alt+A"
  - command: "move workspace right"
    binding: "Alt+X"
  - command: "move workspace up"
    binding: "Alt+D"
  - command: "move workspace down"
    binding: "Alt+S"

  # Move focused window to a workspace defined in `workspaces` config.

  - commands: ["move to workspace 0", "focus workspace 0"]
    binding: "Alt+Shift+0"
  - commands: ["move to workspace 1", "focus workspace 1"]
    binding: "Alt+Shift+1"
  - commands: ["move to workspace 2", "focus workspace 2"]
    binding: "Alt+Shift+2"
  - commands: ["move to workspace 3", "focus workspace 3"]
    binding: "Alt+Shift+3"
  - commands: ["move to workspace 4", "focus workspace 4"]
    binding: "Alt+Shift+4"
  - commands: ["move to workspace 5", "focus workspace 5"]
    binding: "Alt+Shift+5"
  - commands: ["move to workspace 6", "focus workspace 6"]
    binding: "Alt+Shift+6"
  - commands: ["move to workspace 7", "focus workspace 7"]
    binding: "Alt+Shift+7"
  - commands: ["move to workspace 8", "focus workspace 8"]
    binding: "Alt+Shift+8"
  - commands: ["move to workspace 9", "focus workspace 9"]
    bindings: ["Alt+Shift+9"]
```

