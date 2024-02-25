# Ansible baseline role for Ubuntu

A basic Ansible role to update and configure an Ubuntu
server.

> **Note**
>
> Do not use this role without first testing in a non-operational environment.

> **Note**
>
> There is a [SLSA](https://slsa.dev/) artifact present under the
> [slsa action workflow](https://github.com/konstruktoid/ansible-role-baseline/actions/workflows/slsa.yml)
> for verification.

## Task list overview

- Install local facts
- Configure local facts and install Python dependencies
- Configure package manager
- Configure systemd timesyncd
- Configure needrestart, install and remove various packages
- Configure apport
- Configure motdnews
- Configure sudo
- Add issue message

## Role Variables with defaults

### ./defaults/main/packages.yml

```yaml
system_upgrade: true
packages_blocklist:
  - apport*
  - beep
  - pastebinit
  - popularity-contest
  - prelink
  - rpcbind
  - rsh*
  - talk*
  - telnet*
  - tftp*
  - whoopsie
  - xinetd
  - yp-tools
  - ypbind
packages_installation:
  - debsums
  - gnupg2
  - haveged
  - libpam-tmpdir
  - lsb-release
  - needrestart
  - unattended-upgrades
```

`system_upgrade: true` will run `apt upgrade`.

`packages_installation` is packages to be installed and
`packages_blocklist` is packages to be removed.

### ./defaults/main/timesyncd.yml

```yaml
---
manage_timesyncd: true

fallback_ntp:
  - ntp.netnod.se
  - ntp.ubuntu.com
ntp:
  - 2.pool.ntp.org
  - time.nist.gov
```

If `enable_timesyncd: true` then configure systemd
[timesyncd](https://manpages.ubuntu.com/manpages/jammy/man8/systemd-timesyncd.service.8.html).

## Contributing

Do you want to contribute? Great! Contributions are always welcome,
no matter how large or small. If you found something odd, feel free to submit a
issue, improve the code by creating a pull request, or by
[sponsoring this project](https://github.com/sponsors/konstruktoid).

## License

Apache License Version 2.0

## Author Information

[https://github.com/konstruktoid](https://github.com/konstruktoid "github.com/konstruktoid")
