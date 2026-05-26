# Run Programs At Startup (Systemd)

Most background services on Arch Linux use systemd.

## Enable A Service At Startup

```bash
sudo systemctl enable SERVICE_NAME
```

Start immediately as well:

```bash
sudo systemctl enable --now SERVICE_NAME
```

---

## Example: Tailscale + SSH

Enable Tailscale at boot:

```bash
sudo systemctl enable --now tailscaled
```

If you plan to access the machine remotely, you probably also want SSH enabled:

```bash
sudo systemctl enable --now sshd
```

Check service status:

```bash
systemctl status tailscaled
systemctl status sshd
```

---

## Disable Startup

```bash
sudo systemctl disable SERVICE_NAME
```

Stop immediately as well:

```bash
sudo systemctl disable --now SERVICE_NAME
```
