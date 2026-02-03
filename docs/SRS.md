# 🐝 Bee’s Power Media (BPM)
## Software Requirements Specification (SRS)

**Version:** 1.0  
**Status:** Baseline  
**Last Updated:** 03 Feb 2026    
**Target Release (MVP):** 01 Mar 2026  
**Author / Owner:** [Badar Jamal](https://github.com/badarpm/)  

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
| Save Project | Saves the project that includes the state of all three panes. The project is saved as a `.bpmx` file. A project saves the following:<ol><li>Explorer Pane: Folder and files selected in the Explorer pane.</li><li>Working Files Pane: Files added to the Working Files pane along with modified settings.</li><li>Queue Pane: Files added to the Queue pane along with modified settings.</li></ol> | v0.20 |
| Load Project | Loads a saved project | v0.20 |
| ⚙️ | No text; Gear icon only for settings. Not yet defined. | v0.20 |
| ❔ No name | No text; Help icon only for help. Opens online help. May open AI agent pane in future. | v0.20 |

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
| Source Media | Text string | With file name (Vacation_sum....MKV). Three dots before the file extension indicate truncation if the name does not fit the column width.<br><br>Below the file name, the file path is shown (C:\Users\Michael\Videos\Vac...). Truncation is used only if the path does not fit the column width.<br><br><strong>Optional:</strong> The text string is editable. A small button titled <em>Rename</em> appears next to the file name. Clicking the file name or the Rename button enables editing (extension excluded). Once typing starts, the button changes to <em>Save</em>. Clicking Save or pressing Enter renames the file. Clicking outside opens a dialog with two options: Rename; Don’t Rename. | v0.10 |
| Output Format | Dropdown Menu | Dropdown listing all supported output formats (containers), categorized by Video and Audio. | v0.10 |
| Select Streams | Checkbox | Checkbox. Unchecked means all streams are copied. When checked, sub-rows appear for each video, audio, and subtitle stream, each with its own checkbox. Unchecked streams are not copied.<br><br>Each sub-row also includes a dropdown to mark the stream as default (e.g., default audio or subtitle). | v0.10 |
| Start Time | Time input | Start position of the cut in HH:MM:SS format. Default is 00:00:00. User can click HH, MM, or SS; colons are non-editable. Entering 2531 in MM changes the value to 25:31. | v0.10 |
| End Time | Time input | End position of the cut in HH:MM:SS format. Default is the total media duration (e.g., 02:55:00). Editing behavior matches Start Time. | v0.10 |
| Add to Queue | Button | Adds the file to the Queue pane. Available only for main rows (not sub-rows). | v0.10 |
| Remove File | Icon | ❎ Small X icon. Turns red on hover and removes the file when clicked. | v0.10 |

### 8.5 Working Files Toolbar

| Button | Description | Implementation |
|----|----|----|
| Add Files | Opens standard File Explorer window to browser local folders and files. | v0.10 |
| Add Selected to Queue (2) | Will add the files selected (checked) in the Working Files pane to the Queue pane. (2) shows the number of currently selected (checked) files. | v0.10 |
| Clear | Unselects all selected files (Clears all the checkmarks) | v0.10 |

### 8.6 Queue Pane

| Column Title | Type | Details | Implementation |
|----|----|----|----|
| ⠿ No name | Drag Handles | Six dots as drag handles | v0.10 |
| Target File | Text string | With file name (Vacation_sum....MKV). Three dots before the file extension indicate truncation if the full name does not fit the column width.<br><br>Below the file name, the file path is shown (C:\Users\Michael\Videos\Vac...). Truncation is used only if the path does not fit the column width.<br><br><strong>Optional:</strong> The text string is editable. A small button titled <em>Rename</em> appears next to the file name. Clicking the file name or the Rename button enables editing (extension excluded). Once typing starts, the button changes from <em>Rename</em> to <em>Save</em>. Clicking Save or pressing Enter renames the file. Clicking outside opens a dialog with two options: Rename; Don’t Rename (keyboard shortcuts: Enter; Esc).<br><br>Next to the file path, a small <em>Change</em> button is shown. Clicking it opens the standard File Explorer dialog to select the output folder. The user may also edit the path directly; in this case, the button changes to <em>Save</em>. Clicking Save or pressing Enter confirms the folder. Clicking outside opens a dialog with two options: Change Folder; Don’t Change Folder (keyboard shortcuts: Enter; Esc). | v0.10 |


### 8.7 Queue Toolbar

| Button | Description | Implementation |
|----|----|----|
| Process Queue | Starts processing the queue. | v0.10 |
| Clear Queue | Deletes all the queue pan rows. | v0.10 |
| Clear Completed | Deletes the rows for completed tasks in the queue pane. | v0.10 |

---

## 9 User Story

A user is watching a TV serial and wants to cut out their favorite scenes. BPM will enable them to cut the desired portions, without re-encoding, keeping the selected media streams. For example, there is one video stream, two audio streams, and five subtitles. The user can cut the desired portion with only the required video, audio, and subtitle streams. No re-encoding means quick and lossless cutting. In future versions, the program will support re-encoding with a wide range of codecs.

---

## 10 Out of Scope

For the first version (MVP), the following items are out of scope. 

- Converting codecs (Only supports stream copy without re-encoding)

- Preview with seek functionality (Only supports a static screenshot as a preview)

- Playing media within the app (Launches external media player)

---

## 11 Design

Here is the initial design created in HTML/CSS with the help of claude.ai. You can also [view the HTML code](./BPM-mockup-v42.html) or [render HTML file](https://badarpm.github.io/bees-power-media/BPM-mockup-v42.html).


![Screenshot](./BPM-mockup-v42-Screenshot.png)

---

## 12 Definitions, Acronyms, and Abbreviations

**SRS**: Software Requirements Specification  
**FFmpeg**: Fast Forward Moving Picture Experts Group - media processing library  
**Copy Streams**: Converting container format without re-encoding (lossless)  
**MKV**: Matroska Video format  
**Codec**: Algorithm for encoding/decoding video or audio  
**Bitrate**: Amount of data per second in a media file  
**GUI**: Graphical User Interface  

