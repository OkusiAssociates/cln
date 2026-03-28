# cln

Recursively clean temporary and junk files from directories.

## Default Patterns

```
*~  ~*  .~*  .*~  DEADJOE  dead.letter  wget-log*
```

## Installation

```bash
ln -s /path/to/cln /usr/local/bin/cln
```

## Usage

```bash
# Clean current directory (interactive)
cln

# Clean without prompting
cln -P /path/to/clean

# Quiet mode, no prompts
cln -Pq /tmp

# Add custom patterns
cln -a '*.bak,*.tmp' .

# Replace default patterns entirely
cln -S '*.tmp,*.old' /tmp

# Deep clean (depth 7)
cln -Pqm 7 /home/user

# Multiple directories
cln -P dir1 dir2 dir3
```

## Options

| Option | Description |
|--------|-------------|
| `-h` | Show help |
| `-V` | Show version |
| `-p`, `-n` | Prompt before deleting (default) |
| `-P`, `-N` | Delete without prompting |
| `-v` | Increase verbosity |
| `-q` | Suppress output |
| `-m N` | Max depth (-1 = unlimited, default: 3) |
| `-a SPEC` | Add file patterns (comma-separated) |
| `-S SPEC` | Set/replace all patterns (overrides config) |
| `-L` | Follow symbolic links |

## Configuration

Patterns can be customized via config files (one pattern per line, `#` for comments):

| File | Purpose |
|------|---------|
| `~/.local/etc/default/cln` | User override |
| `/etc/default/cln` | System default |

First existing file wins. Command-line `-S` overrides config.

## Testing

```bash
./tests/run-all-tests.sh
```

## Requirements

- Bash 5.2+
- GNU findutils (find), GNU coreutils (rm)

#fin
