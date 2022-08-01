nRonn Installation
====================

## Installation Process

### From a Package Manager

TBD
### From RubyGems

nRonn is distributed as a gem package, which can be used if you don't have
a supported package manager. Install with rubygems:

```
gem install nronn
ronn --help
```

nRonn includes completion definitions for bash and zsh, but these are not
installed into the system locations as part of the gem. You will need to figure 
out how to install those into your system to make them available in your shell.

A decent way to do this is probably to add symlinks to your system shell
completion directories pointing at the files in the installed gem.

In Zsh, you can do something like this:

```
ronn_dist_dir=$(dirname $(dirname $(gem which nronn)))
ronn_zsh_dir="$ronn_dist_dir/completion/zsh"
ln -s "$ronn_zsh_dir/_ronn" /usr/local/share/zsh/site-functions
```

In Bash, something like this:

```
ronn_dist_dir=$(dirname $(dirname $(gem which nronn)))
ronn_bash_dir="$ronn_dist_dir/completion/bash"
ln -s "$ronn_bash_dir/ronn" /usr/local/etc/bash_completion.d
```

You will need to redo these steps each time you upgrade `nronn` or install
it into a different Ruby environment. Sorry for the inconvenience; this seems
to be a limitation of the `gem` installation mechanism.

If that `gem which` stuff doesn't work for you, you can `gem install gem-path`
and use `gem path nronn` instead.


## Building from Source

Hacking? Install nRonn from source.

Clone the git repository and put ronn/bin on your PATH:

```
git clone git://github.com/apjanke/nronn
PATH=$(pwd)/nronn/bin:$PATH
```

The following gems are required for nronn development:
 * nokogiri
 * mustache
 * kramdown
 * rubocop
 * sinatra
 * rack
 * rake
 * test-unit

```
gem install nokogiri mustache kramdown rubocop sinatra rack rake test-unit
```

Or install them with bundler using the project's gem definition:

```
bundle install --with development
```

Then you should be able to make changes directly to your cloned repo and have
them be reflected in your active `ronn` command.

## Legacy Versions

Historical Ronn tarballs available at [the original Ronn repo](https://github.com/n-ronn/nronn/tags).

```
curl -L https://github.com/n-ronn/nronn/archive/refs/tags/0.6.6.tar.gz | tar xvzf -
cd rtomayko-r*
ruby setup.rb
```
