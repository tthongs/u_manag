# u_manag 🛠️

`u_manag` is a lightweight, GUI-based User Management tool for Unix/Linux
systems. It provides a simple interface built with `Zenity` to handle common
administrative tasks like creating, deleting, and renaming users without needing
to remember complex CLI flags.

## Project Overview

- **Purpose:** Provide a user-friendly graphical interface for standard Linux
  user management commands (`useradd`, `userdel`, `usermod`).
- **Main Technologies:**
  - **Bash:** The primary scripting language.
  - **Zenity:** Used for generating GTK+ dialog boxes from the command line.
  - **Polkit (pkexec):** Handles root escalation for secure graphical password
    prompts.
- **Architecture:** A single-file shell script (`u_manag.sh`) that checks for
  root privileges and relaunches itself with `pkexec` if necessary. It uses a
  while-loop driven main menu to navigate between user management functions.

## Building and Running

### Prerequisites

Ensure the following are installed:
- `bash`
- `zenity`
- `polkit`
- `shadow` (for `useradd`, `userdel`, `usermod`)

### Running Locally

To run the script directly from the source directory:
```bash
./u_manag.sh
```

### Installation

#### Arch Linux (via PKGBUILD)
Build and install using `makepkg`:
```bash
makepkg -si
```
This installs the script to `/usr/bin/umanag` and provides a desktop entry.

#### Manual Installation
1. Make the script executable:
   ```bash
   chmod +x u_manag.sh
   ```
2. Move it to your PATH:
   ```bash
   sudo cp u_manag.sh /usr/bin/umanag
   ```
3. (Optional) Install the desktop entry:
   ```bash
   sudo cp umanag.desktop /usr/share/applications/
   ```

## Key Files

- `u_manag.sh`: The core logic and GUI implementation.
- `PKGBUILD`: Arch Linux package build configuration.
- `umanag.desktop`: Integration for application launchers and menus.
- `README.md`: General project documentation and introduction.

## Development Conventions

- **GUI Consistency:** All user interactions must be handled via `Zenity`
  dialogs to maintain a pure GUI experience.
- **Privilege Management:** The script must handle its own escalation to root
  via `pkexec` to ensure it can be run by a standard user from a GUI
  environment.
- **Safety:** Always prompt for confirmation before destructive actions
  (e.g., user deletion).
- **Validation:** Check for the existence of users before attempting
  modifications or deletions.
