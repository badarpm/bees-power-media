**Software Requirements Specification (SRS)**  
This document was last updated on **February 02, 2026**.

# Bee’s Power Media (BPM)
## Software Requirements Specification (SRS)

**Document Status:** Draft  
**Target Release (MVP):** 01 Mar 2026  
**Author / Owner:** Badar Jamal  

---

## 1. Introduction

Ever wanted to cut a portion of a video you’re watching and save it to your Saved Videos collection or share it with someone? This Windows app lets you do that.

The first version (MVP) will offer functionality for a common media management scenario: cutting portions of media files without re-encoding, with an option to select the target container (MKV, mp3, etc.) 

This version MVP) will primarily validate:

- User interface and user experience
- Technical feasibility
- Market demand and future direction

---

## 2. License

This open-source project is distributed under the **MIT License**.

---

## 3. Goals

| Goal | Metric |
|----|----|
| Launch MVP | First stable version released by 01 Mar 2026 |
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
| v0.20 | Project saving, row sorting, skins/themes,  |

---

## 6. Core Functionality

BPM aims to offer functionality that seems basic but is either scattered across different media-cutting tools or not available at all. The following table details the features and the version they will be implemented in. MPV = Version 0.01

### 6.1 Media Processing

| Feature | Description | Implementation |
|----|----|----|
| Copy Streams | Lossless and extremely fast stream copying | v0.10 |
| Subtitle Handling | Cut subtitle streams along with media | v0.10 |
| Stream Selection | Select audio/subtitle streams to include or exclude | v0.10 |
| Queue | Superior user experience with queue-based batch processing | v0.10 |

### 6.2 Three Panel Layout

The application uses a **three-pane layout**
| Feature | Description | Implementation |
|----|----|----|
| File Navigator Pane | Similar to Windows File Explorer, will let users add files to the Working Files pane | v0.10 |
| Working Files Pane | Files organized in a spreadsheet-like view, with rows representing files and columns representing selectable settings or action buttons. This pane will include a collapsible Preview/MediaInfo sub-pane | v0.10 |
| Queue Pane | This will also have a spreadsheet-like view, this will contain the files, along with user-selectable settings, ready to be processed | v0.10 |

### 6.3 The Spreadsheet-like Interface

In addition to a streamlined interface, a spreadsheet-like interface will enable some advanced features not found in current such tools. 

| Feature | Description | Implementation |
|----|----|----|
| Drag Handle | When a user selects a cell, it will offer a drag handle in the bottom-right corner, which you can drag to rows above or down to copy the setting to target cells, similar to the spreadsheets. For example, if a cell contains file name, e.g. Video 01.mp4, and the user drags it to five rows down, the file name will be changed to Video 01.mp4 for all five rows. Additionally, an Auto Fill Options button will appear with two primary options: Copy Cells and Fill Series. Other options can be added if required. | v0.10 |
| Column Resize | The columns will be resizable, like a spreadsheet column | v0.10 |

### 6.4 Planned Features for v0.20

| Feature | Description | Implementation |
|----|----|----|
| Save Project | The program will show a Save Project dialogue box if a user adds files to the Working Files pane or takes any other action. The dialogue box will also appear if a user opens an existing project and makes any changes. | v0.20 |
| Sort by Columns | When you right-click on a column header, it will give you an option to arrange in ascending or descending order. For example, if you right-click on the file name column header, you can arrange all rows in ascending or descending order. | v0.20 |
| Rearrange Rows | The user will be able to drag and rearrange rows. | v0.20 |
| Rearrange Columns | Does it make sense to allow dragging and rearranging columns as well:question: | v0.20 |
| Skins | The program will be developed to support skins, which will support not changing the color scheme but also the compactness of the interface and the look of buttons and other components. For example, it will be possible to design a skeuomorphic skin. | v0.20 |

## 7 Component Descriptions

### Main Toolbar

The main toolbar will be positioned in the uppermost space, above the panes. It will contain the logo and program name on the right and buttons on the left.

| Button | Description | Implementation |
|----|----|----|
| Save Project | Saves the project that includes the state of the all three pans. The project will be saved as bpmx files with (.bpmx) extension. A project will save the following:
1. Explorer Pane: Folder and files selected in the Explorer pane.
2. Working Files Pane: Files added to the Working Files pane along with the settings the user has modified for any row.
3. Queue Pane: Files added to the Queue pane along with the settings the user has modified for any row. | v0.20 |
| Load Project | Loads a saved project | v0.20 |
| No name (Gear icon only) | Settings. I have not decided what these settings should be. | v0.20 |
| No name (Help icon only) | Takes to the online help webpage. If we ever decided to integrate an AI agent, it will open the agent pane. | v0.20 |





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
