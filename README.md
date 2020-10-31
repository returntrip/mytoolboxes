Base Toolbox: [![Docker Repository on Quay](https://quay.io/repository/returntrip/devenv-fedora-toolbox/status "Docker Repository on Quay")](https://quay.io/repository/returntrip/devenv-fedora-toolbox)

Devenv Toolbox: [![Docker Repository on Quay](https://quay.io/repository/returntrip/devenv-fedora-toolbox/status "Docker Repository on Quay")](https://quay.io/repository/returntrip/devenv-fedora-toolbox)

# Toolbox Custom Images

These toolbox images are tailored for my own use and stored in quay.io.

## To-do

- Fix Fedora release 33
- Fix Fedora rawhide (when base container is available)

## Current toolbox images

### devenv - toolbox
Preinstalled dev environment to build `rpm` packages. Also used for Fedora package reviews.

### base - toolbox
Preinstalled base environment used to complement packages installed via `rpm-ostree`.

## Usage

You can either use `toolbox run --container <container> <command>` to launch the preinstalled package or
you can create a shim, store it somewhere in your `PATH` (for instance in `~/.local/bin`), `ln -s <shim_script> <package_binary>`  and finally launch a preinstalled package:

### Example usage

Assuming you want to run `ranger` and you want to name your container `base`:

- Create the toolbox:

    `toolbox create --container base --image quay.io/returntrip/base-fedora-toolbox`

- Create a shim:

    ```
    ~/.local/bin/toolbox-base-runner

    #!/bin/sh
    basename_bin=$(basename $0)
    exec toolbox run --container base $basename_bin "$@"
    ```

- Make the shim executable:

    `chmod +x toolbox-base-runner`

- Create a symbolic link for `ranger`:

    `ln -s toolbox-base-runner ranger`

- You can now use `ranger` on the host and launch `ranger` from the `base` toolbox 
