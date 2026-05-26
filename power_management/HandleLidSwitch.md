# Ignore Laptop Lid Switch

This prevents the laptop from suspending, hibernating, or shutting down when the lid is closed.

---

## Edit systemd-logind Configuration

Open the configuration file:

```bash
sudo nvim /etc/systemd/logind.conf
```

Find or add the following lines:

```ini
HandleLidSwitch=ignore
HandleLidSwitchExternalPower=ignore
HandleLidSwitchDocked=ignore
```

---

## Restart logind Service

Apply changes:

```bash
sudo systemctl restart systemd-logind
```
