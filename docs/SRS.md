**Software Requirements Specification (SRS)**  
This document was last updated on **Janurary 29, 2026** and might not be current. For the current document please visit:
https://consultcrew.atlassian.net/wiki/external/ZjBmNjRhOGJmYjJkNDMwMWIwNTg0NWRkYWQ4MzMwODI

# Bee’s Power Media Manager (BPM)
## Software Requirements Specification (SRS)

**Document Status:** Draft  
**Target Release (MVP):** 01 Mar 2026  
**Author / Owner:** Badar Jamal  
**License:** MIT  

---

## 1. Introduction

Bee’s Power Media Manager (BPM) is a Windows desktop application designed for fast, lossless media cutting. It allows users to cut portions of audio or video files **without re-encoding**, preserving original quality while enabling precise control over media streams.

The MVP focuses on a common but underserved use case: cutting segments of media files and saving them in a chosen container format (e.g., MKV, MP3), while selectively including or excluding audio and subtitle streams.

This version will primarily validate:
- User interface and user experience
- Technical feasibility
- Market demand and future direction

---

## 2. License

This project is open source and distributed under the **MIT License**.

---

## 3. Success Metrics

| Goal | Metric |
|----|----|
| Launch MVP on time | First stable version released by 01 Mar 2026 |
| Usability | A test user with medium technical literacy can cut and convert multiple files without external help |
| Reliability | No major blocking bugs in core functionality |

---

## 4. Assumptions

- Users have **medium technical literacy**
- Users are familiar with common media formats (MP4, MKV, MP3, etc.)
- Users understand basic concepts such as start/end time and media streams
- Users want **fast, lossless** media cutting without re-encoding

---

## 5. Milestones

| Version | Scope |
|----|----|
| v0.10 | Core cutting features, multi-pane UI, spreadsheet-like interface |
| v0.20 | Project saving, sorting, row reordering, quality-of-life improvements |

---

## 6. Core Functionality

### 6.1 Media Processing

| Feature | Description | Planned Version |
|----|----|----|
| Copy Streams (No Re-encoding) | Lossless and extremely fast stream copying | v0.10 |
| Subtitle Handling | Cut subtitle streams along with media | v0.10 |
| Stream Selection | Select audio/subtitle streams to include or exclude | v0.10 |
| Processing Queue | Queue-based batch processing | v0.10 |

---

### 6.2 Application Layout

The application uses a **three-pane layout**:

1. **File Navigator Pane**  
   Similar to Windows File Explorer. Used to browse and add files.

2. **Working Files Pane**  
   Spreadsheet-like view where each row represents a file and columns represent editable settings.  
   Includes a collapsible **Preview / MediaInfo** sub-pane.

3. **Queue Pane**  
   Spreadsheet-like view of files ready for processing with final settings.

---

### 6.3 Spreadsheet-Like Interface Features

- Click-and-drag cell autofill (similar to Excel)
- Auto Fill Options:
  - Copy Cells
  - Fill Series
- Resizable columns
- Row drag-and-drop reordering
- Column sorting (ascending / descending)

---

## 7. Rows & Columns Specification

### 7.1 Working Files Pane

| Column | Type | Description |
|----|----|----|
| Drag Handle | UI control | Rearrange rows |
| Source Media | Text | File name with truncation; file path shown below |
| Output Format | Dropdown | Supported containers, grouped by Audio / Video |
| Select Streams | Checkbox | Expandable sub-rows for video/audio/subtitle streams |
| Start Time | Time input | HH:MM:SS (default: 00:00:00) |
| End Time | Time input | HH:MM:SS (default: total duration) |
| Add to Queue | Button | Adds file to Queue Pane |
| Remove File | Icon | Removes file from Working Files |

**Optional behavior:**  
- File rename (excluding extension) with inline edit and confirmation dialog

---

### 7.2 Queue Pane

| Column | Type | Description |
|----|----|----|
| Drag Handle | UI control | Rearrange rows |
| Target File | Text | Output file name and path |
| Output Folder | Editable path | Changeable via File Explorer dialog |

**Optional behavior:**  
- Inline rename with Save / Cancel
- Inline output folder change with confirmation

---

## 8. Requirements

| Requirement | User Story | Priority |
|----|----|----|
| Intuitive advanced media cutting | A user wants to cut favorite scenes from a TV show without re-encoding, selecting only required audio and subtitle streams | High |

---

## 9. Out of Scope (MVP)

The following are explicitly excluded from the MVP:

- Codec conversion or re-encoding
- In-app media playback
- Seekable preview (static preview only)
- Advanced timeline editing

---

## 10. Design

Design details (UI mockups, interaction flows) are maintained separately and linked from project documentation.

---

## 11. Open Questions

| Question | Answer | Date |
|----|----|----|
| Should column reordering be supported? | TBD | — |

---

## 12. User Stories

| Title | Description | Priority |
|----|----|----|
| — | No user stories finalized yet | — |

---

## 13. Definitions, Acronyms, and Abbreviations

- **SRS** — Software Requirements Specification  
- **FFmpeg** — Media processing library  
- **Copy Streams** — Container conversion without re-encoding  
- **MKV** — Matroska Video format  
- **Codec** — Encoding/decoding algorithm  
- **Bitrate** — Data rate of media  
- **GUI** — Graphical User Interface  

---

## 14. Reference Links

(To be added)
