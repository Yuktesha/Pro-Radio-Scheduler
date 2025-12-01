# Pro Radio Scheduler v6.4.89

**The Ultimate Offline Radio Automation Tool**

*Designed for personal radio stations, caring gifts for family, and automated broadcasting.*

---

## 📻 What is this?

**Pro Radio Scheduler** is a powerful Python application that generates continuous, professional-grade radio schedules from your local MP3 library. 

Unlike simple "shuffle" players, this tool acts as a **Program Director**:
*   **Visual Scheduling**: Follows a Weekly/Monthly Schedule defined in **ODS (LibreOffice)** or **Excel**.
*   **Mandatory Airtime**: Ensures specific content (like your own recordings) airs for a guaranteed duration every hour via `priority.txt`.
*   **Smart Silence Splitting**: Automatically detects silence in long talk shows (>15 mins) and splits them naturally to insert Ads/Jingles, just like a real radio station.
*   **Dual-Pool Logic**: Keeps specific program folders "pure" while allowing general music to mix in only when configured.
*   **High-Quality Output**: Creates 192kbps Stereo, 44.1kHz merged MP3s (1 hour per file).

---

## ✨ Key Features

### 1. 📅 Professional Scheduling (ODS/XLSX)
*   **Visual Planning**: Use **LibreOffice Calc** or **Excel** to draw your schedule.
*   **Merge Cells**: Visually merge cells (e.g., 10:00-12:00) to define program blocks.
*   **Infinite Cycles**: Auto-detects the cycle length. You can make a 3-day shift schedule or a 31-day monthly calendar.
*   **Auto Template**: One-click generation of a ready-to-use schedule template.

### 2. 🧠 Smart Content Handling
*   **Smart Silence Splitting**: Uses `ffmpeg silencedetect` to find natural breaks in speech. No more cutting sentences in half!
*   **Sequential Playback**: Remembers episode progress (Ep.1 -> Ep.2) across days for story folders.
*   **Priority System**: Guarantees specific content airs for $X$ minutes every hour.

### 3. 🎚️ Audio Engineering
*   **High Quality**: Outputs **192kbps Stereo, 44.1kHz**.
*   **Loudness Normalization**: Automatically balances volume between speech and music.
*   **Station Jingles & Ads**: Dedicated folders for IDs and Advertisements/Promos.

### 4. 🖥️ Modern UX
*   **4K Ready**: DPI-aware UI that looks crisp on high-res screens.
*   **Smart Memory**: Remembers your window size and position.
*   **Text-Based Library**: Copy-paste your folder paths directly. Supports relative paths for portable setups.

---

## 🚀 Installation

1.  **Install Python 3.10+**: [Download Here](https://www.python.org/downloads/)
2.  **Install FFmpeg**:
    *   Download FFmpeg and add it to your system PATH.
    *   *Or* simply place `ffmpeg.exe` in the same folder as the script.
3.  **Run the Script**:
    *   Double-click `pro_radio_v6_4_89.py`.
    *   The script will automatically check and install required libraries (`pandas`, `odfpy`, `openpyxl`) on the first run.

---

## 📂 Folder Structure Guide

To get the most out of the scheduler, organize your folders like this:

### 1. `Station_Jingles` (Recommended)
Place your Station IDs, time checks, or short interludes here.
*   *If missing, the script creates dummy files.*

### 2. `Station_ADs` (Recommended)
Place advertisements or promo spots here. They are inserted intelligently during smart splits.

### 3. `priority.txt` (Advanced Control)
Place this file inside any specific music/story folder to control its behavior.

**Example Content:**
```ini
# Weight (1-10): Chance to be picked in random mode (Default: 5)
weight=8

# Min Minutes: Guaranteed airtime per hour (e.g., 10 mins mandatory)
min_minutes=10

# Max Minutes: Cap airtime per hour
max_minutes=15

# Mode: 1=Scattered (inserted randomly), 2=Continuous (played in a block)
mode=1
```

### 4. `ratio.txt` (Global Vibe)
Place in your root folder to set the Music-to-Talk ratio for random slots.
```text
# Music : Talk
7:1
```

---

## 🗓️ How to use the Schedule File

1.  Click **"Generate Template.ods"** in the app.
2.  Open the file in Excel or LibreOffice.
3.  **Sheet 1 [Schedule]**: 
    *   Columns are Days (Day 1, Day 2...).
    *   Rows are Hours (00:00 - 23:00).
    *   Merge cells to create programs. Write the **Program ID** in the cell.
4.  **Sheet 2 [Config]**:
    *   Map **Program ID** to **Folder Path**.
    *   Set `Is Shared Source?`: "No" protects the folder from random play.
    *   Set `Include Shared Pool?`: "Yes" allows mixing general music into this program.

---

## 📝 License

Open Source (MIT). 
Created with love for radio enthusiasts and families.
