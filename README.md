# checkfor

Inspect command resolution and installed versions in your `$PATH`.

`checkfor` is a small, dependency-free **zsh** utility that shows **which executable is actually used** for a command and **what other instances exist** on your system. Optionally, it can run `--version` on each instance to give you a fast overview of toolchain chaos.

This is particularly useful on macOS and Linux systems with Homebrew, Xcode, SDKs, language runtimes, or multiple compiler installations.


## Features

- Resolves the **active executable** using shell command resolution
- Scans **every directory in `$PATH`** for additional executable instances
- Highlights the active command
- Optionally runs `--version` on **all discovered instances**
- ANSI-colored output (can be disabled)
- No external dependencies
- Fast, predictable, and shell-native

## Example Output

```
Using: /opt/homebrew/bin/python3

Found in PATH (3):

* /opt/homebrew/bin/python3
  /usr/bin/python3
  /Library/Frameworks/Python.framework/Versions/3.12/bin/python3

Version output (--version):

==> /opt/homebrew/bin/python3 --version
Python 3.12.1

==> /usr/bin/python3 --version
Python 3.9.6
```

## Usage

```sh
checkfor commandname
checkfor --version commandname
checkfor --help
```

### Examples

```sh
checkfor python
checkfor --version gcc
checkfor node
```

## Options

| Option      | Description                                        |
| ----------- | -------------------------------------------------- |
| `--version` | Run `<command> --version` for every instance found. This obviously should only be used with commands that support the --version parameter. |
| `--help`    | Show detailed help text and exit                   |

## Environment Variables

| Variable     | Effect                                                 |
| ------------ | ------------------------------------------------------ |
| `NO_COLOR=1` | Disable ANSI color output (useful for CI, logs, pipes) |

Example:

```sh
NO_COLOR=1 checkfor git
```

## Exit Codes

| Code | Meaning                      |
| ---: | ---------------------------- |
|    0 | Success                      |
|    1 | Usage error                  |
|  127 | Command not found in `$PATH` |


## Why this exists

`which` lies by omission.
`type` is accurate but incomplete.
`whereis` is noisy.

`checkfor` tells you **everything that matters**, clearly and quickly.


## Requirements

* `zsh` (tested with zsh 5.8+)
* macOS or Linux
* No GNU utilities required.


## License

See repository license.
