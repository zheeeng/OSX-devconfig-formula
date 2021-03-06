# System Preferences Panel

List of self flavored settings.

## General

* `Appearance` > Check `Automatically hide and show the menu bar`

## Desktop & Screen Saver

* Set desktop wallpaper
* `Screen Saver` > In `Sliding Panels`:

    Start after: `5 Minutes`
    Source: `National Geographic`
    Check `Shuffle slide order`
    Check `Show with clock`

## Dock

* Double-click a window's title bar to `zoom`
* Check `Automatically hide and show the Dock`

## Mission Control

* Dashboard: `Off` (** Default settings after OS X 10.10 **)  
    **For the OS X system version below Yosemite:** In Terminal execute:

        `defaults write com.apple.dashboard mcx-disabled -boolean YES`

## Security & Privacy

* `General` > Require password `5 minutes` after sleep or screen begins
* `General` > Allow apps downloaded from: `Anywhere`
* `FileVault` > Make sure turn on FileVault
* `Firewall` > Setup firewall list

## Spotlight

* Uncheck `Fonts`, `Images`

## Displays

* `Display` > Resolution `Scaled` to looks like 1440 x 900(For my 13″ rMBP)
* Uncheck `Automatically adjust brightness` (for over sensitive auto adjust reason, we will install f.lux application makes great work)

## Energy Saver

* Check `Show battery status in menu bar` 
* `Battery` > Turn display off after `5 minutes`
* `Power Adapter` > Turn display off after `10 minutes`
* Change battery to show percentage: `Menubar` > `Power status icon` > `Show Percentage`

## Keyboard

* Change automatic spelling checking scheme to U.S. English: `Text` > Scroll down `Spelling` bar to `Set up...` > check `U.S. English` & uncheck `British English`
* Use Karabiner keyboard remapping, check [Karabiner](../Karabiner/index.html) section.
* `Shortcuts` > Full Keyboard Access: In windows and dialogs, press Tab to move keyboard focus between: `All controls`  
**Tips: `ESC` == `dialog cancel`; `Command` + `Delete` == `Discard` or `Don't save`**
* `Shortcuts` > `Input Sources` > `Shift` + `Command` + `Space` = `Select the previous input source` && `Command` + `Space` = `Select the next input source`
* `Shortcuts` > `Spotlight` > Cancel all spotlight shortcuts (use Alfred 2 instead of Spotlight later)
* `Shortcuts` > `App Shortcuts` > Add {Application: `All Applications`,  Menu Title: `Zoom`, Keyboard Shortcut: `Shift` + `Command` + `M`} (compare with `Command` + `M` == `Minimize Window`)

## Trackpad

* Look up & data detectors: `Tap with three fingers`
* Check all `Point & Click`, `Scroll & Zoom`, `More Gestures`

## Sound

* Uncheck `Show volume in menu bar` (use function keys)

## iCloud

* Check all service.

## Network

* Check `Show Wi-Fi status in menu bar`

## Bluetooth

* Uncheck `Show Bluetooth in menu bar`

## Sharing

* Change Computer Name(hostname)

## Users & Groups

* Disable Guest User
**If any problem happens, maybe you'd turn off FileVault & iCloud Find My Mac & restart your Mac first**

## App Store

* For application update: Check `Automatically check for updates`, `Install system data files and security updates` && Uncheck other checkboxes
* For password settings:  
	Purchases and In-app Purchases: `Always Require`
	Free Download: `Require Password`

## Dictation & Speech

* `Option` + `Esc` = Speak selected text : `Text to Speech` > Check `Speak selected text when the key is pressed`

