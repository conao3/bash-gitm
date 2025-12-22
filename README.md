# bash-gitm

A git wrapper that modifies commit timestamps.

## Install

```bash
nix profile install github:conao3/bash-gitm
```

## Usage

```bash
gitm [<options>] -- <git command> [<git command options>]
```

### Options

- `-h, --help` - Show help message and exit
- `-s, --split` - The split hour (e.g., `9`)
- `-t, --to` - The target hour range (e.g., `21-30`)

### Example

```bash
gitm -s 9 -t 21-30 -- commit -m "message"
```
