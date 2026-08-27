# Lecture 5 Reflection

## 1. Markdown Standards & Documentation Hygiene

- Key Markdown formatting techniques covered:
  - Proper **header hierarchies** (`#`, `##`, `###`)
  - **Tabular data** organization
  - **Code blocks** for syntax
  - **Blockquotes** for emphasis/callouts

### Tools for Previewing Markdown Locally
Instead of opening a full IDE just to preview `.md` files, lightweight alternatives discussed:

| Tool Type | Examples |
|---|---|
| CLI tools | `grip`, markdown-preview utilities |
| Browser extensions | GitHub Markdown renderers |
| Standalone viewers | Lightweight desktop preview apps |

---

## 2. Object-Oriented Programming Foundations for Java Graphics

### Inheritance & Class Hierarchies
- Subclasses **inherit and extend** the state and behavior of parent classes.
- Naming convention example:
```java
  class Apple { }
  class SweetApple extends Apple { }
```
- `SweetApple` is the **specialized (child)** class; `Apple` is the **broader (base)** class.

### Anonymous Inner Classes
- Used for **rapid event handling** and inline component customization.
- Allows developers to **override methods on the fly** without declaring a separate, formal class.

---

## 3. Java Swing Architecture Workflow

A clear architectural hierarchy was established for building GUI applications:

```
JFrame (top-level window/container)
   └── JPanel (custom drawing surface, nested inside)
```

Important distinction: A **JFrame is never placed inside a JPanel**. It's the reverse — the JPanel is nested inside the JFrame.

### Step-by-Step Construction Pattern
1. Create a top-level `JFrame` to act as the application window.
2. Configure its lifecycle properties: size, visibility, close operation.
3. Nest a custom `JPanel` drawing surface inside the frame.
4. Override `paintComponent(Graphics g)` inside the panel class — this is the **core rendering loop**.
5. Always call `super.paintComponent(g)` first — **mandatory** to clear the surface and avoid visual artifacts.
6. Use the `Graphics` context to set stroke/color via the `Color` class before drawing shapes.

### Interactive Components
- Example: instantiate a `JButton` and add it directly to a `JFrame` to demonstrate a basic event-driven layout.

---

## 4. Geometric Algorithms for 2D Shape Construction

### Rectangles from Two Diagonal Points
Given two anchor points `(x1, y1)` and `(x2, y2)`:

| Property | Formula |
|---|---|
| Origin X | `min(x1, x2)` |
| Origin Y | `min(y1, y2)` |
| Width | `\|x2 - x1\|` |
| Height | `\|y2 - y1\|` |

### Triangles from Three Coordinate Points
- Constructed from three pairs: `(x1, y1)`, `(x2, y2)`, `(x3, y3)`.
- Rendered using `drawPolygon` or `fillPolygon`.
- **Collinearity constraint:**
  - Two points can be generated randomly within a coordinate range.
  - The **third point must be chosen carefully** to avoid all three lying on a straight line.
  - This ensures a **non-degenerate, visually stable polygon**.

---

## 5. Core Java Syntax & Conventions (Recap)

- **Imports:** `javax.swing.*`, `java.awt.*` — access windowing toolkits.
- **Structure:** class declarations, access modifiers.
- **Entry point:**
```java
  public static void main(String[] args) { }
```
- **Naming conventions:**
  - `CamelCase` → classes
  - `camelCase` → methods
- **Key drawing methods:** `drawLine`, `drawRect`, `fillOval`, `drawPolygon` — each governed by specific argument-passing rules.

---

## Summary of Technical Points

- Markdown reflections require headers, tables, code blocks, and blockquotes.
- Swing containment hierarchy: `JFrame` (top-level window) contains `JPanel` (drawing surface). This order is fixed and cannot be reversed.
- `paintComponent(Graphics g)` is the rendering loop; `super.paintComponent(g)` must be called first to prevent visual artifacts.
- Rectangle from two points: origin = `(min(x1,x2), min(y1,y2))`; width = `|x2-x1|`; height = `|y2-y1|`.
- Triangle from three points: two points can be random, third point must be chosen to avoid collinearity, using `drawPolygon`/`fillPolygon`.
- Inheritance syntax: `class SweetApple extends Apple` — subclass extends superclass state/behavior.
- Anonymous inner classes allow method overriding inline, without a separate named class, primarily for event handling.
- Standard imports: `javax.swing.*`, `java.awt.*`; entry point: `public static void main(String[] args)`.
- Naming conventions: `CamelCase` for classes, `camelCase` for methods.
