# Wake-on-LAN on Arch Linux

## Install Wake-on-LAN Utility

Install the `wakeonlan` package using `pacman`:

```bash
sudo pacman -S wakeonlan
```

---

## Find Target MAC Address

On the target machine:

```bash
ip a
```

Look for something similar to:

```text
link/ether aa:bb:cc:dd:ee:ff
```

---

## Create Wake Script

Create a shell script:

```bash
nvim wake-pc.sh
```

Add the following content:

```bash
#!/bin/bash

# Replace with your target machine MAC address
MAC="AA:BB:CC:DD:EE:FF"

wakeonlan $MAC
```

Save the file.

---

## Make Script Executable

```bash
chmod +x wake-pc.sh
```

---

## Run the Script

```bash
./wake-pc.sh
```

This sends a magic Wake-on-LAN packet to the target machine.

---

## Notes

- Wake-on-LAN usually works best over Ethernet.
- BIOS/UEFI must have Wake-on-LAN enabled.
- Some motherboards require:
  - Wake on PCI-E
  - Power on by LAN
  - ErP disabled
