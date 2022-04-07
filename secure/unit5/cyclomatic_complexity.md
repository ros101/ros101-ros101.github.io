---
layout: notes
---
# Cyclomatic Complexity

> The Cyclomatic Complexity is commonly considered in modules on testing the validity of code design today. However, in your opinion, should it be? Does it remain relevant today? Specific to the focus of this module, is it relevant in our quest to develop secure software? Justify all opinions which support your argument and share your responses with your team.

Cyclomatic complexity is a proxy for code quality. A function with high complexity is a function with a large number of independent paths. High complexity translates into more complex testing or poor test coverage. Complex testing requires high maintenance costs and is often neglected, while poor test coverage is associated with regressions.

Breaking complex functions into more functions lowers their complexity, and, from a practical perspective, nothing changes since the software will still perform the same operations. However, testing many simple functions is remarkably easier, and makes 100% coverage achievable.

I worked a lot on legacy software with very high complexity (in the range of hundreds), and the operation of refactoring the code to break it down to more manageable functions invariably reveals the existence of paths nobody was aware of. The question "is it a bug or a feature?" may sound funny, but the answer can have dramatic effects on the final software.

I usually recommend keeping the complexity below 5. With functional languages, it is also possible to aim for linear complexity in most of the components.
