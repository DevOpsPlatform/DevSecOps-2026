# Linux File System Hierarchy (FHS) Reference Guide

This comprehensive reference document outlines the **Filesystem Hierarchy Standard (FHS)** for Linux operating systems. The FHS is maintained by the Linux Foundation to ensure a consistent, predictable directory layout across different Linux distributions (e.g., Ubuntu, Fedora, Debian, RHEL).

---

## 📁 1. The Supreme Root Directory

### ` / ` — Root
* **Purpose:** The top-level directory of the entire filesystem. 
* **Details:** Every single file, folder, and mounted storage drive (hard drives, USB sticks, network shares) stems from the root directory. In Linux, there are no drive letters like `C:` or `D:`; everything forms a unified tree from `/`.

---

## ⚙️ 2. System Booting & Configuration

### `/boot` — Bootloader & Kernel Files
* **Purpose:** Contains the essential static files required to boot the operating system.
* **Core Contents:**
  * **Kernel (`vmlinuz`):** The core engine of the operating system.
  * **Initial RAM Disk (`initramfs` / `initrd`):** Temporary root filesystem used during boot.
  * **GRUB:** Bootloader configurations that load the kernel into memory.

### `/etc` — System-Wide Configuration
* **Purpose:** The administrative nerve center holding static configuration files for the entire machine.
* **Core Contents:**
  * `/etc/passwd`: Stores user account data.
  * `/etc/fstab`: Defines how hard drives and partitions automatically mount.
  * `/etc/ssh/sshd_config`: Configures remote access via the SSH protocol.
* **Note:** This directory strictly contains configuration parameters; it does not store binary executable programs.

### `/run` — Volatile Runtime Data
* **Purpose:** Tracks real-time data generated during active system runtimes.
* **Details:** Includes active system daemons, systemd parameters, process ID (`.pid`) tracks, and system locks. This directory resides in RAM and is completely wiped upon system shutdown.

---

## 👥 3. User Directories & Profiles

### `/home` — User Home Directories
* **Purpose:** Personal workspace for regular users on the machine.
* **Details:** A system user named `alex` will have a personal directory at `/home/alex`. This is where individual documents, downloads, and custom configurations (like `.bashrc`) are stored.

### `/root` — Root User Home Directory
* **Purpose:** The private home workspace specifically for the administrative Superuser (root).
* **Details:** Separated from regular `/home` accounts to ensure that administrative configurations remain accessible even if separate storage partitions containing `/home` fail to mount properly.

---

## 💻 4. Executables & Program Binaries

### `/bin` — Essential User Binaries
* **Purpose:** Fundamental command-line utilities accessible to all system users.
* **Key Commands:** `bash`, `ls`, `grep`, `cp`, `mv`.
* **Details:** These are vital tools required for basic operations, even when running the system in emergency single-user repair modes.

### `/sbin` — System Administration Binaries
* **Purpose:** Executables meant primarily for system administrators (root privileges usually required).
* **Key Commands:** `fsck` (filesystem check), `ifconfig` / `ip` (network configurations), `init` (system initialization).

### `/usr` — Userland Programs & Shared Data
* **Purpose:** The primary warehouse where installed software programs, documentation, and libraries are stored by package managers.
* **Core Subdirectories:**
  * `/usr/bin`: Non-essential user commands (installed apps).
  * `/usr/lib`: Shared libraries required by binary executables.
  * `/usr/share`: Architecture-independent shared data (man pages, icons, themes).

---

## 🛠️ 5. Hardware Interfacing & Virtual Files

### `/dev` — Device Files
* **Purpose:** The hardware translation directory where all connected physical components are treated as standard files.
* **Key Concepts:**
  * `/dev/sda` / `/dev/nvme0n1`: Physical hard drives or SSDs.
  * `/dev/null`: The "bit bucket." Any data written here disappears instantly (used to discard unwanted command outputs).
  * `/dev/tty`: Terminal input/output streams.

### `/proc` — Process & Kernel Information
* **Purpose:** A virtual, temporary directory managing the system's memory and active tasks.
* **Details:** Not stored on a hard drive; it is generated dynamically by the Linux kernel in RAM.
  * `/proc/cpuinfo`: Displays hardware processor specifications.
  * `/proc/meminfo`: Provides real-time breakdown of system memory.
  * `/proc/<PID>`: Tracks settings for every individual active process ID.

### `/sys` — Sysfs Hardware Interface
* **Purpose:** An interactive gateway between user spaces and the underlying kernel configurations.
* **Details:** Like `/proc`, this is a memory-resident virtual system. It allows adjustments to live hardware configurations such as network card states (`/sys/class/net/`) or block device parameters (`/sys/block/`).

---

## 💾 6. Variable Data, Caching & Custom Apps

### `/opt` — Optional Add-on Packages
* **Purpose:** Reserved directory for proprietary or third-party isolated software packages.
* **Details:** Applications like standalone `nginx` environments, custom enterprise applications, or standalone development utilities install here so they do not pollute core system libraries.

### `/var` — Variable Data
* **Purpose:** Stores files that are continuously changing in size as the OS functions normally.
* **Core Contents:**
  * `/var/log`: System, security, and application logs.
  * `/var/spool`: Queued operations like printer prints or mail tasks.
  * `/var/cache`: Temporary caching data from package managers or web utilities.

### `/tmp` — Temporary Files
* **Purpose:** A scratchpad folder where programs can create throwaway working logs or session caches.
* **Details:** Files placed in `/tmp` are usually cleared out automatically by the operating system during a system reboot.

---

## 🚀 DevOps Diagnostic Tip

> **Production Downtime? Check `/var/log` First!**
> Statistically, the vast majority of server crashes or configuration errors dump critical debugging details directly into log folders. Check application logs, system status flags (`syslog`), or service-specific streams in `/var/log` to isolate the root cause immediately.

---
*Reference document generated based on standard Filesystem Hierarchy Standard guidelines.*