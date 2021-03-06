# gsd-cli

[![Chat / Support](https://img.shields.io/badge/Chat%20%2F%20Support-discord-7289DA.svg?style=flat)](https://discord.gg/EMbcgR8)
[![GitHub license](https://img.shields.io/badge/license-MIT-blue.svg?style=flat)](https://github.com/Egeeio/game-server-containers/blob/master/LICENSE)

gsd (Game Server Daemon) is a cli tool for deploying dedicated game servers as systemd units (daemons) on Linux (WSL also) systems running systemd.

## Prerequisites

gsd is written with Ruby **2.5** so you'll need the Ruby development headers. You may need to enable multiarch as well.

For Debian systems, run `dpkg --add-architecture i386`, and then install the dependencies: `apt-get install steamcmd ruby-dev`

gsd utilizes several Ruby Gems and uses Bundler to manage them. First, install Bundler: `gem install bundler` and then install the Gems by running `bundle` from the repo directory.

## Usage

gsd is a pretty standard [Commander](https://github.com/commander-rb/commander)-based cli. All commands have built-in `--help` functions. Game servers are installed as systemd units and gsd provides a thin wrapper around common systemd functions. Examples:

`gsd status tf2` is _roughly_ equivilent to `systemctl status tf2`

`gsd restart rust` is _roughly_ equivilent to `systemctl restart rust`

The gsd cli is not (yet) installed as a binary application, and must be used from the repository directory itself. Clone this repo and call `gsd` from the top-level repository directory. For example:

`./bin/gsd status gmod`

Installing a server accepts a parameter for a path. Example: `./bin/gsd install sdtd --path /home/egee/sdtd`. If the directory does not exist, it will be created for you. If no path is provided, the default path is `/tmp/`. Since the game server is **installed** as a systemd unit, elevated permissions are required.

## Supported Games

* GarrysMod
* Rust
* 7 Days to Die
* Starbound
* Team Fortress 2
