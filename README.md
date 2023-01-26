# Radare Iaito for Flatpak

Official Radare Iaito Flatpak package.

<a href='https://flathub.org/apps/details/org.radare.iaito'><img width='120' alt='Download on Flathub' src='https://flathub.org/assets/badges/flathub-badge-en.png'/></a>

## Permissions

The only required permissions are for GUI: `wayland`, X11 (`ipc` + `fallback-x11`), `dri`.

### Optional permissions

Some other permissions can be added using [Flatseal](https://flathub.org/apps/details/com.github.tchx84.Flatseal) GUI or via CLI using `flatpak override`.

Some examples are, to allow radare to debug using ptrace:
```
flatpak override --user --allow=devel org.radare.iaito
```

To allow radare plugins to connect to your network or Internet:
```
flatpak override --user --share=network org.radare.iaito
```

To allow some plugins to attach to a usb device:
```
flatpak override --user --device=all org.radare.iaito
```

The optional permissions you might require depends on the plugins you add and the use of it.

To reset back to default required permissions this command can be used:
```
flatpak override --user --reset org.radare.iaito
```

## Special configurations

Since the application folder is readonly it has been enabled the following configurations and paths have been changed:

- Radare 2 configuration: `~/.var/app/org.radare.iaito/config/radare2/`
- Radare 2 data: `~/.var/app/org.radare.iaito/data/radare2/`

## Projects included

List of project URLs of the modules included in this flatpak version of iaito with radare2:

- [iaito](https://github.com/radareorg/iaito)
  - [iaito-translations](https://github.com/radareorg/iaito-translations)
- [radare2](https://github.com/radareorg/radare2)
  - [r2ghidra](https://github.com/radareorg/r2ghidra)
  - [r2dec](https://github.com/wargio/r2dec-js)
  - [r2pipe](https://github.com/radareorg/radare2-r2pipe) (only python)
