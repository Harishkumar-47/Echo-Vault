# Echo-Vault

Data Recovery Web Application
Recover Deleted Files Intelligently with Deep Disk Analysis

A user-friendly Data Recovery Web Application designed to recover deleted files from storage devices using forensic-level scanning techniques. The application supports both filtered recovery (date range, filename, size) and raw disk scanning for complete partition analysis.

The system combines file system analysis and bit-level recovery to retrieve deleted data across multiple file formats and partitions.

Project Overview

Traditional recovery tools are often difficult for non-technical users and provide limited filtering capabilities.

This project solves that problem by providing:

Web-based recovery interface
Intelligent filtering options
Raw partition scanning
File system metadata analysis
Bit-by-bit disk imaging
Multi-format recovery support

Users can recover files using:

Date range filtering
Partial filename search
File size filtering
File extension filtering
Full raw partition scans
Key Features
Smart Recovery

Recover deleted files using:

Date Created
Date Modified
Date Deleted (if metadata exists)
Partial file names
File extensions
File size

Example:

Search:

filename: report
date: 2026-01-01 → 2026-06-01
size: < 50MB

Returns:

report_final.docx
report_old.pdf
Raw Scan Mode

Performs complete disk traversal.

Capabilities:

Sector-by-sector scan
Bit-by-bit imaging
Deep recovery
Partition analysis
Signature-based carving

Useful when:

File table is corrupted
Deleted metadata is unavailable
Entire partitions are damaged
File System Support

Supported partitions:

FAT32
NTFS
exFAT
EXT2
EXT3
EXT4
File Type Recovery

Recover:

Documents:

DOC
DOCX
PDF
TXT
XLSX

Media:

MP3
WAV
MP4
AVI
MKV
JPG
PNG

Archives:

ZIP
RAR

Other:

Binary files
Unknown signatures
Architecture
                    ┌──────────────────────┐
                    │     User Interface    │
                    │     (Web Browser)     │
                    └──────────┬────────────┘
                               │
                               ▼
                    ┌──────────────────────┐
                    │   Web Application     │
                    │ (Flask / FastAPI)     │
                    └──────────┬────────────┘
                               │
          ┌────────────────────┼────────────────────┐
          │                    │                    │
          ▼                    ▼                    ▼

 ┌────────────────┐  ┌────────────────┐  ┌────────────────┐
 │ Metadata Scan  │  │  Raw Disk Scan │  │ File Recovery  │
 │ Search Engine  │  │ Sector Reader  │  │ Export Engine  │
 └──────┬─────────┘  └──────┬─────────┘  └──────┬─────────┘
        │                   │                   │
        ▼                   ▼                   ▼

┌──────────────┐  ┌────────────────┐  ┌─────────────────┐
│ PyTSK3       │  │ Disk Imaging   │  │ Recovery Output │
│ Metadata API │  │ Bit Extraction │  │ Download Files  │
└──────────────┘  └────────────────┘  └─────────────────┘
Recovery Workflow
Start
 ↓
Select Disk / Partition
 ↓
Choose Recovery Mode
 ├── Smart Search
 │      ↓
 │ Apply Filters
 │      ↓
 │ Recover Files
 │
 └── Raw Scan
        ↓
 Scan Entire Partition
        ↓
 Generate Disk Image
        ↓
 Extract Recoverable Files
        ↓
 Download Results
Technologies Used
Backend
Python
Flask / FastAPI
REST API
Digital Forensics
PyTSK3

Python bindings for The Sleuth Kit.

Used for:

Reading file systems
Extracting deleted entries
Metadata recovery
Partition traversal

Install:

pip install pytsk3


Example Use Cases
Recover Accidentally Deleted Files

Search:

Date: Last 30 days
Filename: project

Recover:

project_final.docx
Deep Recovery

Select:

RAW SCAN

Output:

disk_image.dd
recovered/

Future Enhancements
AI-based file prioritization
Cloud backup recovery
Timeline visualization
Duplicate detection
Live scan progress
Distributed recovery engine
GPU accelerated carving
Recovery confidence score
Security Considerations
Read-only scanning
No modification of source disk
Evidence integrity preservation
