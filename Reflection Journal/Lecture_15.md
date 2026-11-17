# Session 15: Mock Pitches, Generics & JavaFX Graphics
**Date:** 01/10/2026

---

## 1. Mock Presentations & A Reality Check
Today’s session kicked off differently than usual—several groups, including ours, went up for mock project presentations. Doing a dry run in front of the faculty gave us a much clearer picture of how the final evaluation is going to work and what they actually care about when grading. 

The biggest lesson from going up there was realizing that a presentation isn't just a feature showcase; you have to be able to clearly explain *how* and *why* your project works. Starting the class with our own project on the screen also made the rest of today's lecture feel way more relevant, since I could immediately connect the new concepts back to what we are actively building.

### Functionality vs. Features (What Actually Matters)
One point from the feedback really stuck with me: the difference between **functionality** and **features**. 
* **Functionality** is whether the core purpose of your software actually works the way it is supposed to.
* **Features** are all the extra add-ons and bells and whistles you tack on.

When you're building a project, it is super tempting to keep piling on extra features just to make the app look bigger and more impressive. Today was a good reminder that none of those extras matter if the core functionality is buggy. A smaller, rock-solid application will always beat a bloated project where half the things don't work properly.

---

## 2. Writing Smarter Code with Java Generics
After the presentations wrapped up, we shifted into **Generic Programming** in Java. This topic clicked for me pretty quickly because the core idea is really practical: stopping yourself from writing the exact same code over and over just to handle different data types.

Instead of making one class to handle `Integer` data and a nearly identical class for `String` data, you can write a single generic class or method using a type parameter, and then just plug in the specific data type when you actually use it.

**Why this matters in practice:**
* **Beyond Inheritance:** In earlier OOP sessions, we mostly talked about code reuse through inheritance and polymorphism. Generics showed me another angle on reusable code—writing a single piece of logic that adapts to different types.
* **Easier Maintenance:** It isn't just about saving lines of code. If all your logic lives in one generic class instead of three duplicated ones, fixing a bug or updating a method only has to happen in one place.
* **Where We Already Use It:** This is the exact mechanism behind Java's built-in collections like `List`, `Set`, and `Map`, where the same data structure works regardless of what type of object you store inside it.

---

## 3. Graphics in JavaFX: Shapes vs. Canvas
From generics, we moved into how JavaFX handles graphics and how OOP concepts like inheritance and polymorphism show up visually.

### The `Shape` Hierarchy
JavaFX has a base `Shape` class, and specific shapes like `Rectangle`, `Circle`, `Line`, and `Ellipse` all inherit from it. Because they share that common parent type, they also share standard styling properties like:
* `fill` (interior color)
* `stroke` and `strokeWidth` (border color and thickness)
* `opacity` (transparency)

Seeing this made our earlier lessons on polymorphism feel a lot more concrete. For example, if you were building a drawing or diagramming app, you wouldn't need separate logic to manage circles, lines, and rectangles—you could group and style all of them together through the common `Shape` reference.

### Two Different Ways to Draw
We also compared JavaFX's `Shape` objects against using `GraphicsContext` (which tied back nicely to our older Java 2D sessions):

| Approach | How It Works | Best Used When... |
| :--- | :--- | :--- |
| **`Shape` Objects** | Shapes exist as actual nodes inside the JavaFX Scene Graph. | You want persistent objects on screen whose properties you can easily modify or animate later. |
| **`GraphicsContext`** | Works like direct drawing—you issue commands to paint directly onto a `Canvas`. | You just need to render graphics directly (similar to how we drew things in Java 2D) without tracking every shape as a separate UI node. |

---

## Summary Takeaways
1. **Nail the core first:** Main functionality needs to be reliable before spending time on bonus features.
2. **Pitching is part of the build:** How well you explain your architecture and decisions matters just as much as the code during evaluations.
3. **Use Generics to stay DRY (Don't Repeat Yourself):** Type parameters let one class or method safely handle multiple data types, making code cleaner and easier to maintain.
4. **Polymorphism in UI:** `Circle`, `Rectangle`, `Line`, and `Ellipse` all extend `Shape`, allowing them to share properties (`fill`, `stroke`, `opacity`) and be managed together.
5. **Scene Graph vs. Canvas:** JavaFX gives you the flexibility to either work with modifiable `Shape` nodes in the scene graph or draw directly onto a canvas using `GraphicsContext`.
