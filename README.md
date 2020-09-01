# Toolbox Custom Images

These toolbox images are tailored for my own use and stored in quay.io.

## devenv - toolbox

Preinstalled dev environment to build `rpm` packages. Also used for Fedora package reviews.

## base - toolbox

Preinstalled base environment used to complement packages installed via `rpm-ostree`.
You can either use `toolbox run --container <container> <command>` to launch the preinstalled package or
you can create a shim, store it (for instance) in `~/.local/bin` and `ln -s <shim_script> <package_binary>`  to launch a preinstalled package:

```
#!/bin/sh
basename_bin=$(basename $0)
exec toolbox run --container <container> $basename_bin "$@"
```

## Example usage

Assuming you want run `ranger` and your base container is named `base`:

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
