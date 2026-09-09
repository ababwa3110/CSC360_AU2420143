# Lecture 6 Reflection: Course Roadmap, Git Practices, Maven Configuration & Thread Safety

**Date:** 25 August 2026

---

## 1. Shape Complexity Progression

Three-stage roadmap for shape-drawing tasks:

1. **Square** — coordinate/structural baseline.
2. **Triangle** — multi-point geometry, extends square logic.
3. **Trees** — shape composition, likely recursive construction.

Each stage extends the coordinate/structural logic of the previous stage.

---

## 2. Git Practices

- Pull upstream changes before starting new work.
- Outdated local branches are the primary cause of merge conflicts.
- Workflow order:
```
  git pull
  (begin new work)
```

---

## 3. Maven Configuration (`pom.xml`)

- `pom.xml`: core Maven project configuration file.
- Defines:
  - Dependencies
  - Build settings

### IntelliJ Maven Integration
- IntelliJ exposes Maven-specific tooling for build management within the IDE, as an alternative to CLI Maven commands.

---

## 4. GUI Thread Safety

- GUI components are **not thread-safe**.
- Related concepts:
  - Threads
  - Thread safety
  - Processes (OS-level)

### Constraint
- GUI operations must execute on a single designated thread (Event Dispatch Thread, in Swing/AWT), not accessed concurrently from multiple threads.

---

## 5. Java Cold Start

- Java has a cold start: initialization overhead precedes execution.
- Consequence: unsuitable as a scripting language, relative to languages with immediate execution.

---

## Summary of Technical Points

- Shape progression: square → triangle → trees; each stage extends prior coordinate/structural logic; trees involve shape composition and recursion.
- Git: pull upstream before new work to prevent merge conflicts.
- `pom.xml` defines Maven dependencies and build settings; IntelliJ provides integrated Maven tooling.
- GUI components are not thread-safe; GUI operations restricted to a single designated thread.
- Java cold start (initialization overhead) makes it unsuitable for scripting use cases.
