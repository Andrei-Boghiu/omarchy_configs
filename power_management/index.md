# Prevent Sleep and Screen Saver

## Disable Suspend and Hibernate

Prevent the system from sleeping entirely:

```bash
sudo systemctl mask sleep.target suspend.target hibernate.target hybrid-sleep.target
```

Verify:

```bash id="1d67za"
systemctl status sleep.target suspend.target hibernate.target hybrid-sleep.target
```

Expected:

```text
Loaded: masked
```

All should appear masked or inactive.

## Re-enable Sleep Later

```bash id="7h0n2v"
sudo systemctl unmask sleep.target suspend.target hibernate.target hybrid-sleep.target
```

---

## Disable Screen Saver in Hyprland / Wayland

If running Omarchy desktop with Hyprland:

Edit:

```bash
sudo nvim ~/.config/hypr/hypridle.conf
```

Disable or remove timeout listeners.

Example minimal config:

```ini
general {
    lock_cmd = pidof hyprlock || hyprlock
}

listener {
    timeout = 0
}
```

Then restart:

```bash
systemctl --user restart hypridle
```
