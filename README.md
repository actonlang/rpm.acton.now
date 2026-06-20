# Acton RPM Repository

This repository publishes stable Acton RPM packages for DNF/YUM based
systems.

## Install

Import the Acton package signing key, add the repository, and install Acton:

```sh
sudo rpm --import https://rpm.acton.now/acton.gpg
sudo tee /etc/yum.repos.d/acton.repo >/dev/null <<'REPO'
[acton]
name=Acton
baseurl=https://rpm.acton.now/$basearch
enabled=1
gpgcheck=1
repo_gpgcheck=1
gpgkey=https://rpm.acton.now/acton.gpg
REPO
sudo dnf install -y acton
acton version
```

On systems that use `yum` instead of `dnf`, use the same repo file and run:

```sh
sudo yum install -y acton
```

## Upgrade

```sh
sudo dnf upgrade -y acton
```

## Remove

```sh
sudo dnf remove -y acton
sudo rm -f /etc/yum.repos.d/acton.repo
```

## Repository Layout

DNF substitutes `$basearch` automatically. The published architecture
repositories are:

- `https://rpm.acton.now/x86_64`
- `https://rpm.acton.now/aarch64`

## Signing

Keep both signature checks enabled:

```ini
gpgcheck=1
repo_gpgcheck=1
```

The public key is published at `https://rpm.acton.now/acton.gpg`. The RPM
packages and the repository metadata are signed with the matching private key.
