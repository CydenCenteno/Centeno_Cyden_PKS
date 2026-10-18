# Fundamentals of Programming — Core Concepts

## Program Development Cycle

Analyze problem → Design (algorithm/flowchart/pseudocode) → Code → Test → Debug → Document → Maintain.

## Data Types & Variables

- Primitive: integer, floating point, boolean, character.
- Reference/compound: string, array, object.
- **Variable** = named storage. **Constant** = fixed value.
- Type casting: implicit (widening) safe; explicit (narrowing) may lose data.

## Operators

| Category | Examples |
|----------|----------|
| Arithmetic | `+ - * / %` |
| Relational | `== != < > <= >=` |
| Logical | `&& \|\| !` |
| Assignment | `= += -= *=` |

Integer division truncates: `7 / 2 = 3`. Modulo `7 % 2 = 1`.

## Control Flow

- **Sequence** — top to bottom.
- **Selection** — `if / else if / else`, `switch`.
- **Iteration** — `for` (known count), `while` (condition first), `do-while` (runs at least once).
- `break` exits loop. `continue` skips to next iteration.

## Functions / Methods

- Parameters in, return value out.
- One function, one job.
- **Scope** — variable visible only in its block.
- **Recursion** — function calls itself; needs base case.

## Arrays & Collections

- Array: fixed size, index from 0.
- List: dynamic size. Map: key → value. Set: unique values.

## OOP — Four Pillars

| Pillar | Meaning |
|--------|---------|
| Encapsulation | Hide data, expose via methods |
| Inheritance | Child class reuses parent |
| Polymorphism | Same call, different behavior |
| Abstraction | Expose essentials, hide detail |

Class = blueprint. Object = instance. Constructor initializes object.

## Error Handling

- Syntax error (compile) · Runtime error (crash) · Logic error (wrong result).
- `try / catch / finally`. Catch specific exceptions. Never swallow silently.

## Algorithms & Complexity

| Big O | Name | Example |
|-------|------|---------|
| O(1) | Constant | Array index lookup |
| O(log n) | Logarithmic | Binary search |
| O(n) | Linear | Linear search |
| O(n log n) | Linearithmic | Merge sort |
| O(n²) | Quadratic | Nested loops, bubble sort |

Binary search requires sorted data.

## Good Practices

- Meaningful names. Small functions. Comments explain *why*.
- Avoid magic numbers — use constants.
- Test edge cases: empty, null, zero, negative, max.

## Gotchas

- Off-by-one errors in loops.
- `=` assigns, `==` compares.
- Infinite loop: condition never becomes false.
- Floating point is imprecise (`0.1 + 0.2 != 0.3`).
