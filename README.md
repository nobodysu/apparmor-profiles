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
Read-only version by default.

WARNING: custom applications might fail without adjustment!

#### Compatibility
- Pi-hole (commented out by default)

#### Supported systems
- Debian 10
- Armbian Buster
- Ubuntu 20.04 (commented out by default)

### [czkawka](https://github.com/nobodysu/apparmor-profiles/blob/master/usr.local.bin.linux_czkawka)
Snap releases are not supported.

#### Dependencies
- `abstractions/3rd/file-chooser`
- `abstractions/3rd/nameservice-strict`
- `local/usr.lib.libreoffice.program.soffice.bin`
- `usr.bin.ristretto`

#### Excessiveness
- interactive `file-chooser` dialog
- opening files with `xdg-open`
- various `sanitized_helper` transitions

#### Supported systems
- Xubuntu 20.10
- Ubuntu 21.04

### [ristretto](https://github.com/nobodysu/apparmor-profiles/blob/master/usr.bin.ristretto)

#### Excessiveness
- file deletion by write access
- editing with `dash` transition
- *disabled* interactive `file-chooser` dialog

#### Supported systems
- Xubuntu 20.10

### [yadifa](https://github.com/nobodysu/apparmor-profiles/blob/master/usr.bin.yadifa)
Without transfers.

#### Supported systems
- Debian 10

# Links
- https://github.com/qarmin/czkawka/
