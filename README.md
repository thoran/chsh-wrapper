# chsh-wrapper

Change the login shell, choosing from every copy of every shell actually installed rather than from the one path `chsh` would guess at.

## Why

`/etc/shells` lists shells by a single path apiece, usually the system copy under `/bin`. A shell installed by Homebrew, or built by hand, sits somewhere else entirely, and there may be more than one copy of it. This reads `/etc/shells` for the names, then asks `which -a` for every path each name resolves to, and offers the lot.

## Usage

Named, where the shell is known:

```shell
chsh-wrapper zsh
```

The name is resolved to a path and passed to `chsh`.

Unnamed, to choose from a menu:

```shell
chsh-wrapper
```

Every path found is listed and numbered; enter a number to select one.

Anything else, such as `chsh-wrapper -s /bin/zsh`, is passed to `chsh` unchanged, so as it can stand in for `chsh`.

## Notes

It runs `sudo chsh -s <path> <user>` and prints the command before running it, so what it is about to do is visible first.

## License

MIT
