# Concordia
Supervisor-led agent society for coordinated problem solving
Inspiration
I was inspired by the idea that complex problems get easier when they are broken into focused roles instead of forcing one model to do everything at once. That is why I designed the project around a supervisor, specialist workers, and a shared state, so the system behaves like a coordinated team rather than a single monolith.
The motivation also came from real failure modes in agent systems: confusion over responsibilities, looping conversations, and conflicting outputs. A clear orchestration layer with explicit authority and escalation rules seemed like the most reliable way to keep the workflow stable.
What I learned
I learned that multi-agent design is less about making agents “smarter” and more about making the system more manageable. Shared state, structured messages, and explicit handoffs matter because they reduce coordination mistakes and make the whole workflow easier to inspect and debug.
I also learned that evaluation has to go beyond answer quality. Good agent systems should be measured by task success rate, coordination quality, latency, and cost efficiency, because a system can be accurate and still be too slow or too expensive to use in practice.
How I built it
I built the project as a hierarchy: a supervisor agent first decomposes the task, then assigns sub-tasks to specialized agents such as a researcher, coder, and reviewer. Each agent reads and writes to a shared state object, which acts like a blackboard for dependencies, progress, and intermediate results.
For communication, I used constrained message formats with clear intents such as PROPOSE, ACCEPT, REJECT, COUNTER_PROPOSE, and REQUEST_INFO, so agents could negotiate without drifting into vague conversation. When conflicts appeared, I added a debate-style resolution step, and for unresolved deadlocks I escalated to a meta-agent or human review, which matches common conflict-mitigation patterns in multi-agent systems.
Challenges faced
The hardest challenge was preventing agents from duplicating work or contradicting each other. That problem showed up when one agent moved ahead with incomplete assumptions, so I had to tighten role boundaries, add verification gates, and define termination rules to stop loops and retries from spiraling.
Another challenge was balancing performance with cost. Splitting work across agents can improve execution time, but it can also increase token usage, so I had to compare the multi-agent setup against a single-agent baseline using cost, latency, and success rate instead of assuming specialization would always be cheaper.
Project story
In the end, this project taught me that a strong agent society is built on structure, not just intelligence. The best results came from combining decomposition, shared memory, conflict resolution, and measurable evaluation into one workflow that could adapt without losing control.
That shift in thinking was the biggest lesson: the goal was not to create one perfect “god agent,” but to design a system where several limited agents could reliably outperform a single general one on complex tasks.
