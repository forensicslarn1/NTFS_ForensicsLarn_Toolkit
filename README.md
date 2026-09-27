# NTFS_ForensicsLarn_Toolkit
Windows C++ forensic toolkit for NTFS volume analysis with BitLocker and EFS support. NTFS Analyzer: MFT parsing, file recovery, USN journal BitLocker Module: FVE metadata, decryption, key testing EFS Module: Certificate extraction, masterkey recovery Disk Analyzer: MBR/GPT parsing, partition analysis
NTFS_ForensicsLarn_Toolkit
Build Status

A Windows C++ forensic tool for NTFS volume analysis with BitLocker and EFS support.

⚠️ Disclaimer
This tool is for educational and legitimate forensic purposes only. Always:

Work on copies of evidence (disk images), never originals
Have proper authorization before analyzing any system
Follow forensic best practices (chain of custody, documentation)
Use established forensic tools (EnCase, FTK, Autopsy) for production work
🚀 Quick Start
Build from Source
# Prerequisites: Visual Studio 2019/2022 with C++ workload, CMake 3.15+git clone https://github.com/forensicslarn1/NTFS_ForensicsLarn_Toolkit.gitcd NTFS_ForensicsLarn_Toolkitmkdir buildcd buildcmake -G "Visual Studio 17 2022" -A x64 ..cmake --build . --config Release# Binary location: build\Release\NTFS_ForensicsLarn_Toolkit.exe
Download Pre-built
Download the latest release from the Releases page.

📖 Usage
Interactive Mode
NTFS_ForensicsLarn_Toolkit.exe
Example Session
[nftk]> open C:\forensics\disk_image.dd[nftk]> partitions[nftk]> ntfs 0[nftk]> mft csv C:\output\mft_records.csv[nftk]> deleted[nftk]> recover secret.docx C:\recovered\secret.docx[nftk]> exit
Command Reference
Command	Description
open <path> [live]	Open disk image or live volume
partitions	List all partitions
ntfs [partition#]	Analyze NTFS filesystem
mft [format] [output]	Export MFT (csv/json/raw)
usn [format] [output]	Export USN journal
deleted	List deleted files
extract <file> <output>	Extract a file
recover <file> <output>	Recover deleted file
bitlocker info	Show BitLocker metadata
efs list	List EFS encrypted files
shell	Enter shell mode
help	Show help
🔧 Features
✅ Implemented
MBR/GPT partition parsing
NTFS boot sector analysis
MFT record parsing (resident/non-resident)
File extraction via data runs
Deleted file detection and recovery
BitLocker detection and metadata parsing
EFS encrypted file detection
CSV/JSON export
🚧 In Progress
USN journal parsing
$LogFile analysis
BitLocker password/recovery key testing
BitLocker volume decryption
EFS certificate extraction
EFS file decryption
🏗️ Architecture
┌─────────────────────────────────────┐│         CLI Interface               │├─────────────────────────────────────┤│  Disk Analyzer │ NTFS Analyzer      ││                 │                   ││  BitLocker Module │ EFS Module      │├─────────────────────────────────────┤│      Volume Reader (Abstraction)    ││  ┌─────────────┬─────────────────┐  ││  │ File Image  │  Live Disk      │  ││  └─────────────┴─────────────────┘  │└─────────────────────────────────────┘
📚 References
NTFS Documentation
Microsoft BitLocker Overview
EFS Documentation
Dislocker (BitLocker for Linux)
📄 License
MIT License - see LICENSE file for details.

🤝 Contributing
Contributions welcome! Please:

Fork the repository
Create a feature branch
Submit a pull request
