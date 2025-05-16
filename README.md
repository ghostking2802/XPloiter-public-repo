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

## Screenshots 

 📸![Screenshot From 2025-04-21 11-54-15](https://github.com/user-attachments/assets/731a69e7-319f-4f86-a582-476f1e19bb46)
![Screenshot From 2025-04-21 11-58-06](https://github.com/user-attachments/assets/c49e8361-d404-4746-9770-d9bbecb1822f)
![Screenshot From 2025-04-21 11-59-25](https://github.com/user-attachments/assets/00dbb13a-dcfc-4a5f-a6c3-ba03a1d9c609)
![Screenshot From 2025-04-21 11-59-45](https://github.com/user-attachments/assets/7cdc5bf4-3666-4cfd-b7b5-d4c3931a5805)
![Screenshot From 2025-04-21 11-59-52](https://github.com/user-attachments/assets/b2cc45c5-c7b5-4286-9e9a-e40cf745fca3)
![Screenshot From 2025-04-21 12-03-09](https://github.com/user-attachments/assets/85a1c6f6-5c4c-47e4-9d94-6cb1c548bbc9)
![Screenshot From 2025-04-21 12-03-25](https://github.com/user-attachments/assets/63bcc605-4f26-440d-a0b8-fbdb5f5df6f8)
![Screenshot From 2025-04-21 12-03-46](https://github.com/user-attachments/assets/6aaa3a55-a1f5-4266-b47e-d61cd9edbe63)
![Screenshot From 2025-04-21 12-03-55](https://github.com/user-attachments/assets/7b8667df-2de5-48c0-a5ba-0e4d838fd9e8)
![Screenshot From 2025-04-21 12-05-32](https://github.com/user-attachments/assets/928cc460-ed0e-4c19-ace6-5d4e6ac6b92f)
![Screenshot From 2025-04-21 12-05-53](https://github.com/user-attachments/assets/729a6a3b-5dce-47b0-9464-b1da6bd9341b)
![Screenshot From 2025-04-21 12-06-14](https://github.com/user-attachments/assets/2bfef53c-bae1-4739-9411-0edf413882b2)
![Uploadin![Screenshot From 2025-04-21 12-06-26](https://github.com/user-attachments/assets/d875a194-c520-4ead-989b-9395b2a9c9a3)
g Screenshot From 2025-04-21 12-06-20.png…]()
![Screenshot From 2025-04-21 12-08-29](https://github.com/user-attachments/assets/ba1ba456-187a-4cde-801a-f5e5d6778347)
![Uploadi![Screenshot From 2025-04-21 12-15-41](https://github.com/user-attachments/assets/62d318cf-73b2-4ad1-a92b-d18c3fe41d5d)
![Screenshot From 2025-04-21 12-08-39](https://github.com/user-attachments/assets/40aa0a24-ad03-46a2-a9d1-d44c0dfcb388)!
[Screenshot From 2025-04-21 12-06-20](https://github.com/user-attachments/assets/1aade45b-b4fd-4f32-b79d-97934ad58e3a)
ng Screenshot From 2025-04-21 12-08-39.png…]()
![Screenshot From 2025-04-21 12-17-08](https://github.com/user-attachments/assets/78653e4b-0ad2-4ee2-85b0-af290892687b)
![Screenshot From 2025-04-21 12-08-39](https://github.com/user-attachments/assets/40aa0a24-ad03-46a2-a9d1-d44c0dfcb388)![Screenshot From 2025-04-21 12-06-20](https://github.com/user-attachments/assets/1aade45b-b4fd-4f32-b79d-97934ad58e3a)

# 💡 Usage Example

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
| Soumabha Majumdar  | Developer & Forensics Lead |
| Prof. Rahul Kamble | Supervisor (NFSU) |

## 📜 License

This project is for educational and law enforcement forensic usage only. Licensed under [Your Preferred License].
