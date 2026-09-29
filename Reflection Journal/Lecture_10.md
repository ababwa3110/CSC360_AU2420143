# Reflection: 8 September 2026

## Topics Covered

1. Assessment structure and prescribed textbooks
2. Exceptions, assertions, logging (Core Java Vol. I, Ch. 7)
3. Generic programming (Ch. 8)
4. Component model and event handling (Ch. 10)
5. Layout managers vs. CSS Grid
6. Radio buttons, checkboxes, modal dialogs

---

## 1. Assessment and References

Assessment components: reflection journals, milestone commits for the group project, lab implementations, written exams (graphics algorithms and pipeline design).

| Reference | Used for |
|---|---|
| Core Java Vol. I (Horstmann) | Java implementation: OOP, generics, events, Java 2D |
| Computer Graphics with OpenGL (Hearn, Baker) | Coordinate spaces, rasterization, clipping, fixed pipeline |
| Interactive Computer Graphics with WebGL (Angel, Shreiner) | Shaders, matrix transforms, scene composition |
| Designing the User Interface (Shneiderman et al.) | Usability, direct manipulation, affordances |
| Introduction to Computer Graphics (Eck) | Open-access text on 3D transforms and canvas rendering |

---

## 2. Exceptions, Assertions, Logging

### 2.1 Exception hierarchy

| Category | Examples | Meaning |
|---|---|---|
| Unchecked (`RuntimeException`) | `NullPointerException`, `IndexOutOfBoundsException` | Programming bugs |
| Checked | `IOException` (e.g. image load failure) | Recoverable external failures |

Rules:
- Never swallow an exception with an empty `catch`.
- Preserve the stack trace (log it or chain it as the cause).
- Release resources (file handles, graphics contexts) in all paths.
- Move the component to a safe fallback state after a failure.

```java
try (InputStream in = Files.newInputStream(path)) {
    BufferedImage img = ImageIO.read(in);
    texture.set(img);
} catch (IOException e) {
    logger.log(Level.SEVERE, "Texture load failed: " + path, e);
    texture.set(FALLBACK_IMAGE);
}
```

`try-with-resources` closes the stream automatically, whether the block exits normally or by exception.

### 2.2 Assertions

- `assert` checks internal invariants during development.
- Disabled by default. Enabled with the `-ea` JVM flag, so there is no cost when disabled.
- Graphics use cases: non-negative screen coordinates, matching vector/matrix dimensions, color channels within [0, 255].

```java
assert x >= 0 && y >= 0 : "negative screen coordinate: (" + x + ", " + y + ")";
assert r >= 0 && r <= 255 : "red out of range: " + r;
```

Assertions are for bugs, not for validating user input or recoverable conditions.

### 2.3 Logging (`java.util.logging`)

Advantages over `System.out.println`:
- Severity levels: `SEVERE`, `WARNING`, `INFO`, `CONFIG`, `FINE`, `FINER`
- Configurable formatters and handlers
- Thread-safe
- Filtering by level at runtime, with no recompilation

Useful for tracking frame drops and race conditions in render and event threads.

---

## 3. Generic Programming

Pre-generics collections stored `Object`, which required explicit casts and could throw `ClassCastException` at runtime. Generics move that check to compile time.

```java
class SceneNode<E> { /* ... */ }
class Vector3D<T extends Number> { T x, y, z; }
```

The same structure (quadtree, octree, vertex buffer) can then hold `float`, `double`, or custom vertex types.

| Feature | Syntax | Purpose |
|---|---|---|
| Bounded type | `<T extends Comparable<T>>` | Guarantees `compareTo` is available |
| Upper-bounded wildcard | `<? extends Shape>` | Read from a collection of `Shape` or its subtypes |
| Lower-bounded wildcard | `<? super Polygon>` | Write `Polygon` into a collection of `Polygon` or its supertypes |

**Type erasure:** type parameters are removed at compile time and replaced by their bound (or `Object`). Compile-time checking is enforced, and the bytecode is the same as non-generic code, so there is no runtime penalty.

---

## 4. Components and Event Handling

### 4.1 Component model

A graphical component is an object with:
- a bounding rectangle
- internal state
- paint logic
- event callbacks

### 4.2 Event flow

```
Input hardware (mouse / keyboard / touch)
  -> OS interrupt -> event record
  -> window manager routes to application
  -> registered listener callback on component
  -> listener updates the model
  -> repaint()
  -> paint scheduled on the Event Dispatch Thread (EDT)
```

```java
panel.addMouseListener(new MouseAdapter() {
    @Override
    public void mousePressed(MouseEvent e) {
        model.setSelection(e.getX(), e.getY());  // update model state
        panel.repaint();                         // request a new paint pass
    }
});
```

Key points:
- Listeners only mutate the model and call `repaint()`. Drawing happens in the paint method.
- `repaint()` schedules painting. It does not draw immediately.
- Swing UI code runs on the EDT.
- This listener/model/paint separation is what makes direct manipulation possible.

---

## 5. Layout Managers vs. CSS Grid

| | Swing | CSS |
|---|---|---|
| Uniform grid | `GridLayout` | `grid-template-columns: repeat(n, 1fr)` |
| Flexible cells | `GridBagLayout` (constraints object) | Grid tracks, `fr` units, `gap`, alignment |

CSS Grid defines a 2D matrix of row and column tracks declaratively. Both approaches compute component sizes and positions from constraints instead of hard-coded pixel values.

---

## 6. Selection Controls and Modal Dialogs

### 6.1 Radio button vs. checkbox

| | Radio button | Checkbox |
|---|---|---|
| Selection | Mutually exclusive within a group | Independent |
| State | One active option per group | Each toggles on/off separately |
| Use for | Single choice among states | Additive options |
| Example | Render mode: Wireframe / Flat / Ray traced | Shadows, anti-aliasing, debug axes |

### 6.2 Modal dialogs

A modal dialog blocks input to the parent window until the user dismisses it.

Use cases:
1. **Data-loss prevention:** confirm before closing an unsaved project, discarding a layer hierarchy, or overwriting a scene file.
2. **Mandatory error acknowledgement:** shader compile errors, render failures, disk I/O errors. The user must acknowledge before continuing, so the application state is not corrupted by further actions.

```java
int choice = JOptionPane.showConfirmDialog(
    frame, "Discard unsaved changes?", "Confirm",
    JOptionPane.YES_NO_OPTION);
if (choice == JOptionPane.YES_OPTION) { closeProject(); }
```

---

## Summary

Error handling in Java separates unchecked exceptions (bugs) from checked exceptions (recoverable failures). Checked failures are handled with `try-with-resources`, logged with `java.util.logging` at the appropriate level, and followed by a fallback state. Assertions check internal invariants and are enabled only with `-ea`. Generics provide compile-time type safety through bounded types and wildcards (`? extends` for reading, `? super` for writing), and type erasure keeps runtime cost at zero. In GUI code, input events reach registered listeners, which update the model and call `repaint()`, and painting is then scheduled on the EDT. Swing layout managers and CSS Grid both position components from constraints rather than fixed pixels. Radio buttons enforce a single choice within a group, checkboxes toggle independently, and modal dialogs block the parent window for data-loss confirmation and mandatory error acknowledgement.
