# Ignore Laptop Lid Switch

This prevents the laptop from suspending, hibernating, or shutting down when the lid is closed.

---

## Edit systemd-logind Configuration

Open the configuration file:

```bash id="01pdwl"
sudo nvim /etc/systemd/logind.conf
```

Find or add the following lines:

```ini id="zh8yl7"
HandleLidSwitch=ignore
HandleLidSwitchExternalPower=ignore
HandleLidSwitchDocked=ignore
```

---

## Restart logind Service

Apply changes:

```bash id="98f1n6"
sudo systemctl restart systemd-logind
```
