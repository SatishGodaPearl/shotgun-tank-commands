
![Shotgun Software](https://media.licdn.com/media/p/3/000/208/39c/17ade73.png)

# shotgun-tank-commands
This is the list Shotgun's Tank commands and their descriptions

The following commands are available:

## Admin Commands

### localize

Installs the Core API into your current Configuration. This is typically done
when you want to test a Core API upgrade in an isolated way. If you want to
safely test an API upgrade, first clone your production configuration, then
run the localize command from your clone's tank command.

### share_core

When new projects are created, these are often created in a state where each
project maintains its own independent copy of the core API. This command
allows you to take the core for such a project and move it out into a separate
location on disk. This makes it possible to create a shared core, where
several projects share a single copy of the Core API. Note: if you already
have a shared Core API that you would like this configuration to use, instead
use the attach_to_core command.

### attach_to_core

When new projects are created, these are often created in a state where each
project maintains its own independent copy of the core API. This command
allows you to attach the configuration to an existing core API installation
rather than having it maintain its own embedded version of the Core API. Note:
If you don't have a shared core API yet, instead use the share_core command.

### cache_apps

Toolkit manages a bundle cache to ensure that all versions of apps and engines
that are specified in the environments exists locally. This cache is normally
automatically managed by the update and install commands, but if you are
manually editing version numbers inside the environment configuration, you may
need to run the cache_apps command to ensure that all necessary code exists in
the cache.

### clear_shotgun_menu_cache

Clears the Shotgun Menu Cache associated with this Configuration. This is
sometimes useful after complex configuration changes if new or modified
Toolkit menu items are not appearing inside Shotgun.

### move_configuration

Moves this configuration from its current disk location to a new location.

### configurations

Shows an overview of the different configurations registered with this
project.

### migrate_published_file_entities

Migrates your publishes from TankPublishedFile to PublishedFile and sets this
configuration to use PublishedFile whenever publishing.

### synchronize_folders

Ensures that the local folders and folder metadata is up to date with Shotgun.

### upgrade_folders

Upgrades on old project to use the shared folder generation that was
introduced in Toolkit 0.15

### unregister_folders

Unregisters the folders for an object in Shotgun.

### migrate_desktop

Migrates Shotgun Desktop away from the Template Project.

### cache_yaml

Populates a cache of all YAML data found in the config.

## Configuration Commands

### setup_project

Sets up a new project with the Shotgun Pipeline Toolkit.

### core

Updates your Toolkit Core API to a different version.

### dump_config

Dump the specified config to a file or <stdout>.If the `--file` option is not
specified, the config will be written to stdout. The tank command itself also
writes to <stdout> so be careful of redirecting to a file and expecting to use
the config immediately.

### validate

Validates your current Configuration to check that all environments have been
correctly configured.

### install_app

Adds a new app to your configuration.

### push_configuration

Pushes any configuration changes made here to another configuration. This is
typically used when you have cloned your production configuration into a
staging sandbox, updated the apps in this sandbox and want to push those
updates back to your production configuration.

### install_engine

Adds a new engine to your configuration.

### updates

Checks if there are any app or engine updates for the current configuration.

Examples:
---------

Check everything:
> tank updates

Check the Shot environment:
> tank updates Shot

Check all maya apps in all environments:
> tank updates ALL tk-maya

Check all maya apps in the Shot environment:
> tank updates Shot tk-maya

Make sure the loader app is up to date everywhere:
> tank updates ALL ALL tk-multi-loader

Make sure the loader app is up to date in maya:
> tank updates ALL tk-maya tk-multi-loader


## Developer Commands

### switch_app

Switches an app from one code location to another.

### app_info

Shows a breakdown of your installed apps.

### shell

Starts an interactive Python shell for the current location.

## Login Commands

### logout

Log out of the current user (no need for a context).

## Production Commands

### folders

Creates folders on disk for your current context. This command is typically
used in conjunction with a Shotgun entity, for example 'tank Shot P01 folders'
in order to create folders on disk for Shot P01.

### preview_folders

Previews folders on disk for your current context. This command is typically
used in conjunction with a Shotgun entity, for example 'tank Shot P01
preview_folders' in order to show what folders would be created if you ran the
folders command for Shot P01.

## Shell Engine Commands

### launch_maya_{version}

Launches and initializes an application environment.


### open_log_folder

Opens the folder where log files are being stored.

### --debug

Sometimes it can be useful to see what is going on under the hood. You can pass a --debug flag to the tank command which will enable verbose output and timings, sometimes making it easier to track down problems or understand why something isn't doing what you expected it to.

# Some Example

### Show all tank commands for an asset named 'piano'
> tank Asset piano

### We can also list all assets containing the phrase 'pi'
> tank Asset pi

### We can execute the built-in folder creation command for the piano
> tank Asset piano folders

### If the application launcher app is installed, we can launch maya and set the work area to the piano
> tank Asset piano launch_maya

### Alternatively, we can specify a path on disk instead of a Shotgun entity
> tank /mnt/projects/hero/assets/piano launch_maya

### Or we can change our work directory and run tank like this
> cd /mnt/projects/hero/assets/piano launch_maya

> tank launch_maya
