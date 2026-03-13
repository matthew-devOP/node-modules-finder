# Node Modules Finder

A desktop GUI tool that scans your filesystem for `node_modules` folders, shows how much disk space each one uses, and lets you delete them to reclaim storage. Built with Python and Tkinter.

![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![Platform](https://img.shields.io/badge/Platform-macOS%20%7C%20Linux%20%7C%20Windows-lightgrey)
![License](https://img.shields.io/badge/License-MIT-green)

## Why?

Node.js projects accumulate `node_modules` folders that can easily reach hundreds of megabytes each. Old or forgotten projects silently eat up gigabytes of disk space. This tool helps you find them all in one place, see which ones haven't been accessed recently, and clean them up safely.

## Features

- **Recursive directory scanning** — walks any directory tree to find all `node_modules` folders
- **Project detection** — displays the parent project name for each `node_modules`
- **Size calculation** — shows the actual disk usage of each folder
- **Last accessed date** — helps identify stale projects you no longer work on
- **Open in Finder** — double-click to open any `node_modules` or its parent project folder
- **Selective deletion** — delete individual folders or bulk-select multiple
- **Delete all** — one-click removal of every found `node_modules`
- **Smart scanning** — skips hidden directories, `__pycache__`, and doesn't recurse into nested `node_modules`
- **Non-blocking UI** — scanning runs in a background thread so the app stays responsive

## Installation

### Prerequisites

- **Python 3.8+**
- **Tkinter** (included with most Python installations)

### Setup

```bash
git clone https://github.com/matthew-devOP/node-modules-finder.git
cd node-modules-finder
```

No additional dependencies required.

### Run

```bash
python node_modules_finder.py
```

## Usage

1. **Select a folder** — use the Browse button or type a path (defaults to your home directory)
2. **Click Scan** — the app recursively searches for `node_modules` folders
3. **Review results** — sorted table showing project name, path, size, and last access date
4. **Clean up** — select folders and delete them, or use "Delete All" to remove everything at once

> Deletion is permanent. The app will always ask for confirmation before removing anything.

## How It Works

The app uses `os.walk()` to traverse the directory tree. When it finds a `node_modules` directory, it calculates the total size by summing all files within it, reads the last access timestamp, and extracts the parent folder name as the project identifier. It skips hidden directories and avoids descending into `node_modules` to prevent finding nested instances.

## Tech Stack

- **Python 3** with **Tkinter** / **ttk** for the GUI
- **os** / **shutil** for filesystem operations
- **threading** for non-blocking scans
- **subprocess** for Finder integration (macOS `open` command)

## Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/my-feature`)
3. Commit your changes
4. Push to the branch (`git push origin feature/my-feature`)
5. Open a Pull Request

## License

This project is licensed under the MIT License.
