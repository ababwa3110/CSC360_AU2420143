# Lecture 8 Reflection: Group Project Setup, Linear Algebra, Stack vs Queue, JavaFX Mouse Events & Point-in-Circle

**Date:** 01 July 2026

---

## 1. Group Project & GitHub Repository Setup

- GitHub repository to be created for the group project, with access shared across all team members.
- Direct application of earlier Git structure/version control leads to a real collaborative setup.

---

## 2. Matrices & Systems of Linear Equations

- Covered row vectors and column vectors, worked through with a concrete example rather than definitions alone.
- Connected to Maven in a new context: libraries for matrix operations and solving determinants.

| Library | Use |
|---|---|
| Apache Commons Math | General-purpose math operations |
| EJML | Efficient Java Matrix Library |
| ND4J | N-dimensional array/matrix operations |

- Extends Maven's role beyond build automation/dependency management into supporting mathematical computation within Java projects.

---

## 3. Group Project Status (Groups 1 & 2)

- Brief overview of ongoing builds for group one and group two.
- Short segment — gave a general sense of how each team is to approach their project.

---

## 4. Stack vs Queue for Erasing

- Discussed why a stack (LIFO) is used instead of a queue (FIFO) for an erasing/undo-style operation.
- A stack naturally supports undo behavior because the last action pushed is the first one removed.
- A queue's FIFO order doesn't support this kind of reversal in the same way.

---

## 5. JavaFX: Circles, Arrows & Mouse Listeners

- Applied example: right-click draws a circle; circles are connected using arrows.
- Requires mouse listeners to:
  - Detect the click event.
  - Determine coordinates for drawing the circle.
  - Determine coordinates for drawing the connecting arrow.
- Extension of the earlier event listener model into a visual/interactive context.

---

## 6. Point-in-Circle Test

- Determined whether a given point lies inside a circle by revisiting the distance formula between two points.
- Distance formula:
```
  d = sqrt((x2 - x1)^2 + (y2 - y1)^2)
```
- A point lies inside the circle if its distance from the center is less than the circle's radius.
- Connects back to earlier coordinate-based work with squares and triangles — point containment is a natural extension once basic shape/coordinate logic is established.

---

## Summary of Technical Points

- GitHub repo created and shared for the group project, applying earlier Git version-control concepts.
- Row/column vector distinction covered via example; Maven libraries (Apache Commons Math, EJML, ND4J) introduced for matrix/determinant operations.
- Brief status check on group 1 and group 2 project builds.
- Stack (LIFO) preferred over queue (FIFO) for erasing/undo operations due to last-in-first-out ordering.
- JavaFX circle-drawing via right-click, connected by arrows, driven by mouse listener event detection.
- Point-in-circle containment test derived from the distance formula: point is inside if distance from center < radius.
