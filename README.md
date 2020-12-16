# apparmor-profiles
## Prerequisites

```
# apt install apparmor-utils
```

## Installation
```
# mv usr.bin.curl /etc/apparmor.d/
# aa-enforce /etc/apparmor.d/usr.bin.curl
```

## Deinstallation
```
# aa-disable /etc/apparmor.d/usr.bin.curl
# rm /etc/apparmor.d/usr.bin.curl
```

## Testing
```
# aa-complain /etc/apparmor.d/usr.bin.curl
```
Error log is `/var/log/syslog` by default.

# curl
Read-only version by default.

WARNING: custom applications might fail without adjustment!

# Supported systems

- Debian 10
- Armbian Buster
- Ubuntu 20.04
