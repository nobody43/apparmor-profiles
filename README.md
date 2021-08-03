# apparmor-profiles
## Prerequisites
```
# apt install apparmor-utils
```

## Testing
```
# mv usr.bin.curl /etc/apparmor.d/
# aa-complain /etc/apparmor.d/usr.bin.curl
```
Error log is `/var/log/syslog` by default.

## Installation
```
# aa-enforce /etc/apparmor.d/usr.bin.curl
```

## Deinstallation
```
# aa-disable /etc/apparmor.d/usr.bin.curl
# rm /etc/apparmor.d/usr.bin.curl
```

## Profiles
### [curl](https://github.com/nobodysu/apparmor-profiles/blob/master/usr.bin.curl)
WARNING: custom applications might fail without adjustment!

#### Dependencies
- `abstractions/3rd/nameservice-strict`

#### Compatibility
- Pi-hole (commented out by default)

#### Tested on
- Debian 10
- Armbian Buster
- Xubuntu 21.04 (commented out by default)

### [czkawka](https://github.com/nobodysu/apparmor-profiles/blob/master/usr.local.bin.linux_czkawka)
Snap releases are not supported.

#### Dependencies
- `abstractions/3rd/file-chooser`
- `abstractions/3rd/nameservice-strict`
- `local/usr.lib.libreoffice.program.soffice.bin`
- `usr.bin.ristretto`

#### Excessiveness
- `w`rite access on home
- interactive `file-chooser` dialog
- opening files with `xdg-open`
- various `sanitized_helper` transitions
- *disabled* `dbus-overwrite`

#### Tested on
- Xubuntu 21.04
- Ubuntu 21.04

### [ristretto](https://github.com/nobodysu/apparmor-profiles/blob/master/usr.bin.ristretto)

#### Excessiveness
- file deletion by `w`rite access
- editing with `dash` transition
- *disabled* interactive `file-chooser` dialog

#### Tested on
- Xubuntu 21.04

### [openvpn](https://github.com/nobodysu/apparmor-profiles/blob/master/usr.sbin.openvpn)
Without NetworkManager. Without interactive credentials supplying, so be sure to provide them in config with `auth-user-pass`.

#### Dependencies
- `abstractions/3rd/nameservice-strict`

#### Tested on
- Debian 10

### [yadifa](https://github.com/nobodysu/apparmor-profiles/blob/master/usr.bin.yadifa)
Without transfers.

#### Tested on
- Debian 10

### [youtube-dl](https://github.com/nobodysu/apparmor-profiles/blob/master/usr.local.bin.youtube-dl)
No auto-update and debug.

#### Dependencies
- `abstractions/3rd/nameservice-strict`

#### Excessiveness
- *disabled* `--exec`

#### Compatibility
- yt-dlp

#### Tested on
- Debian 10
- Xubuntu 21.04
- Ubuntu 21.04

### [youtubedl-gui](https://github.com/nobodysu/apparmor-profiles/blob/master/usr.local.bin.youtubedl-gui)
Flatpack releases are not supported.

#### Dependencies
- `abstractions/3rd/nameservice-strict`
- `usr.local.bin.youtube-dl`

#### Excessiveness
- *disabled* interactive `file-chooser` dialog
- *disabled* `dbus-overwrite`
- *disabled* `qt5-settings-write`
- *disabled* `network` access

#### Tested on
- Debian 10
- Xubuntu 21.04
- Ubuntu 21.04

# Links
- [F**k AppArmor](https://presentations.nordisch.org/apparmor/) - crash course
- [AppArmor Core Policy Reference](https://gitlab.com/apparmor/apparmor/-/wikis/AppArmor_Core_Policy_Reference)
- https://github.com/qarmin/czkawka/
- https://github.com/yadifa/yadifa
- https://github.com/JaGoLi/ytdl-gui
