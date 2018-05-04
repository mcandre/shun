# shun: a workaround for missing flags in UNIX `shutdown` commands

# EXAMPLE

```console
$ shutdown -h now
```

# ABOUT

shun is a wrapper for native `shutdown` commands, which tend to provide different flags for different particular UNIX distributions. shun does not attempt to support the vast majority of these many features, but rather provides a minimal syntax and semantics support, in order to help in porting shell scripts between different UNIX systems, where hardcoded and difficult to change commands may be invoked on systems with incompatible feature flags.

Semantics are NOT guaranteed to behave identically: shun simply plugs into a compatible syntax, and assumes some default values. For example, shun's `shutdown` always assumes desired time = `now`.

# INSTALL

1. `git clone https://github.com/mcandre/shun.git`
2. Soft link `lib/shutdown` onto a directory shadowing native `shutdown`.

For example, in Haiku OS:

```console
$ git clone https://github.com/mcandre/shun.git /boot/home/shun
$ ln -s /boot/home/shun/lib/shutdown /boot/system/non-packaged/bin/shutdown
```
# UNINSTALL

Remove the shadow `shutdown` link.
