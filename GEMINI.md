# User Management Scripting

## Project Overview
This directory is dedicated to shell scripting projects focused on **user management** in a Unix/Linux environment. It is part of a larger collection of scripting tutorials and exercises, which covers tools like `awk`, `sed`, and `sort`.

### Current Project: `umanag`
`umanag` is a specialized development project aimed at basic UNIX users. It provides a set of tools to simplify common user management tasks.
- **Packaging Goal:** The project is designed to be distributed as a `.deb` package (for Debian/Ubuntu) or a `.tar.gz` archive.

## Building and Running
As this project consists of shell scripts, there is no traditional "build" step, but there is a packaging process.

### Prerequisites
- A Unix-like environment (Linux, macOS, or WSL).
- Standard shell (e.g., `bash`, `sh`, or `zsh`).
- Root or sudo privileges for most user management tasks.

### Running Scripts
Ensure scripts have execution permissions:
```bash
chmod +x <script_name>.sh
./<script_name>.sh
```

## Development Conventions
- **Shebang:** Always include `#!/bin/bash` or `#!/bin/sh` at the top of scripts.
- **Error Handling:** Use `set -e` or check exit codes to ensure scripts fail gracefully.
- **Root Checks:** For scripts modifying system users, include a check for root privileges:
  ```bash
  if [[ $EUID -ne 0 ]]; then
     echo "This script must be run as root"
     exit 1
  fi
  ```
- **Documentation:** Use comments to explain complex logic or required input parameters.
- **Testing:** Test scripts in a safe, non-production environment (like a virtual machine or container) before running them on a live system.
