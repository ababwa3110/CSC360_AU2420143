# Lecture 7 Reflection: Java Compilation, Git Hygiene, Maven Build Pipeline, CI/CD, Encoding, Testing

**Date:** 27 August 2026

---

## 1. Java Compilation Process

`.java` files hold source code. `javac` compiles them into `.class` files containing bytecode, which the JVM executes at runtime. JAR files package compiled `.class` files and related resources together into a single distributable unit.

```
.java  →  javac  →  .class (bytecode)  →  JAR (packaged output)
```

Seeing the full pipeline made the distinction between source code and generated artifacts clearer than treating each piece in isolation.

---

## 2. Git: What Belongs in Version Control

Generated/binary files — `.class` files, JAR files — should not be committed to a Git repository. A repository should contain:

- Source code
- Files required to reproduce the build (e.g. `pom.xml`)

Version control tracks meaningful changes to a project, not output regenerated on every compile. Committing build artifacts adds clutter and makes the repo harder to maintain.

---

## 3. Maven / `pom.xml` — Broader Role

Previously `pom.xml` was framed mainly around dependency management. It actually drives the full build pipeline:

- Dependency management
- Compiling source code
- Running tests
- Packaging the application (e.g. into a JAR)

`pom.xml` is the config that takes raw source code through to executable/distributable output.

---

## 4. CI/CD (Overview)

Continuous Integration / Continuous Delivery (or Deployment): building and testing should be automated rather than done manually after every change.

- Code is pushed → CI/CD system compiles and tests automatically.
- Shifts the workflow from manual, developer-triggered builds toward an automated, repeatable process.

---

## 5. Character Encoding: UTF-8 vs UTF-16

Both UTF-8 and UTF-16 can represent the full Unicode character set, but capability alone doesn't determine which is the better choice. Selection factors:

| Factor | Relevance |
|---|---|
| Efficiency | Byte usage per character |
| Compatibility | Interop with existing systems |
| Support | How widely adopted/supported an encoding is |

Takeaway: technical capability doesn't automatically make something the right choice for a given situation.

---

## 6. Interviews & Proof of Concept Presentation

- Difficult interview questions don't always need an immediate, perfect answer.
- Reasoning through a problem out loud, explaining an approach, and showing what's already been built can matter as much as having the answer instantly.

---

## 7. Node.js: Security & Authentication (Brief)

- Secure login systems are a core requirement for applications handling user accounts.
- Introduced concepts: JWT tokens, session management.
- Not covered in depth — framed as an intro to how authentication fits into a web application's architecture.

---

## 8. Testing: Unit vs Integration

- **Unit testing** — verifies individual components/pieces of functionality in isolation.
- **Integration testing** — verifies that different parts of a system work correctly together.
- Connects to developing projects in phases: components get tested individually before being combined into a larger system.
- Testing responsibility is often a significant part of a developer's role at a company.

---

## Summary of Technical Points

- Compilation pipeline: `.java` → `javac` → `.class` (bytecode) → JAR (packaged output).
- Git repos should hold source code and build-reproduction files only; generated/binary files (`.class`, JAR) are excluded.
- `pom.xml` drives the full Maven pipeline: dependencies, compilation, testing, packaging — not just dependency management.
- CI/CD automates build/test on every push, replacing manual compile-and-test workflows.
- UTF-8 vs UTF-16 choice depends on efficiency, compatibility, and support — not just Unicode coverage.
- Interview approach: reasoning and demonstrated work can substitute for an immediate perfect answer.
- Node.js auth basics: JWT tokens, session management, as part of application security architecture.
- Unit testing verifies isolated components; integration testing verifies components working together; both tie into phased project development.
