# bash-gitm

A lightweight git wrapper that remaps commit timestamps to a specified time range.

## Overview

`gitm` intercepts git commands and adjusts the author and committer timestamps. This is useful when you want to normalize commit times to specific hours, such as consolidating late-night commits into regular working hours.

## Installation

### Using Nix

```bash
nix profile install github:conao3/bash-gitm
```

### From Source

Clone the repository and ensure `git` and `python3` are available in your PATH.

## Usage

```bash
gitm [options] -- <git-command> [git-options]
```

### Options

| Option | Description |
|--------|-------------|
| `-h, --help` | Display help message |
| `-s, --split <hour>` | The hour that divides the day (required) |
| `-t, --to <range>` | Target hour range in `start-end` format (required) |

### How It Works

The tool maps a 24-hour period starting from the split hour onto the target range. Commits made at any time will have their timestamps adjusted to fall within the specified target hours.

### Examples

Remap commits to appear between 9 PM and 6 AM (21:00-30:00, where 30 represents 6 AM the next day):

```bash
gitm -s 9 -t 21-30 -- commit -m "Update documentation"
```

This takes the current time, calculates where it falls in the 24-hour period starting at 9 AM, and maps it proportionally to the 21:00-06:00 range.

## Requirements

- Bash
- Python 3
- Git

## License

See the repository for license information.
