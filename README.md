MetaMod Source Updater
=================

Updates or installs the latest MetamodSource stable release or snapshots.

## Features

* Installs/updates stable releases or snapshots
* Downloaded packages will be cached and not downloaded the next time
* Can fix the permission afterwards (--fixpermissions)

## Installation

```shell
# Change to any directory where you want to install it first
apt-get install lynx wget findutils rsync git -y
git clone https://github.com/mrc4tt/mmsource-updater.git
cd mmsource-updater
chmod u+x update.sh
./update.sh
```

## Usage

### Syntax
```shell
./update.sh <game_dir> [<optional Package URL>] --snapshot-stable --snapshot-dev --install --dontask --fixpermissions
```

### Options

#### --snapshot-stable

Updates or installs the latest Metamod Source STABLE snapshot.

#### --snapshot-dev

Updates or installs the latest Metamod Source DEV snapshot.

#### --install

Installs metamod source instead of updating.

#### --dontask

Never ask for anything during execution.
This affects the situation when no package URL was found or
the security check before continuing the update

#### --fixpermissions

Reads the owner and the group of the game directory of the srcds after the update
and applies them recursively to the metamod source files.
This is needed if the update is executed by root and the srcds doesn't run as root.

### Examples
```shell
./update.sh /game/css/cstrike
./update.sh /game/csgo/csgo

./update.sh /srcds/css/cstrike --install --fixpermissions # Install sourcemod and fix the file permissions afterwards
./update.sh /srcds/css/cstrike --snapshot-stable          # Update sourcemod to the latest STABLE snapshot
./update.sh /srcds/css/cstrike --snapshot-dev             # Update sourcemod to the latest DEV snapshot
./update.sh /srcds/css/cstrike --dontask                  # Never ask for anything
```

## Settings
```bash
# The source code of this page will be searched for the latest sourcemod package
# We assume that the last one is the latest
SNAPSHOT_STABLE_MIRROR="https://mms.alliedmods.net/mmsdrop/1.11/"
SNAPSHOT_STABLE_SEARCHPATTER="https:.*mmsource-.*-linux.*gz"

SNAPSHOT_DEV_MIRROR="https://mms.alliedmods.net/mmsdrop/1.12/"
SNAPSHOT_DEV_SEARCHPATTER="https:.*mmsource-.*-linux.*gz"
```

## Credits
[Thanks for loan of script! - BCServ! (SourceMod)](https://github.com/bcserv/sourcemod-updater)
