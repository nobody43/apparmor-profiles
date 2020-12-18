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
### curl
Read-only version by default.

WARNING: custom applications might fail without adjustment!

#### Compatibility
- Pi-hole (commented out by default)

## Supported systems

- Debian 10
- Armbian Buster
- Ubuntu 20.04 (commented out by default)
