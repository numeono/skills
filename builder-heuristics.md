# Builder heuristics

These heuristics guide how to build and what to build on. They apply to code, infrastructure, commands, skills, and documentation. The heuristics are listed in priority order. When two conflict, the higher one wins.

Call them by name. Collectively, they are the builder heuristics. Individually, refer to each as "builder heuristic N" and link to this file when invoking one.

## How to build

**1. The best part is no part.** Before adding a file, dependency, service, configuration flag, abstraction, or script, try to remove the need for it. Reuse what already exists, or show that the problem does not need solving. Every added part is something someone must understand, maintain, secure, back up, and eventually remove.

**2. First principles: question the requirement.** Ask what outcome is actually needed, which constraints are real, which are assumptions inherited from an earlier decision, and whether a recent change has made the requirement unnecessary or wrong. Reason from what is true now, not from precedent. The right implementation of a bad requirement is still the wrong result.

**3. Occam's razor: simple is best.** When several solutions fit the facts, prefer the one that introduces the least complexity. Complexity must earn its place by solving a problem you can name.

**4. Standard is best.** Prefer the well-established option: the language's idiom, the framework's default, a widely available tool, or the pattern already used in the project. Match the surrounding code instead of importing a new style. A custom mechanism must be justified by a concrete need that the standard option cannot meet.

**5. Deterministic is best: programmatic over AI.** Use AI to help write scripts, parsers, schemas, migrations, and tests, then let the shipped system run without a model in the loop whenever possible. Use AI at runtime only where deterministic methods cannot handle the task, such as open-ended language, judgment over messy or unseen input, or work with no rule you can state. Keep runtime AI behind a narrow boundary, check its output programmatically, and decide in advance what happens when it is wrong.

**6. Maintainable is important.** Write for whoever inherits the work, including your future self or an agent with none of your context. Prefer obvious control flow over clever compression and one documented method over several undocumented ones. Explain why when the reason is not self-evident. If the work cannot be understood without its author present, it is not finished.

Name things so they explain themselves. Prefer a clear, descriptive name over a terse one for variables, functions, commands, and files. `client-extract-config` is clearer than `cfg` without becoming needlessly long.

**7. Modular is important.** Keep concerns in separate, replaceable pieces with narrow boundaries. Give each piece one job and make it replaceable without changing its neighbors. Modularity shapes the parts that survive builder heuristics 1 through 5. It is not permission to add unnecessary parts.

**8. Production-ready, reusable, and open-sourceable.** Build work that could ship. Handle errors, choose sensible defaults, and make deployment possible without the original author narrating it. Do not hardcode personal paths, organization names, hostnames, or credentials. Publishing or reusing the work should require minimal changes.

## Choosing tools, dependencies, and services

**9. Open source and commercially usable.** Prefer open-source software under permissive licenses such as MIT, Apache-2.0, and BSD. Check the license before adopting a dependency. Copyleft and source-available licenses can impose obligations or restrictions on distributed software, so adopting one should be a deliberate decision. Closed-source software is an exception that needs a concrete justification.

**10. Self-hostable and owned rather than rented.** Favor software you can run on your own hardware. A hosted tier counts only if you could move it in-house later through an open-source implementation, documented deployment process, exportable data, and no proprietary lock-in. All else being equal, prefer free, one-time, or metered pricing over per-seat subscriptions. Cost is a tiebreaker, not a gate. Pay for a subscription when it is genuinely the best tool for mission-critical work, and apply more scrutiny to incidental or replaceable services.

## When a heuristic cannot be met

Some constraints leave no compliant option, such as a required platform, a vendor API, or a service with no self-hosted equivalent. Break the heuristic deliberately. State which heuristic cannot be met and why, keep the exception behind a replaceable boundary, and do not let it become the default for the next decision.

If a request conflicts with these heuristics, build what was requested and explain what you would have done differently. Do not silently substitute another design.
