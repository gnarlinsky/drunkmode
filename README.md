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
* Currently, `rm` (including `rm -f`)

## Setting up:
* create `.drunkmoderc` for the first time
``` bash
$ touch ~/.drunkmoderc
```

* add source command to your `.bashrc` (note: NOT `.bash_profile`, since that is not
sourced when `exec bash`ing)
``` bash
source ~/.drunkmoderc
```

* copy or link commands to `usr/bin/` (assuming that's in your PATH)
``` bash
$ sudo ln -s ~/githubbed/drunkmode/drunkmodeo* /usr/bin/
```
You may have to precede the above command with `sudo`.

* copy or link `drunk_commands` to home directory from this (cloned repo) directory
``` bash
$ ln -s /path/to/currentdir/drunk_commands ~/.drunk_commands
```
or
``` bash
$ cp /path/to/currentdir/drunk_commands ~/.drunk_commands
```

* Note: may have to change permissions for commands (`chmod +x`)

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
![screen shot 2013-11-23 at 10 04 42
am](https://f.cloud.github.com/assets/4472418/1606777/fe41c914-5458-11e3-8fe3-6f8b3bedf46f.png)

<!--
## How it works
how works/env variable, bashrc, etc, or maybe the WARNING at the top is
sufficient-->

## Future/wishlist
* additional commands
* option for user to define their own commands to put under drunkmode control
* automate set up process
* `exec bash` ... but that would necessitate an entire overhaul, probably
* generate random strings to type out, rather than the same ones each time
* see Issues
