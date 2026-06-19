# aeroport-iso-tool

This repository houses the automated system deployment scripts and imaging tools responsible for generating the streamlined, headless Windows 11 ARM64 installation media required by the AeroPort hypervisor framework.

---

## Functional Overview

The deployment logic relies on native PowerShell configurations and Deployment Image Servicing and Management (DISM) automation engines to construct an unattended installation matrix:
* **UUP Manifest Interrogation:** Pulls and compiles clean deployment packages straight from official update channels.
* **Image Optimization:** Mounts the installation target, permanently strips telemetry modules, diagnostic tracking services, and default enterprise package bloatware to minimize background memory and CPU consumption.
* **Subsystem Pre-Injection:** Packages and registers the compiled user-mode Indirect Display Driver (`aeroport-idd-driver`) and guest binaries directly into the offline image layout.
* **Boot Configuration Modification:** Adjusts the offline Boot Configuration Data (BCD) records to toggle testing signatures on (`bcdedit /set testsigning on`), enabling seamless initialization of custom user-mode components out of the box.

---

## Utilization

Scripts inside this repository are designed to execute within an administrative PowerShell terminal session on a native Windows development machine. The resulting automated ISO target can then be transferred directly to the Mac host layer for orchestration.