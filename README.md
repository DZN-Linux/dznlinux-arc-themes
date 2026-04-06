# DZNLinux Arc Themes

A collection of 69 color variants of the Arc GTK theme, adapted for DZN Linux. Each variant ships in light, dark, and darker flavors and is applied to GTK 3 applications running in KDE Plasma or other desktop environments.

## Features

- 23 accent colors, each with light, dark, and darker variants (69 themes total)
- Flat design with transparent elements
- GTK 3 support for styling GTK applications within KDE Plasma
- Compatible with KDE Plasma 6.6 on both X11 and Wayland

## Compatibility

- **Desktop Environments**: KDE Plasma 6.6 (primary), Xfce, GNOME
- **Display Server**: X11 and Wayland
- **GTK Version**: GTK 3 apps are fully themed; GTK 4 apps are not styled by these themes (see Troubleshooting)
- **Qt/KDE apps**: Not affected — use Kvantum or Plasma color schemes for Qt theming

## Installation

### Manual Installation

```bash
# Clone this repository
git clone https://github.com/DZN-Linux/dznlinux-arc-themes.git

# Install themes system-wide
sudo cp -r dznlinux-arc-themes/usr/share/themes/* /usr/share/themes/

# Or install for current user only
cp -r dznlinux-arc-themes/usr/share/themes/* ~/.local/share/themes/
```

### Applying the Theme in KDE Plasma

Open **System Settings → Colors & Themes → GTK Theme** and select any `Arc-*` variant.

Alternatively, set it via command line:
```bash
# GTK 3
gsettings set org.gnome.desktop.interface gtk-theme "Arc-Aqua-Dark"
```

Or edit `~/.config/gtk-3.0/settings.ini`:
```ini
[Settings]
gtk-theme-name=Arc-Aqua-Dark
```

## Color Variants

| Accent | Light | Dark | Darker |
|--------|-------|------|--------|
| Aqua | Arc-Aqua | Arc-Aqua-Dark | Arc-Aqua-Darker |
| Blood | Arc-Blood | Arc-Blood-Dark | Arc-Blood-Darker |
| Botticelli | Arc-Botticelli | Arc-Botticelli-Dark | Arc-Botticelli-Darker |
| Casablanca | Arc-Casablanca | Arc-Casablanca-Dark | Arc-Casablanca-Darker |
| Crimson | Arc-Crimson | Arc-Crimson-Dark | Arc-Crimson-Darker |
| Emerald | Arc-Emerald | Arc-Emerald-Dark | Arc-Emerald-Darker |
| Evopop | Arc-Evopop | Arc-Evopop-Dark | Arc-Evopop-Darker |
| Fire | Arc-Fire | Arc-Fire-Dark | Arc-Fire-Darker |
| Froly | Arc-Froly | Arc-Froly-Dark | Arc-Froly-Darker |
| Havelock | Arc-Havelock | Arc-Havelock-Dark | Arc-Havelock-Darker |
| Hibiscus | Arc-Hibiscus | Arc-Hibiscus-Dark | Arc-Hibiscus-Darker |
| Mandy | Arc-Mandy | Arc-Mandy-Dark | Arc-Mandy-Darker |
| Mantis | Arc-Mantis | Arc-Mantis-Dark | Arc-Mantis-Darker |
| Niagara | Arc-Niagara | Arc-Niagara-Dark | Arc-Niagara-Darker |
| Numix | Arc-Numix | Arc-Numix-Dark | Arc-Numix-Darker |
| Orchid | Arc-Orchid | Arc-Orchid-Dark | Arc-Orchid-Darker |
| Paper | Arc-Paper | Arc-Paper-Dark | Arc-Paper-Darker |
| Pink | Arc-Pink | Arc-Pink-Dark | Arc-Pink-Darker |
| Polo | Arc-Polo | Arc-Polo-Dark | Arc-Polo-Darker |
| Punch | Arc-Punch | Arc-Punch-Dark | Arc-Punch-Darker |
| Smoke | Arc-Smoke | Arc-Smoke-Dark | Arc-Smoke-Darker |
| Tacao | Arc-Tacao | Arc-Tacao-Dark | Arc-Tacao-Darker |
| Tory | Arc-Tory | Arc-Tory-Dark | Arc-Tory-Darker |

## File Structure

```
usr/share/themes/Arc-<Color>[-Dark|-Darker]/
├── index.theme        # Theme metadata
├── gtk-3.0/
│   ├── gtk.css        # Main GTK 3 stylesheet (imports from gtk.gresource)
│   ├── gtk-dark.css   # Dark variant stylesheet
│   └── gtk.gresource  # Compiled GTK 3 theme resources
├── gtk-2.0/           # GTK 2 support (legacy apps)
├── metacity-1/        # GNOME Metacity window decorations
├── openbox-3/         # OpenBox window manager
├── xfwm4/             # Xfce window manager
├── plank/             # Plank dock
└── unity/             # Ubuntu Unity
```

## License

Licensed under the GNU General Public License v3.0 or later (GPL-3.0-or-later).

See [LICENSE](LICENSE) file for details.

## Credits

- Original Arc theme: horst3180
- Color variants generated with [Arc-Theme-Colora](https://github.com/erikdubois/Arc-Theme-Colora) by erikdubois
- DZN Linux adaptation: Seth Dawson

## Links

- GitHub: https://github.com/DZN-Linux/dznlinux-arc-themes
- DZN Linux: https://github.com/DZN-Linux
- Arc Theme upstream: https://github.com/jnsh/arc-theme

## Troubleshooting

### GTK 4 apps are not themed

These themes target GTK 3. GTK 4 applications (and apps using libadwaita) use a separate styling API and will not pick up Arc themes. This is a known limitation of all Arc-based theme collections. GTK 4 apps in KDE Plasma 6.6 will render using their built-in defaults.

### Theme not listed in KDE System Settings

Verify themes are in the correct location:
```bash
ls /usr/share/themes/ | grep Arc
# or
ls ~/.local/share/themes/ | grep Arc
```

### GTK apps ignore the theme on Wayland

Ensure KDE's GTK integration portal is running:
```bash
systemctl --user status xdg-desktop-portal-kde
```

If GTK apps still don't pick up the theme, set it explicitly in `~/.config/gtk-3.0/settings.ini`.

### Theme looks incorrect in specific apps

Check SDDM logs for errors:
```bash
journalctl --user -b | grep gtk
```

Some apps override the system theme. Check the app's own preferences for a theme or appearance setting.
