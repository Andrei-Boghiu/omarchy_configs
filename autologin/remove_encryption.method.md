# Omarchy Auto-Login (Method 1: Remove Encryption)

## Important Clarification

By default, Omarchy already has auto-login enabled.

This means:

- after the system boots,
- the user is automatically logged in,
- and Hyprland starts automatically.

The password prompt shown at boot is **not** a login screen.

It is the LUKS full-disk encryption prompt.

### Why You Still See a Password Prompt

Omarchy installs with disk encryption enabled by default.

Boot flow:

```text
Power on
→ LUKS encryption password prompt
→ Linux boots
→ SDDM autologins
→ Omarchy starts
→ Hyprland loads
```

The encryption password is required before Linux can access the disk.

## Install Omarchy Without Encryption

This is the simplest method if you want:

- fully automatic boot,
- no password prompt,
- immediate startup into Hyprland.

## Recommended Approach

1. Install Arch Linux manually.
2. Follow the Omarchy manual installation guide.
3. Skip the disk encryption/LUKS setup section entirely.
4. Install Omarchy normally afterward.

Everything else works normally.

## Result

Boot flow becomes:

```text
Power on
→ Linux boots immediately
→ SDDM autologins
→ Omarchy starts
→ Hyprland loads
```

No password required.

---

# Alternative Method

Devices with TPM 2.0 can use automatic TPM-based LUKS unlocking.

This keeps encryption enabled while removing the password prompt.

That setup is documented separately.
