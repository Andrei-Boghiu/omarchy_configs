# Dual Boot Detection (Limine)

Limine can automatically detect other EFI boot entries such as Windows.

> Note: First few tries failed due to unknown windows errors or misconfigurations. The only solution that I found was to reinstall windows and run `limine-entry-tool --scan` afterwards.

## Scan For Other Operating Systems

Run:

```bash
sudo limine-scan
```

Or:

```bash
sudo limine-entry-tool --scan
```

This scans EFI boot entries and lets you add them to the Limine boot menu.

---

## Notes

- Useful for dual boot setups with Windows.
- Usually detects `Windows Boot Manager` automatically.
- Reboot after scanning to verify entries appear in Limine.
