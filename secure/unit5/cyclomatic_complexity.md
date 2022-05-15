---
layout: notes
---
# Exploring the Cyclomatic Complexity’s Relevance Today

> The Cyclomatic Complexity is commonly considered in modules on testing the validity of code design today. However, in your opinion, should it be? Does it remain relevant today? Specific to the focus of this module, is it relevant in our quest to develop secure software? Justify all opinions which support your argument and share your responses with your team.

Cyclomatic complexity is a proxy for code quality. A function with high complexity is a function with a large number of independent paths. High complexity translates into more complex testing or poor test coverage. Complex testing requires high maintenance costs and is often neglected, while poor test coverage is associated with regressions.

Breaking complex functions into more functions lowers their complexity, and, from a practical perspective, nothing changes since the software will still perform the same operations. However, testing many simple functions is remarkably easier, and makes 100% coverage achievable.

I worked a lot on legacy software with very high complexity (in the range of hundreds), and the operation of refactoring the code to break it down to more manageable functions invariably reveals the existence of paths nobody was aware of. The question "is it a bug or a feature?" may sound funny, but the answer can have dramatic effects on the final software.

I usually recommend keeping the complexity below 5. With functional languages, it is also possible to aim for linear complexity in most of the components.

## Discussion

> What about CC in the presence of microservices?

From a design perspective, microservices are the components of classic monoliths. The differences introduced by the microservice model focus on deployment, scalability, scope, and lifecycle, not on how developers code. When tasked to break down a monolith into microservices, the developers may even keep most of the code unchanged, especially in monoliths with components where the coupling is low, and cohesion is high.
There is the misconception that an architecture based on microservices is inherently simple, but it is quite the opposite.

Monoliths centralize the common functions (logging, authentication, authorization), while microservices tend to duplicate them. To promote code reuse, it is necessary to implement strategies such as creating an internal framework, which sounds easy but means managing its lifecycle across many small applications.

Deployment of microservices is also way more complex because it is no more just about deploying an artifact. Microservices need to be wired together by a communication infrastructure made by other microservices. Monoliths' components call each other passing references to memory. With microservices, even the simplest direct REST API requires at least a service to resolve the services' names and a circuit breaker managing timeouts.
Another big difference is that a monolith is either all up or all down. In a microservices architecture, some services may be temporarily unavailable or partially disrupted, and this needs to be considered in a design.

Summarizing. Considerations about code's cyclomatic complexity are unaffected by a shift towards microservices. However, microservices add a whole new category of complexity in the areas of deployment and orchestration.
