---
description: Instructions for installing Docker Desktop on Ubuntu
keywords: requirements, apt, installation, ubuntu, install, uninstall, upgrade, update
title: Install Docker Desktop on Ubuntu
toc_max: 4
---


To get started with Docker Desktop on Ubuntu, make sure you
[meet the prerequisites](#prerequisites), then
[install Docker Desktop](#install-docker-desktop).

## Prerequisites

Your Ubuntu distribution must meet the [system requirements](../install.md#system-requirements) to install and launch Docker Desktop successfully.

### OS requirements

To install Docker Desktop, you need the 64-bit version of one of these Ubuntu
versions:

- Ubuntu Jammy Jellyfish 22.04 (LTS)
- Ubuntu Impish Indri 21.10

Docker Desktop is supported on `x86_64` (or `amd64`) architecture.

### Uninstall old versions

To remove Docker Desktop for Linux, run:

```console
$ sudo apt remove docker-desktop
```

For a complete cleanup, remove configuration and data files at `$HOME/.docker/desktop`, the symlink at `/usr/local/bin/com.docker.cli`, and purge
the remaining systemd service files.

```console
$ rm -r $HOME/.docker/desktop
$ sudo rm /usr/local/bin/com.docker.cli
$ sudo apt purge docker-desktop
```

> **Note**
>
> If you have installed the Docker Desktop for Linux tech preview or beta version, you need to remove all files that were generated by those packages (e.g., `~/.config/systemd/user/docker-desktop.service`, `~/.local/share/systemd/user/docker-desktop.service`).


## Install Docker Desktop

Recommended approach to install Docker Desktop on Ubuntu:

1. [Set up Docker's DEB repository](../../../engine/install/ubuntu.md#set-up-the-repository) 

2. Download latest DEB package from the [release](../release-notes/index.md) page.

3. Install the package with apt as follows:
    
```console
$ sudo apt-get update
$ sudo apt-get install ./docker-desktop-<version>-<arch>.deb
```

> **Note**
>
> At the end of the installation process, `apt` displays an error due to installing a downloaded package. You
> can ignore this error message.
>
>  ```
>  N: Download is performed unsandboxed as root, as file '/home/user/Downloads/docker-desktop.deb' couldn't be accessed by user '_apt'. - pkgAcquire::Run (13: Permission denied)
>  ```

There are a few post-install configuration steps done through the maintainers' scripts (post-install script contained  in the deb package.

The post-install script:

- sets the capability on the Docker Desktop binary to map privileged ports and set resource limits
- adds a DNS name for Kubernetes to `/etc/hosts`
- creates a link from `/usr/bin/docker` to `/usr/local/bin/com.docker.cli`

## Launch Docker Desktop

{% include desktop-linux-launch.md %}


## Upgrade Docker Desktop

Once a new version for Docker Desktop is released, the Docker UI shows a notification. 
You need to download the new package each time you want to upgrade Docker Desktop and run

```console
$ sudo apt-get install ./docker-desktop-<version>-<arch>.deb
```


## Uninstall Docker Desktop

To remove Docker Desktop for Linux, run:

```console
$ sudo apt remove docker-desktop
```

For a complete cleanup, remove configuration and data files at `$HOME/.docker/desktop`, the symlink at `/usr/local/bin/com.docker.cli`, and purge
the remaining systemd service files.

```console
$ rm -r $HOME/.docker/desktop
$ sudo rm /usr/local/bin/com.docker.cli
$ sudo apt purge docker-desktop
```

Remove the `credsStore` and `currentContext` properties from `$HOME/.docker/config.json`. Additionally, you must delete any edited configuration files manually. 

## Next steps

- Take a look at the [Get started](../../../get-started/index.md) training modules to learn  how to build an image and run it as a containerized application.
- Review the topics in [Develop with Docker](../../../develop/index.md) to learn how to build new applications using Docker.