### 1. Drawing a Square (Pseudocode & Canvas Logic)
* **Pixel units:** Canvas measurements and coordinates are defined in pixels.
* **Centering logic:** Find the starting corner by subtracting half the length from the center point: `start_x = center_x - (length / 2)` and `start_y = center_y - (length / 2)`.
* **Pseudocode:**
  ```text
  half_len = length / 2
  start_x = center_x - half_len
  start_y = center_y - half_len
  
  drawLine(start_x, start_y, start_x + length, start_y)
  drawLine(start_x + length, start_y, start_x + length, start_y + length)
  drawLine(start_x + length, start_y + length, start_x, start_y + length)
  drawLine(start_x, start_y + length, start_x, start_y)
  ```

---

### 2. Maven Project Structure & Files
* **`pom.xml`:** The core config file holding project dependencies, build steps, and plugin settings.
* **`src/main/java`:** Holds all main Java source code files.
* **`src/main/resources`:** Holds non-code assets like images, properties, or configuration files.
* **`src/test/java`:** Holds unit test classes (e.g., JUnit tests).
* **`target/`:** Holds compiled output (`.class` files) and built final binaries (`.jar` or `.war`).

---

### 3. What is JFrame?
* **GUI Window:** A Java Swing top-level container that represents a standard desktop window with title bar and window controls.
* **Component Host:** Serves as the main canvas/frame onto which buttons, labels, panels, and custom graphics are placed.

---

### 4. Static Field vs. Object Field
* **Static Field:** A class-level variable shared across all instances; only one copy exists in memory regardless of how many objects are created.
* **Object (Instance) Field:** Belongs to a specific object instance; every object gets its own separate copy with unique values stored on the heap.
