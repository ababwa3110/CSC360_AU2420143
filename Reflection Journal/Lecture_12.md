# L12 Reflection: 15/09/2026

## Work Done: Stack-Based Traversal

Modules: `StackFrame`, `TreeTraversal` (my module).

### StackFrame

```java
class StackFrame {
    TreeNode node;
    String prefix;   // string printed before the connector
    boolean isLast;  // last child of its parent?
}
```

Each frame carries the state needed to print one line, so traversal needs no recursion.

### Push logic

```java
String childPrefix = frame.prefix + (frame.isLast ? "    " : "│   ");
for (int i = children.size() - 1; i >= 0; i--) {
    boolean isLast = (i == children.size() - 1);
    stack.push(new StackFrame(children.get(i), childPrefix, isLast));
}
```

- The stack is LIFO, so children are pushed last-to-first. The first child then pops first and the order is preserved.
- `isLast` is true only for index `size - 1`.
- The child prefix depends on the parent: 4 spaces if the parent is last (no vertical line), `│` plus 3 spaces if not (line continues).
- `buildInitialStack(root)` does the same for the root's children with prefix `""`.

### Trace (root `CEO`, children `VP_Sales`, `VP_Eng`)

| Step | Pop | Stack after push (top first) |
|---|---|---|
| 0 | (initial) | VP_Sales(F), VP_Eng(T) |
| 1 | VP_Sales | Manager_1(F), Manager_2(T), VP_Eng(T) |
| 2 | Manager_1 | Sales_Rep(T), Manager_2, VP_Eng |
| 3 | Sales_Rep | Manager_2, VP_Eng |

### Complexity

O(N) pushes and pops. String prefix construction adds O(depth) per node.

### Summary

Replaced recursive traversal with an explicit `Deque<StackFrame>`. Reverse-order pushing keeps sibling order, and the prefix rule keeps the vertical lines correct.
