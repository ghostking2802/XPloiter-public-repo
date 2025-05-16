
# XPloiter - Crime Scene Digital Evidence Collector

XPloiter is an advanced Python and Bash-powered forensic toolkit tailored for field deployment using Raspberry Pi. It provides a complete GUI-driven and automated system for acquiring, analyzing, and mapping digital evidence from live and static sources at a crime scene.

## 🚀 Overview

XPloiter is designed to streamline the forensic acquisition process directly on-site, minimizing evidence contamination and providing a structured workflow for investigators. It integrates disk imaging, logical extraction, USB forensics, network mapping, and live analysis through a PyQt-based interface, backed by powerful Bash tools.

This solution is optimized for deployment on a Raspberry Pi 4B with a 7-inch touchscreen, running Raspberry Pi OS.

## 🧠 Key Features

### 🔹 Modular Forensic Acquisition
- **Physical Imaging**: Uses `dd` for raw bit-by-bit imaging.
- **Logical Acquisition**: Extracts file system-level data using standard tools.
- **Multi-Imaging**: Parallel imaging of multiple disks via `multi_imaging_tool.sh`.

### 🔹 GUI Frontend
- Built using **PyQt6** (`main.py`, `ui.py`) for touch-friendly interaction.
- Simple interface for selecting forensic operation modules (physical, logical, analysis).

### 🔹 USB Device Analysis
- Detects and logs USB device information using `lsusb`, `udevadm`, and logs them in real-time.
- Triggers notifications for new devices—ensuring all storage evidence is captured.

### 🔹 Disk Fixing Tools
- Auto-corrects partition issues using `fix_partition.sh`.
- Ensures that damaged evidence storage can still be imaged properly.

### 🔹 Live Network Reconnaissance
- `nmapAutomator.sh`: A wrapper for `nmap` with various scan profiles (quick, full, UDP, aggressive).
- Automatically maps connected devices, detects open ports, services, OS, and common CVEs.

### 🔹 Offline Data Carving
- Integrates **PhotoRec** for raw file carving from corrupted or unstructured storage.
- Stores logs in `photorec.log` for post-processing.

### 🔹 Device Mapping & Pinging
- `ping.sh`: Rapidly checks host responsiveness across a subnet.
- Supports network mapping before pulling data over remote protocols (e.g., SSH, FTP).

## 📁 Directory Structure

```
XPloiter/
├── main.py              # Entry point for PyQt GUI
├── ui.py                # GUI layout, signal-slot binding
└── bin/                 # Shell script modules
    ├── XPloiterForensics.sh   # Entry bash script for all acquisition tasks
    ├── fix_partition.sh       # Automated partition fixing
    ├── logical.sh             # File-level acquisition
    ├── multi_imaging_tool.sh  # Parallel disk imaging
    ├── nmapAutomator.sh       # Network enumeration
    ├── physical.sh            # Raw imaging (dd based)
    ├── ping.sh                # Subnet scanner
    └── usb_analysis.sh        # USB info logging
```

## 🛠️ Tech Stack

| Component       | Technology        |
|----------------|-------------------|
| GUI            | Python + PyQt6    |
| Backend Scripting | Bash, coreutils, `dd`, `lsblk`, `nmap`, `photorec` |
| Platform       | Raspberry Pi OS   |
| Storage Logs   | `/home/pi/XPloiterLogs/` (configurable) |

## 🧪 Workflow

1. **Launch** `main.py` to initialize the PyQt GUI.
2. Select a forensic task (e.g., physical imaging).
3. Internally, the GUI invokes the corresponding script in `bin/` using `subprocess`.
4. Logs and output files are generated and saved for later analysis.
5. USB insertion triggers auto-detection and logs metadata.
6. Live network mapping can be executed via `nmapAutomator.sh`.

## 🛡️ Forensic Best Practices Followed

- **Read-only Imaging**: Physical imaging scripts avoid writing to source devices.
- **Write Blocking**: Can integrate external USB write-blockers.
- **Logging**: Every operation is logged with timestamps.
- **Chain of Custody**: Device IDs, mount points, and hash logs are maintained.

## 📸 Screenshots (Add these on your GitHub)
- Home GUI Interface
- Imaging In-Progress
- Network Scan Output
- USB Device Detection Log

## 💡 Usage Example

```bash
python3 main.py
```

From GUI:
- Click "Physical Imaging" → Select disk `/dev/sda` → Output as `case123.raw`

Or from CLI:
```bash
bash bin/physical.sh /dev/sda case123.raw
```

## 🔐 Future Enhancements

- 📦 Integrate TSK (`fls`, `icat`) for logical acquisition.
- 📊 Include graphical report generation in HTML/PDF.
- 🔌 Add remote SSH imaging support.
- 📡 Incorporate anomaly detection in captured traffic using AI models.
- 🔍 Real-time integrity checks using hash comparison.

## 🧑‍💻 Contributors

| Name              | Role                  |
|-------------------|-----------------------|
| Your Name         | Developer & Forensics Lead |
| Prof. Rahul Kamble | Supervisor (NFSU) |

## 📜 License

This project is for educational and law enforcement forensic usage only. Licensed under [Your Preferred License].
