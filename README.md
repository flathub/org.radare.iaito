# Radare Iaito for Flatpak

Official Radare Iaito Flatpak package.

<a href='https://flathub.org/apps/details/org.radare.iaito'><img width='120' alt='Download on Flathub' src='https://flathub.org/assets/badges/flathub-badge-en.png'/></a>

## Permissions

The required permissions for GUI are: `wayland`, X11 (`ipc` + `fallback-x11`), `dri`.
Also to allow ptrace in radare2: `devel`.


### Optional permissions

Some other permissions can be added using [Flatseal](https://flathub.org/apps/details/com.github.tchx84.Flatseal) GUI or via CLI using `flatpak override`.

To allow radare plugins to connect to your network or Internet:
```sh
flatpak override --user --share=network org.radare.iaito
```

To allow some plugins to attach to a usb device:
```sh
flatpak override --user --device=all org.radare.iaito
```

To allow some plugins to access to an specific folder not selected by the GUI (with optional `:ro` to only allow read only):
```sh
flatpak override --user --filesystem=/mnt/hdd:ro org.radare.iaito
```

The optional permissions you might require depends on the plugins you add and the use of it.

To reset back to default required permissions this command can be used:
```sh
flatpak override --user --reset org.radare.iaito
```

## CLI

With this flatpak, you can also run radare2 as cli.

To do so one need to define the following aliases:
```sh
alias r2='flatpak run --command=r2 org.radare.iaito'
alias r2agent='flatpak run --command=r2agent org.radare.iaito'
alias r2p='flatpak run --command=r2p org.radare.iaito'
alias r2pm='flatpak run --command=r2pm --share=network --devel org.radare.iaito'
alias r2r='flatpak run --command=r2r org.radare.iaito'
alias rabin2='flatpak run --command=rabin2 org.radare.iaito'
alias radare2='flatpak run --command=radare2 org.radare.iaito'
alias radiff2='flatpak run --command=radiff2 org.radare.iaito'
alias rafind2='flatpak run --command=rafind2 org.radare.iaito'
alias ragg2='flatpak run --command=ragg2 org.radare.iaito'
alias rahash2='flatpak run --command=rahash2 org.radare.iaito'
alias rarun2='flatpak run --command=rarun2 org.radare.iaito'
alias rasign2='flatpak run --command=rasign2 org.radare.iaito'
alias rasm2='flatpak run --command=rasm2 org.radare.iaito'
alias ravc2='flatpak run --command=ravc2 org.radare.iaito'
alias rax2='flatpak run --command=rax2 org.radare.iaito'
```

With this commands, by default no local files will be accesible.
To allow acces to a folder please use the special permissions procedure explained above or use `zenity` inside the flatpak sandbox to open a dialog using XDG portals.
Example:
```console
$ alias r2='flatpak run --command=r2 org.radare.iaito'
$ r2 -
[0x00000000]> o `!zenity --file-selection`
```

Also for r2pm, network is mandatory to be usable (for the packages repository), as well as an SDK runtime (for git and build tools) so the first run might require you to install the corresponding flatpak SDK.

## Folders

Since the application don't have access to the home folder by default, flatpak sets radare2 paths to:

- Radare 2 configuration: `~/.var/app/org.radare.iaito/config/radare2/`
- Radare 2 data: `~/.var/app/org.radare.iaito/data/radare2/`

## Projects included

List of project URLs of the modules included in this flatpak version of iaito with radare2:

- [iaito](https://github.com/radareorg/iaito)
  - [iaito-translations](https://github.com/radareorg/iaito-translations)
- [radare2](https://github.com/radareorg/radare2)
  - [r2ghidra](https://github.com/radareorg/r2ghidra)
  - [r2frida](https://github.com/nowsecure/r2frida)
  - [r2dec](https://github.com/wargio/r2dec-js)
  - [r2yara](https://github.com/radareorg/r2yara)
  - [r2ai](https://github.com/radareorg/r2ai)
  - [r2pipe](https://github.com/radareorg/radare2-r2pipe) (only python)
