# shun: a workaround for missing flags in UNIX `shutdown` commands

# EXAMPLE

```console
$ shutdown -h now
```

# ABOUT

shun is a wrapper for native `shutdown` commands, which tend to provide different flags for different particular UNIX distributions. shun does not attempt to support the vast majority of these many features, but rather provides a minimal syntax and semantics support, in order to help in porting shell scripts between different UNIX systems, where hardcoded and difficult to change commands may be invoked on systems with incompatible feature flags.

Semantics are NOT guaranteed to behave identically: shun simply plugs into a compatible syntax, and assumes some default values. For example, shun's `shutdown` always assumes desired time = `now`. In fact, syntax is NEITHER guaranteed to be preserved; even after `getopt` is added to this implementation, flag incompatibilities between different systems will continue to present difficulties. Ah well.

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

# REQUIREMENTS

* [coreutils](https://www.gnu.org/software/coreutils/coreutils.html)

## Recommended

* [vast](http://github.com/mcandre/vast)
* [shfmt](https://github.com/mvdan/sh) (e.g. `GO111MODULE=on go get mvdan.cc/sh/v3/cmd/shfmt`)
* [bashate](https://pypi.python.org/pypi/bashate/0.5.1)
* [shlint](https://rubygems.org/gems/shlint)
* [checkbashisms](https://sourceforge.net/projects/checkbaskisms/)
* [ShellCheck](https://hackage.haskell.org/package/ShellCheck)
* [stank](https://github.com/mcandre/stank) (e.g. `go get github.com/mcandre/stank/...`)
* [slick](https://github.com/mcandre/slick) (e.g. `go get github.com/mcandre/slick/....`)

# DEVELOPMENT

## Lint

```console
$ vast [lint]
```
