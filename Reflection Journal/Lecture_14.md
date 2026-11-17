# JavaFX Project Log — Day 14: Full System QA & Pitch Prep
29/09/2026

---

## Overview: Stepping Away from the Code
Since we finished building out all the core functionality in Session 13, we didn't write any major new code today. Instead, we shifted gears completely toward validation and presentation prep. 

 Up until now, we had been looking at the project strictly as developers. Today was about stepping back and using the app the exact way a normal user would—booting it up, writing notes, saving them, and closing the program. Tying together the base FXML layouts we made in Session 12 with the backend logic from Session 13 allowed us to finally see the complete visual flow from the initial splash screen right into the main notes workspace.

---

## The QA Checklist: What We Tested
A big realization today was that a feature might work fine in isolation, but weird issues only show up when everything has to run together as one complete system. We had to make sure the UI, the FXML controllers, and our Java logic were all talking to each other properly.

Here is the exact sequence we ran through to validate the build:

- [x] **Startup Sequence:** Verified the splash screen, dynamic loading messages, and progress bar animations.
- [x] **Timestamps:** Checked that the "last opened" time updates and displays accurately.
- [x] **Scene Transitions:** Made sure the handoff from the splash screen to the main application window was smooth.
- [x] **Data Persistence:** Tested writing and saving notes, then completely shutting down and relaunching the app to confirm the saved text loaded back in.
- [x] **Edge Cases & Warnings:** Intentionally tried closing the window with unsaved edits to make sure the warning prompt actually catches the user before data is lost.

*Note: These kinds of features—auto-loading old data, state saving, and unsaved-work alerts—are things we take for granted in everyday productivity apps, and testing them showed us how much work goes into preparing real-world software for release.*

---

## Building the Presentation
Once we knew the app was stable, we started putting together our PowerPoint slides. While testing the visual flow, we grabbed clean screenshots of the working screens to use in the deck.

Our main goal for the slides is to cover:
* **The Big Picture:** The core objective of the app and a walkthrough of its features.
* **Under the Hood:** How we structured the FXML files and hooked them up to our Java backend.

---

## Roadblocks & Reflections

### What Clicked Today
Testing the project as a finished product actually helped us understand our own code a lot better. We also realized that giving a good software demo isn't just about showing off a pretty interface—you have to be able to explain *how* the pieces fit together behind the scenes.

### Where We Struggled
1. **Thinking Outside the "Happy Path":** It is easy to test an app when you follow the rules, but it was tricky remembering to test all the random ways a user might break the flow (like editing a note and immediately hitting the close button without saving).
2. **Filtering Technical Details for the PPT:** Organizing the presentation was harder than expected. We had to figure out how to explain our Java and FXML architecture clearly without dumping too much complicated info onto the slides.

---

## Quick Summary (TL;DR)
* **Test the whole system, not just parts:** Individual features aren't truly done until they work together without breaking each other.
* **Check different user scenarios:** Always test edge cases and user mistakes before calling a project finished.
* **Integration is key:** A working JavaFX app relies on smooth communication between the FXML views, controllers, and backend Java code.
* **Balance the presentation:** A solid pitch covers both *what* the software does for the user and *how* it was engineered.
* **Reviewing builds confidence:** Walking through the app from start to finish gave us a much clearer grasp of our own implementation.
