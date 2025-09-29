[中文](./README_CN.md)

# org-workbench

A digital card workbench system for org-mode, providing a powerful tool for organizing and managing your notes. 

Compatible with org-mode, and pakages that support the ID system, such as org-supertag, org-roam, org-brain, etc.

## Overview

![org-workbench](./assets/figure-1.gif)

org-workbench provides a digital card system that simulates a traditional physical card workbench, allowing you to organize and rearrange your org-mode notes in a digital environment. It's perfect for research organization, writing projects, and argument structure building.

## Why use org-workbench?

Imagine you're writing a paper or working on a research project. You have many notes scattered across different org files, and now you need to reorganize this content into a logically clear structure.

**Problems with traditional approaches:**
- Reorganizing directly in the original files would destroy the existing structure
- Frequently switching between multiple files can cause loss of context
- Need to consider complex hierarchical relationships, making operations cumbersome

**org-workbench's solution:**
- Create a "workbench" and extract all related content as cards
- Experiment with different arrangements in a safe environment without affecting the original files
- All cards are at the same level, making moving and reorganizing very simple
- Can quickly jump back to the original file for editing while maintaining synchronization

Simply put, org-workbench gives you a digital "card workbench" that lets you easily reorganize your notes like you would with physical cards.

## Features

- **Digital Card System**: Create cards from any org-mode heading
- **Multiple Workbenches**: Create separate workbenches for different projects or topics
- **Persistent Storage**: All workbench states are automatically saved and restored across sessions
- **Visual Interface**: Clean org-mode outline with efficient navigation
- **Card Operations**: Add, remove, and organize cards with intuitive commands
- **Smart ID System**: Automatically enables enhanced features when org-supertag, org-brain, or org-roam are detected
- **Enhanced Features**: Sync cards with source files and jump to original locations (when ID system is enabled)
- **Export to Org-links**: Export all cards in a workbench as a list of `org-link`s to a new buffer.
- **Backward Compatibility**: Works seamlessly with existing org-luhmann setups

## Display Format
The workbench uses org-mode structure to display cards, breaking the original level structure to make it easier to move and reorganize cards:

```
Workbench: default (5 cards)
════════════════════════════════════════════════════════════

1 Test Card 1
This is the content of the first test card.
Contains some text content for testing workbench functions.

1a Test Branch Card
This is the content of the branch card.

1a.1 Subheading 1
Content of subheading 1.

1a.2 Subheading 2
Content of subheading 2.

1a.2.1 Deeper Subheading
Content of deeper subheading.

2 Test Card 2
This is the content of the second test card.
```

Note: Stars are completely hidden, but all org-mode features are preserved. All cards are at the same level, making it easy to move and reorganize them.

## Installation

### With use-package and straight.el

```elisp
(use-package org-workbench
  :straight (:host github :repo "yibie/org-workbench")
  :after org-supertag ; or org-roam, org-brain, etc.
  :config
  (org-workbench-setup))
```

### Manual Installation

1. Download `org-workbench.el` to your load-path
2. Add to your init file:

```elisp
(require 'org-workbench)
(with-eval-after-load 'org-supertag ; or org-roam, org-brain, etc.
  (org-workbench-setup))
```

## Usage

### Basic Commands

#### Adding Cards

**Add Entire Subtree (Recommended)**
`M-x org-workbench-add-subtree`
1. Place the cursor on any heading 
3. All headings in the subtree will be extracted as individual cards

**Add Only the Current Heading**
`M-x org-workbench-add-heading`
1. Place the cursor on any heading
2. Press `C-c l h`
3. Only the current heading is added, excluding its subheadings and content

#### Managing Workbenches
`M-x org-workbench-manage`
- Create new workbenches for different projects
- Rename or delete existing workbenches
- Switch between workbenches easily

#### Card Operations in Workbench

- **Move Cards**: `M-↑`/`M-↓` to move cards up/down 
- **Navigate**: `n`/`p` or `C-n`/`C-p` to move between cards
- **Remove Cards**: `C-c C-k` to remove current card
- **Clear Workbench**: `C-c w c` to clear all cards
- **Refresh**: `g` to refresh the display

#### Enhanced Features (when ID system is enabled)

- **Jump to Source**: `RET` to jump to the original location of the card
- **Sync Single Card**: `C-c s c` to sync current card with its source
- **Sync All Cards**: `C-c s a` to sync all cards with their sources
- **Export Links**: `C-c C-e` (`M-x org-workbench-export-links`) to export all card links to a new buffer.

## Configuration

### Card Content Length
```elisp
(setq org-workbench-card-content-length 500)
```

### ID System

```elisp
;; Enable/disable ID system
(setq org-workbench-enable-id-system t)
```
org-workbench can operate in two modes:
- **Without IDs**: You get a basic workbench for visually rearranging cards.
- **With IDs (Recommended)**: By enabling `org-workbench-enable-id-system`, you unlock all enhanced features like jumping to source, syncing content, and exporting links. For this to work, your org headings need to have `ID` properties, which can be easily added via `M-x org-id-get-create`.

For the best experience, it is highly recommended to use an ID-based workflow.

## Use Cases

### 1. Research Project Organization
- Add related research notes to the workbench
- Arrange cards in logical order
- Quickly jump to the original notes for editing

### 2. Writing Project Planning
- Collect parts of the writing outline
- Rearrange chapter order
- Quickly access reference materials during writing

### 3. Argument Structure Building
- Add arguments and evidence as cards
- Experiment with different argument orders
- Build a logically clear argument structure

### 4. Temporary Note Collection
- Create a temporary collection for specific topics
- Quickly switch between different projects
- Keep the workspace clean

## Technical Details

### Data Storage
- All workbench states are saved in the file specified by `org-workbench-save-file`
- Data is stored in Emacs Lisp format
- All workbenches are automatically loaded when `org-workbench-setup` is executed

### Card Information
Each card contains:
- `:id`: Unique ID (when ID system is enabled)
- `:number`: Luhmann number
- `:title`: Full title
- `:content`: Truncated content (for display)
- `:level`: Level of the original title
- `:file`: Original file path



## License

This project is licensed under the MIT License.

## Author

Yibie (yibie@outlook.com)

## Related Projects

- [org-supertag](https://github.com/yibie/org-supertag) - Super tagging system for org-mode
- [org-luhmann](https://github.com/yibie/org-luhmann) - Luhmann numbering system for org-mode 

