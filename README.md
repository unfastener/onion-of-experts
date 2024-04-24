# onion-of-experts

## Introduction

This is an idea for an efficient design of hierarchical LLMs. I'm publishing this idea here on GitHub, so that there is a public record of it.

Here's the original discussion that sparked the idea. The discussion focused on the differences between corvid and mammal brains:

> Basically, run a "corvid-like" efficient LLM as your main "mind". Then, have layers of larger
> LLMs around that are dormant, but can be called to action by the small LLM, recursively. The
> large LLM layers could be loaded from disk when needed and dropped when done, making the average
> power and memory usage much lower than when keeping everything resident at all times.


## The Idea

The concept of "onion of experts" reflects a sophisticated approach to designing systems that balance efficiency, capability, and resource usage. This idea builds on several existing strategies in AI and could potentially offer a flexible and scalable way to manage computational resources while maintaining high performance.

### How It Could Work

Core Model ("Corvid-like" Efficient LLM): This core model acts as the first line of response. It's designed to handle most queries that require less complexity and can be resolved with a high degree of efficiency. This layer operates continuously and uses minimal resources.

Dormant Expert Layers: Surrounding the core are multiple larger, more capable models. These models are dormant until needed, which conserves computational resources. When the core model encounters a query or task beyond its capability, it activates the relevant expert layer.

Dynamic Activation: The expert models can be dynamically loaded into memory only when needed. This could be based on specific triggers or thresholds in the complexity or nature of the queries received by the core model.

Recursive Activation: If the first activated expert layer cannot handle a query, it could pass the query further out to an even more capable, though more resource-intensive, layer. This process can continue as needed, adding layers like the layers of an onion.

Resource Management: Each layer could be optimized for different types of tasks, with mechanisms to load and unload models efficiently to manage computational overhead and memory usage dynamically.

### Benefits

Efficiency: Most of the time, only the most resource-efficient layer would be active, conserving energy and computational resources.

Scalability: Additional layers can be added as needed without restructuring the entire system.

Flexibility: Different layers can be specialized for various tasks, improving overall performance and adaptability.

### Challenges

Complexity in Management: Dynamically managing which layers are active and seamlessly transitioning between them could be technically challenging.

Latency: Loading and unloading models might introduce latency, which could impact performance, especially for time-sensitive applications.

Cost of Context Switching: There might be a computational cost associated with saving and restoring state as different layers are activated and deactivated.

This concept parallels some strategies in distributed computing and cloud services, where resources are allocated dynamically based on demand, but applied in the context of AI model architecture. It's a forward-thinking approach that could align well with future advancements in AI deployment, particularly in environments with variable computational workload demands.

### Additional Ideas

The expert layers don't have to run on the same computer as the core model / models. In fact, on a mobile device, it would be beneficial to have the core layer(s) run locally, and have an API to call the expert layers when their assistance is needed.
