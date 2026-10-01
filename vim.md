# tOS-Lite Exclusive Vim User Manual

This manual is a guide for using Vim (vimrc.local) in the tOS-Lite environment, which is optimized for embedded AI model lightweighting and real-time predictive inference education. To minimize memory usage (180MB) and protect the SD card's lifespan, all temporary files are processed in a RAM disk (tmpfs), and features specialized for Python development are built-in by default.

## Basic UI and Editor Environment
- Theme and Colors: Highly readable Gruvbox (Dark) theme and bottom Airline status bar are applied.
- Relative Number: Line numbers are displayed relative to the current cursor position. Very useful for quick cursor movements such as 10j (move down 10 lines) or 5k (move up 5 lines).
- Code Indent and Brackets
  - Indent is automatically set to 4 spaces.
  - Vertical indent lines (|, ¦) are displayed to easily identify Python blocks.
  - When typing an opening bracket, the closing bracket is auto-completed, and rainbow colors (vim-rainbow) are applied to each bracket pair for easy code analysis.
- Auto-clean function: Trailing whitespace at the end of the code is automatically removed every time the file is saved, and when the file is reopened, the cursor automatically returns to its previous working position.

## Window Splitting and Terminal Movement
Shortcut keys are configured to conveniently split the screen and use the terminal within Vim without a terminal multiplexer (like tmux) in an SSH remote connection environment.

Function | Shortcut (Normal Mode) | Shortcut (Terminal/Insert Mode)
-----|------------------|---------------------------
Split Window (Horizontal) | `:split` | -
Split Window (Vertical) | `:vsplit` | -
Move Window (Left) | `Ctrl + h`, `Alt + h` | -
Move Window (Down) | `Ctrl + j`, `Alt + j` | -
Move Window (Up) | `Ctrl + k` | `Alt + k`
Move Window (Right) | `Ctrl + l` | `Alt + l`
Open Built-in Terminal | `:term` | -
Exit Terminal Mode | - | `Esc`

> Tip: By entering `:term` after `:vsplit`, you can code and monitor the system simultaneously with the terminal placed next to the editor. The terminal's scrollback buffer is generously set to 100,000 lines.

## Features Specialized for Python Development and Debugging
Shortcut keys are mapped to immediately execute and debug Python code written on the Raspberry Pi. (The `<Leader>` key used in shortcut combinations is the comma (`,`).)

Function | Shortcut | Description
-----|-------|----------
Execute Python Code | `,` then `r` | Saves the Python file currently being edited and executes it immediately.
Toggle Debug Breakpoint | `F6` | Inserts or deletes the Python 3 standard debugger `breakpoint()` code on the current line.
Fold/Unfold Code | `Space` | Folds or unfolds the code in class or function block units. (SimpylFold applied)

## Search and Multi-Cursor

Function | Shortcut | Description
-----|--------|---------
Search Word | `/search_term` | Searches case-insensitively, but strictly matches case only when uppercase letters are entered (Smartcase).
Turn off Search Highlight | `Esc` twice | Immediately clears the yellow highlight remaining on the screen after the search is completed.
Select Multi-Cursor | `Ctrl + n` | Pressing while the cursor is over a word selects the word, and continuously pressing creates additional cursors on the next identical words, allowing simultaneous editing. (vim-visual-multi)

## SD Card Protection and File Volatility Guide
tOS-Lite saves all Vim temporary files (`.swp`, backup files, undo logs, command history) in RAM (`tmpfs`, `/var/lib/tos/vim`) rather than a physical disk to increase the SD card lifespan of the educational board and prevent I/O bottlenecks.

- Impact: Rebooting the Raspberry Pi resets the history of previously searched words or Vim internal commands like `:wq`.
- Advantage: Even if the board's power is suddenly cut off or an error occurs during work, messy temporary files (`.filename.swp`) do not remain in the user's home folder (Workspace) causing conflicts, ensuring a clean practice environment at all times. (However, the code saving itself is normally reflected on the physical disk.)
