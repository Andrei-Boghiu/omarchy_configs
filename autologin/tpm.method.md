# Omarchy TPM2 Auto-Unlock Notes

> Note:
> I did not manage to make this work successfully yet.
> Keeping this file here for future reference and experimentation.

## Goal

Use TPM 2.0 to automatically unlock the LUKS-encrypted disk at boot while keeping encryption enabled.

Expected flow:

```text
Power on
→ TPM2 unlocks LUKS automatically
→ SDDM autologins
→ Omarchy starts
→ Hyprland loads
```

---

## Requirements

- TPM 2.0 support
- `/dev/tpm0`
- `/dev/tpmrm0`
- `systemd-analyze has-tpm2` returns `yes`

---

## TPM Enrollment

```bash
sudo systemd-cryptenroll --tpm2-device=auto /dev/nvme0n1p2
```

Verify:

```bash
sudo systemd-cryptenroll /dev/nvme0n1p2
```

Expected:

```text
SLOT TYPE
0    password
1    tpm2
```

---

## Important Notes

- Keep the password slot enabled.
- BIOS updates or Secure Boot changes may break TPM unlock.
- Omarchy currently appears to rely partly on legacy `cryptdevice=` boot parameters.
- My attempt resulted in an emergency shell during boot.
