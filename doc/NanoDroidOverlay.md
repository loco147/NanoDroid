Table of Contents
=================

   * [NanoDroid-Overlay Script](#nanodroid-overlay-script)
      * [Purpose](#purpose)
         * [Pseudo Debloat Feature](#pseudo-debloat-feature)
         * [Force Debloat Feature](#force-debloat-feature)
         * [Alter the list of pseudo-debloated applications](#alter-the-list-of-pseudo-debloated-applications)
      * [Invocation](#invocation)
      * [Overview](#overview)
      * [Default Settings](#default-settings)

Created by [gh-md-toc](https://github.com/ekalinin/github-markdown-toc)

# NanoDroid-Overlay Script

## Purpose

The `nanodroid-overlay` Script, respectively it's shortcut `novl` is used by NanoDroid to handle the

  * Pseudo Debloat Feature (Magisk Mode)
  * Force Debloat Feature (System Mode)

### Pseudo Debloat Feature

Magisk allows for apps to be magically removed upon runtime, they don't get actually removed from `/system` but they are pseudo-removed during runtime.

### Force Debloat Feature

In System Mode apps can are moved to `/data/media/0/nanodroid_backups/` or restored from there.

### Alter the list of pseudo-debloated applications

You can pseudo-debloat applications by adding them to configuration file

`.nanodroid-overlay`

on your device, in one of the following directories

* `/data/media/0` (internal storage (TWRP))
* `/sdcard1` (internal storage (ORANGEFOX))
* `/external_sd` (TWRP path to SD Card (if any))
* `/data` (fallabck)

See the [default settings](.nanodroid-overlay) (contains instructions aswell).

The syntax is pretty simple:

* one app per line (no leading spaces)
* name must be an exact match of the **directory** of the app, **not** the app name or app id
* commented out lines (starting with #) are ignored

The following paths are searched for matching apps:

* `/system/app`
* `/system/priv-app`
* `/system/reserve`
* `/system/product/app`
* `/system/product/priv-app`

After you've made your changes, issue the following command on your device, either using `adb shell` or **Termux** as root:

`nanodroid-overlay --update`

## Invocation

From within a terminal on your device, for example `adb shell` or `Termux` invoke the script using either

`nanodroid-overlay [switch] [parameter(s)]`

or

`novl [switch] [parameter(s)]`

## Overview

`-a`, `--add` [app]

add Overlay for **app** (if it exists) and add it to the config file; [app] is the name of the app's directory in `/system/app` or `/system/priv-app`

`-r`, `--remove` [app]

remove Overlay for **app** (if it exists) and remove it from the config file; [app] is the name of the app's directory in `/system/app` or `/system/priv-app`

`-s`, `--show`

show all apps that **don't** have an Overlay (slow)

`-l`, `--list`

show all apps that **do** have an Overlay

`-x`, `--create`

create Overlays from config file

`-u`, `--update`

**The following features are only available in Magisk Mode:**

remove existing Overlays and re-create them from the config file

`-c`, `--clear`

remove existing Overlays

`-g`, `--genconfig`

(re-)create config file from existing Overlays

## Default Settings

The following applications are debloated by default

* Basic Dreams
* Calendar
* CM File Manager
* crDroid Filemanager and Music Player
* Eleven, Phonograph (Audio Player)
* E-Mail + Exchange2
* Browser, Gello, Slimperience, Via Browser, Jelly (Browser)
* PhotoTable
* Sound Recorder, Recorder
* messaging (SMS & MMS)
* Wallpaper, WallpaperPickerGoogle (Google Wallpaper application)
* Wallpaper Backup
* mGerrit
* FM Radio
* Gallery2
* OmniSwitch
* Screencast
* Snap, Snapdragon Camera (Camera)
* Resurrection Remix Statistics
* Sim Toolkit
