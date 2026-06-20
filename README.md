# aeroport-iso-tool

An automated PowerShell environment provisioning suite designed to ingest retail Microsoft Windows 11 ARM64 installation images and output streamlined, security-adjusted virtual disks configured for immediate use inside the AeroPort core hypervisor.

## Optimization Details

The utility carries out unattended Deployment Image Servicing and Management (DISM) configurations to strip, optimize, and patch the installation image:
* Unmounts and parses standard Windows components (`install.wim` / `boot.wim`).
* Disables analytical OS tracking layers, system telemetry daemons, and unnecessary background cloud applications.
* Relaxes specific exploit mitigation settings (such as Control Flow Guard and Extended Flow Guard) on explicitly flagged execution paths to optimize dynamic instruction translation pipelines.
* Slipstreams native Red Hat VirtIO guest drivers for virtual network cards, storage controllers, and memory balloon engines.
* Automatically registers the `aeroport-guest-agent` compilation assets to deploy and boot as a native Windows system service during the initial Out-Of-Box Experience (OOBE).

## Usage Instructions

1. Download a certified Windows 11 ARM64 retail ISO directly from Microsoft.
2. Launch a PowerShell instance with administrator privileges.
3. Call the build utility script with paths defined:
   ```powershell
   .\provision-image.ps1 -SourceIso "C:\Path\To\windows_11_arm64.iso" -DestinationDir "C:\AeroPortOutput"
