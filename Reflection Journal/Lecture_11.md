# L11 Reflection: 10/09/2026

## Work Done: Data Model and Input

Modules: `TreeNode`, `TreeBuilder`, `InputHandler`.

### TreeNode

```java
class TreeNode {
    String name;
    List<TreeNode> children = new ArrayList<>();
}
```

A node holds a name and an ordered list of children. Children print in insertion order.

### TreeBuilder

```java
Map<String, TreeNode> nodeMap = new HashMap<>();
Set<String> childNodes = new HashSet<>();
TreeNode parent = nodeMap.computeIfAbsent(parentName, TreeNode::new);
TreeNode child  = nodeMap.computeIfAbsent(childName,  TreeNode::new);
parent.children.add(child);
childNodes.add(childName);
```

- `computeIfAbsent` guarantees one `TreeNode` per name, so repeated names refer to the same object.
- Root detection: the root is the node whose name is never in `childNodes`.
- If every node appears as a child (a cycle), `buildTree` returns `null` and `main` reports it.

### InputHandler

- Reads `n`, then `n` lines of `Parent Child`, split on `\\s+`.
- Validation: lines with fewer than 2 tokens are skipped with a message.

### Pipeline so far

```
Scanner -> List<String[]> pairs -> TreeBuilder.buildTree() -> TreeNode root
```

### Summary

Built the tree from parent-child pairs using a name-to-node map and identified the root as the node absent from the child set. Input is read and validated line by line.
