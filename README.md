# *DRAFT*:
Custom UNIX (Bash) commands to enable or disable "drunk mode."

## CAUTION! Danger!
* **No guarantees on anything! Use at your own risk!!! Not for public
consumption without reflection!**
* *`drunkmodeon` and `drunkmodeoff` use `exec bash` as a dirty
workaround for the fact that changes to environment variables that happen
during the execution of a script will not persist in the calling process's
environment. Since this puts you in a new shell, it's potentially problematic
(e.g. leaving your virtualenv, original shell's history unavailable,...).
See http://stackoverflow.com/a/497479, particularly the associated
discussion.*
* Also note I make a number of assumptions about directory structures and such.

## General idea
Ever accidentally `rm *`'d because you were a little inebriated (or very tired or extra stupid or what have you)?  Turn on
drunkmode to get extra prompts and warnings when carrying out the more
"dangerous" commands or actions.

## Affected commands
* Currently, `rm`

## Setting up:
* adding source command to bashrc (note: NOT bash_profile, since that is not
sourced when `exec bash`ing)
``` bash
##
# drunkmodeon and drunkmodeoff commands
##
source ~/.drunkmoderc
```

* copying or linking commands to usr/bin/ (assuming that's in your PATH)
``` bash
(todo)
```
* copying or linking .drunk_commands to home dir from this directory
``` bash
$ ln -s /path/to/currentdir/drunk_commands ~/.drunk_commands
```
or
``` bash
$ cp /path/to/currentdir/drunk_commands ~/.drunk_commands
```

* note may have to change permissions for commands (`chmod +x`)
* may automate this process later

## Using it
Turn drunkmode on
``` bash
$ drunkmodeon
```
Turn drunkmode off
``` bash
$ drunkmodeoff
```

## Examples/see it in action
(todo)

<!--
## How it works
how works/env variable, bashrc, etc, or maybe the WARNING at the top is
sufficient-->

## Future/wishlist
* additional commands to change
* automate set up process
* `exec bash` ... but that would necessitate an entire overhaul, probably
* generate random strings to type out, rather than the same ones each time
* see Issues
