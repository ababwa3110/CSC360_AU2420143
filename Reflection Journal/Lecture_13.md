# L13 Reflection: 29/09/2026

## Work Done: Printing and Integration

Modules: `TreePrinter`, `AsciiTree` (main).

### TreePrinter

```java
System.out.println(root.name);
Deque<StackFrame> stack = TreeTraversal.buildInitialStack(root);
while (!stack.isEmpty()) {
    StackFrame frame = stack.pop();
    String connector = frame.isLast ? "└── " : "├── ";
    System.out.println(frame.prefix + connector + frame.node.name);
    TreeTraversal.pushChildren(stack, frame);
}
```

- The root is printed without a connector.
- Each pop prints `prefix + connector + name`, then pushes that node's children.
- `TreePrinter` depends on `StackFrame` and `TreeTraversal`, so it was merged last among the modules.

### Integration (`AsciiTree.main`)

```
InputHandler.readRelationships -> TreeBuilder.buildTree -> null check -> TreePrinter.printTree
```

If `buildTree` returns `null`, the program prints an error and exits.

### Merge order (one branch per module, merged by PR)

Tree Construction -> Input Handling -> Stack Traversal -> Printing -> Integration.

### Test output

```
CEO
├── VP_Sales
│   ├── Manager_1
│   │   └── Sales_Rep
│   └── Manager_2
└── VP_Eng
    ├── Dev_1
    ├── Dev_2
    └── Dev_3
```

### Known limitations

- Non-numeric input for `n` throws `NumberFormatException`.
- Multiple roots: only the first root found is printed.
- A child with two parents is printed under both.
- Cycles that do not include every node are not detected.

### Summary

Connected the modules into one pipeline. The printer pops frames from the stack, prints each line, and pushes children. The full program produces correct output for the sample input, with the limitations above still open.
