**Software Requirements Specification (SRS)**  
This document was last updated on **February 02, 2026**.

# 🐝 Bee’s Power Media (BPM)
## Software Requirements Specification (SRS)

**Document Status:** Draft  
**Target Release (MVP):** 01 Mar 2026  
**Author / Owner:** Badar Jamal  

---

## 1. Introduction

Ever wanted to cut a portion of a video you’re watching and save it to your Saved Videos collection or share it with someone? This Windows app lets you do that.

The first version v0.10 (MVP) will offer functionality for a common media management scenario: cutting portions of media files without re-encoding, with an option to select the target container (MKV, mp3, etc.) 

This version will primarily validate:

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
| v0.20 | Project saving, row sorting, skins/themes, wide codec & quality support |

---

## 6. Core Functionality

BPM aims to offer functionality that seems basic but is either scattered across different media-cutting tools or not available at all. The following table details the features and the version they will be implemented in. MPV = v0.01

### 6.1 Media Processing

| Feature | Description | Implementation |
|----|----|----|
| Cut Portion | Cutting the desired portion by entering start and end time | v0.10 |
| Copy Streams | Lossless and extremely fast stream copying | v0.10 |
| Subtitle Handling | Cut subtitle streams along with media | v0.10 |
| Stream Selection | Select audio/subtitle streams to include or exclude | v0.10 |
| Queue | Superior user experience with queue-based batch processing | v0.10 |

### 6.2 Three Panel Layout

The application uses a **three-pane layout**
| Feature | Description | Implementation |
|----|----|----|
| File Navigator Pane | Similar to Windows File Explorer, will let users add files to the Working Files pane | v0.10 |
| Working Files Pane | Files organized in a spreadsheet-like view, with rows representing files and columns representing selectable settings or action buttons. The user will add files here, choose settings, and add them to the queue. This pane will include a collapsible Preview/MediaInfo sub-pane | v0.10 |
| Queue Pane | This will also have a spreadsheet-like view, this will contain the files, along with user-selectable settings, ready to be processed | v0.10 |

### 6.3 The Spreadsheet-like Interface

In addition to a streamlined interface, a spreadsheet-like interface will enable some advanced features not found in current such tools. 

| Feature | Description | Implementation |
|----|----|----|
| Drag Handle | When a user selects a **cell**, it will offer a drag handle in the bottom-right corner, which you can drag to rows above or down to copy the setting to target cells, similar to a spreadsheets. For example, if a cell contains file name, e.g. Video 01.mp4, and the user drags it to five rows down, the file name will be changed to Video 01.mp4 for all five rows. Additionally, an Auto Fill Options button will appear with two primary options: Copy Cells and Fill Series. Other options can be added if required. | v0.10 |
| Column Resize | The columns will be resizable, like a spreadsheet column | v0.10 |

---

## 7 Planned Features for v0.20

| Feature | Description | Implementation |
|----|----|----|
| Save Project | The program will show a Save Project dialogue box if a user adds files to the Working Files pane or takes any other action. The dialogue box will also appear if a user opens an existing project and makes any changes. | v0.20 |
| Sort by Columns | Columns will have the option to sort ascending, descending, and user defined. The user defined will be the order by which the files were added or rearranged by the user. | v0.20 |
| Rearrange Columns | Does it make sense to allow dragging and rearranging columns as well :question: | v0.20 |
| Skins | The program will be developed to support skins, which will support not only changing the color scheme but also the compactness of the interface and the look of buttons and other components. For example, it will be possible to design a skeuomorphic skin. | v0.20 |

---

## 8 Component Descriptions

### 8.1 Main Toolbar

The main toolbar will be positioned in the uppermost space, above the panes. It will contain the logo and program name on the right and buttons on the left.

| Button | Description | Implementation |
|----|----|----|
| Save Project | Saves the project that includes the state of the all three pans. The project will be saved as bpmx files with (.bpmx) extension. A project will save the following:
1. Explorer Pane: Folder and files selected in the Explorer pane.
2. Working Files Pane: Files added to the Working Files pane along with the settings the user has modified for any row.
3. Queue Pane: Files added to the Queue pane along with the settings the user has modified for any row. | v0.20 |
| Load Project | Loads a saved project | v0.20 |
| ⚙️No name | Gear icon for settings. I have not decided what these settings should be. | v0.20 |
| ❔ No name | Help icon for help. Takes to the online help webpage. If we ever decided to integrate an AI agent, it will open the agent pane. | v0.20 |

### 8.2 File Explorer Pane 

Similar to the Navigation Pane (left pane) of the standard Windows File Explorer, this pan will show folders. In contrast to Windows File Explorer, however, it will also show file in the folders and all folders and files will have a checkbox on the left side of their icons. When a user checks the checkbox of a folder, all the files in the folder will be checked. If a folder has partial selection (some files in the folder are checked while others are not), the checkbox for the folder will show a partial selection (a horizontal line or a small square). The File Explorer pane will also have expand/collapse chevrons (arrows) similar to Windows File Explorer Navigation Pane. 

The user will be able to drag files to the Working Files pane. When a user drags folders/files from the File Explorer pane, all other panes will become blurred and the Working Files pane will change into a drop file zone. 

A related aspect: Users can drag files from Windows File Explorer to the BPM window. When a user drops files in the BPM window, all panes (including the File Explorer pane) will become blurred and the Working Files pane will change into a drop file zone. 

### 8.3 File Explorer Toolbar

| Button | Description | Implementation |
|----|----|----|
| Add to Working Files (2) | This button will show the number of selected files in parentheses e.g. (2). When clicked, the files checked in the Explorer pane will be added to the working files pane. | v0.10 |

### 8.4 Working Files Pane

| Column Title | Type | Details | Implementation |
|----|----|----|----|
| ⠿ No name | Drag Handles | Six dots as drag handles | v0.10 |
| Source Media | Text string | With file name (Vacation_sum....MKV) Three dots before file extension show truncation, in case the whole name does not fit in the current column width.

In the same row, below the file name, file path will be shown (C:\Users\Michael\Videos\Vac...). Again, truncation will only be used if the file path does not fit in the column width.

**Optional**: The text string will be editable. There will be a small button titled Rename next to the file name. Clicking on the file name or the Rename button will enable the user to type a new name excluding extension. As soon as the user starts typing, the button will change from Rename to Save. Clicking the Save button or pressing the Enter key will rename the file. If the user clicks outside the fields, a dialogue box will appear offering two options: Rename; Don’t Rename.  | v0.10 |
| Output Format | Dropdown Menu | This column will show a dropdown menu with a list of all supported output formats (containers) categorized by Video and Audio. | v0.10 |
| Select Streams | Checkbox | A checkbox. Unchecked means that all streams will be copied. When checked, it will show sub-rows below, one for each video, audio, and subtitle stream. Each sub-row will have checkboxes as well, allowing the user to select which streams they want to be copied in the output. Unchecked streams will not be copied.
Additionally, a dropdown will be shown for each sub-row with the option to set the stream as default. For example, if a video has two audio or subtitle streams, this option will enable the user to choose the default audio and subtitle stream. | v0.10 |
| Start Time | Time input | It will show start position of the media cut in HH:MM:SS format. The default will be 00:00:00. The user will be able to click into the HH, MM, or SS position. The colon (:) will be grayed out and the user don't need to interact with it. For example, if a user clicks the MM position, both MM values will be highlighted, ready to edit. And when the user enters 2531, the start time will change to 25:31 (25 minutes and 31 seconds).  | v0.10 |
| End Time | Time input | It will show start position of the media cut in HH:MM:SS format. The default will be The total duration of the media file. For example a two-hour and 55 minute video file will display 00:02:55. Editing process will be the same as the Start Time column. | v0.10 |
| Add to Queue | Button | An Add to Queue button for each main row (excluding sub-rows) that will add the file to the Queue pane below already added files. | v0.10 |
| Remove File | Icon | ❎ This will show a small X icon. The icon will turn from white/yellow to red on hover and will remove the file from the pane when clicked. | v0.10 |

### 8.4 Working Files Toolbar

| Button | Description | Implementation |
|----|----|----|
| Add Files | Opens standard File Explorer window to browser local folders and files. | v0.10 |
| Add Selected to Queue (2) | Will add the files selected (checked) in the Working Files pane to the Queue pane. (2) shows the number of currently selected (checked) files. | v0.10 |
| Clear | Unselects all selected files (Clears all the checkmarks) | v0.10 |

### 8.5 Queue Pane

| Column Title | Type | Details | Implementation |
| ⠿ No name | Drag Handles | Six dots as drag handles | v0.10 |
| Target File | Text string | With file name (Vacation_sum....MKV) Three dots before file extension show truncation, in case the whole name does not fit in the current column width.

In the same row, below the file name, file path will be shown (C:\Users\Michael\Videos\Vac...). Again, truncation will only be used if the file path does not fit in the column width.

Optional: The text string will be editable. There will be a small button titled Rename next to the file name. Clicking on the file name or the Rename button will enable the user to type a new name excluding extension. As soon as the user starts typing, the button will change from Rename to Save. Clicking the Save button or pressing the Enter key will rename the file. If the user clicks outside the fields, a dialogue box will appear offering two options: Rename; Don’t Rename (Keyboard shortcuts: Enter; Esc).
Additionally, next to the file path, there will be a small Change button. Clicking it will open the standard File Explorer dialogue box, allowing the user to select the output folder. The user can directly edit the path, and in this case, the browser button will change to Save. Clicking the Save button or pressing the Enter key will confirm the output folder. If the user clicks outside the fields, a dialogue box will appear offering two options: Change Folder; Don’t Change Folder (Keyboard shortcuts: Enter; Esc). |v0.10 |

### 8.6 Queue Toolbar

| Button | Description | Implementation |
|----|----|----|
| Process Queue | Starts processing the queue. | v0.10 |
| Clear Queue | Deletes all the queue pan rows. | v0.10 |
| Clear Completed | Deletes the rows for completed tasks in the queue pane. | v0.10 |

## 9 User Story

A user is watching a TV serial and wants to cut out their favorite scenes. BPM will enable them to cut the desired portions, without re-encoding, keeping the selected media streams. For example, there is one video stream, two audio streams, and five subtitles. The user can cut the desired portion with only the required video, audio, and subtitle streams. No re-encoding means quick and lossless cutting. In future versions, the program will support re-encoding with a wide range of codecs.

## 10 Out of Scope

For the first version (MVP), the following items are out of scope. 

- Converting codecs (Only supports stream copy without re-encoding)

- Preview with seek functionality (Only supports a static screenshot as a preview)

- Playing media within the app (Launches external media player) 

====================================================================

| Column Title | Type | Details | Implementation |
|  |  |  | v0.10 |
|  |  |  | v0.10 |

| Button | Description | Implementation |
|----|----|----|
|  |  | v0.10 |
|  |  | v0.10 |


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
