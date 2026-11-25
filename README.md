[README.md](https://github.com/user-attachments/files/35391951/README.md)
# System_info

A small Bash script that prints basic system information from the command line. Pick a flag, get an answer: host name, logged-in users, or network details. It uses `getopts` to read the flags, so it behaves like a real CLI tool.

Built as part of my cybersecurity learning path (**SleepySOC**) to practice Bash scripting, argument parsing, and the Linux commands analysts use daily for quick host triage.

## Usage

```bash
chmod +x system_info.sh
./system_info.sh [options]
```

## Options

| Flag | What it does | Command used |
|------|--------------|--------------|
| `-h` | Show the help message | `echo` |
| `-n` | Show the host name | `hostname` |
| `-w` | Show who is logged in | `who` |
| `-i` | Show IP and network info | `ip a` |

Flags can be combined and run in the order you type them.

## Examples

```bash
./system_info.sh -h        # show help
./system_info.sh -n        # print the computer name
./system_info.sh -n -i     # host name, then IP and network info
./system_info.sh -w -n     # logged-in users, then host name
```

An unknown flag prints an error and exits with code 1:

```bash
./system_info.sh -z
# Invalid option. Use -h for help.
```

## How it works

The script loops over the flags with `getopts "hnwi"`. Each flag letter lands in a variable, and a `case` block runs the matching command. Any letter not in the list falls through to a catch-all that prints an error and exits.

## Requirements

Linux with Bash, plus the `hostname`, `who`, and `ip` commands (all standard on most distros, including Kali and Ubuntu).

## Author

**SleepySOC** (Abdul-Rahman) — [Medium](https://medium.com/@a.rahman25cs) · [LinkedIn](https://www.linkedin.com/in/abdul-rahman-a97239329)
