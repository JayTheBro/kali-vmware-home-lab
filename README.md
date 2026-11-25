# kali-vmware-home-lab
# Kali Linux & VMware Workstation Home Lab

## Overview
Setup notes and troubleshooting log for running Kali Linux inside VMware Workstation Pro on a Windows host. I built this environment as an isolated sandbox for packet capture, vulnerability scanning, and upcoming security coursework.

## Environment Specs
* **Host OS:** Windows (x64)
* **Hypervisor:** VMware Workstation Pro
* **Guest OS:** Kali Linux (Pre-built VMware 64-bit Image)
* **Hardware:** AMD Ryzen CPU on a Gigabyte UEFI Motherboard

## Setup Process
1. **Hypervisor & Image Prep:** Installed VMware Workstation Pro and unpacked the pre-built Kali Linux `.7z` archive with 7-Zip.
2. **Hardware Virtualization:** Enabled **SVM Mode (AMD-V)** in the Gigabyte UEFI BIOS under `Tweaker > Advanced CPU Settings` so the board would allow 64-bit guest execution.
3. **Initial Boot & Credentials:** Opened the `.vmx` file, logged in with the default Kali credentials, and immediately changed the user password using `passwd`.
4. **Guest Integration:** Checked `open-vm-tools-desktop` and display acceleration settings to get window scaling working properly.

## Issues Hit & Fixes
* **AMD-V Disabled on Boot:** VMware refused to power on the 64-bit image until I turned on `SVM Mode` in the motherboard firmware and confirmed `Virtualization: Enabled` inside Windows Task Manager.
* **Invisible Guest Cursor (Open):** The mouse pointer disappears inside the VM window after booting. Still troubleshooting input capture and 3D acceleration settings for this.

## Next Steps
* Fix the invisible guest cursor issue inside VMware.
* Save a clean baseline VM snapshot before installing extra packages or running lab exercises.
* Configure host-only and NAT networking to spin up a vulnerable target machine for isolated traffic analysis.
