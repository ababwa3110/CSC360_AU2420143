# Lecture 9 Reflection: Headless Systems, CLI vs GUI, SSH, ASCII Trees & Group Project Reviews

**Date:** 03 September 2026

---

## 1. ASCII Tree: Printing vs Drawing (Group 4)

- **Printing** an ASCII tree — purely text-based output.
- **Drawing** an ASCII tree — graphical representation.
- Tradeoffs between the two depend on the target environment and end goal.

---

## 2. Headless Systems

- A headless system operates without a graphical interface or presentation layer.
- No visual layer available — text-based output becomes the only option in this environment.
- Directly explains the earlier emphasis on text-based/ASCII output.

---

## 3. CLI vs GUI

- CLI is often more powerful than a graphical display for direct system interaction.
- Text is the most direct way to communicate with the CPU.

### Remote Access Without a GUI
- Question raised: how to connect to a remote machine with no graphical interface (compared against tools like AnyDesk, which rely on a GUI).
- Answer: **SSH keys** — ties back directly to the earlier SSH lecture.

---

## 4. Constructing a Vertical ASCII Tree

- Structure resembles a file directory: root at the top, indentation used to represent nested files/folders beneath it.

```
root/
├── folder1/
│   ├── file1.txt
│   └── file2.txt
└── folder2/
    └── file3.txt
```

- Conceptually bridges text-based representation and the earlier coordinate-based shape-drawing work — both represent structure, just through different mediums.

---

## 5. Group Project Reviews

### Group 5
- Java program to draw arrows between two lists of strings that share common elements.
- Demonstrates how graphics can make relationships between data points clearer than plain text.

### Group 6
- Custom splash screen built with FXML.
- Broken into sub-tasks: application name, logo.

### Group 7
- JavaFX tree structure:
  - Selecting a folder reveals its children.
  - Selecting a child allows its properties to be edited.
- Additional requirement: object serialization, so the structure persists between sessions.

### Group 8
- Composite progress bar tracking multiple jobs, with cancellation support.
- Ties back to threads — managing multiple simultaneous processes requires proper thread handling.

---

## Summary of Technical Points

- ASCII tree output can be printed (text-only) or drawn (graphical); choice depends on environment/goal.
- Headless systems have no graphical layer, making text-based output the only viable output method.
- CLI offers more direct system control than GUI; text is the most direct interface to the CPU.
- Remote access to a headless machine relies on SSH keys rather than GUI-based remote desktop tools.
- Vertical ASCII trees represent directory structure using a root node and indentation for nested items.
- Group 5: arrow-drawing between related string lists.
- Group 6: FXML-based custom splash screen (name + logo).
- Group 7: JavaFX folder/child tree with editable properties and object serialization for persistence.
- Group 8: composite progress bar with multi-job tracking and cancellation, requiring thread handling.
