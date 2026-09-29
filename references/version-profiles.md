# Version Profiles

Use this file to adapt the same insight core to different interaction environments.

## Core idea

This skill is one analysis core with multiple interaction shells.
Do not force the same intake behavior everywhere.

The main difference across environments is not the quality of analysis.
It is:

1. whether follow-up questions are possible
2. whether a short confirmation step is possible
3. whether the input is one-shot text or attachment only
4. whether platform documents and internal tooling are available

## Profile 1: local-interactive

Use for:

- interactive CLI or desktop agent sessions where follow-up questions feel natural

Behavior:

1. allow short follow-up questions
2. ask for missing speaker, role, or scene context before strong interpretation
3. support deep memo plus optional analysis notes

Best for:

- highest precision
- messy interview material
- customer and school-enterprise conversations
- cases where endorsement and correction chains matter

## Profile 2: workflow-confirmed

Use for:

- messaging-bot runtimes
- scheduled or semi-structured agent pipelines

Behavior:

1. front-load a small set of required fields
2. allow only light confirmation
3. prefer stable Markdown output over long back-and-forth
4. read [workflow-confirmed-template.md](workflow-confirmed-template.md) when defining the intake or output contract

Best for:

- collaborative use
- bot- or form-driven input
- repeatable team workflows

## Profile 3: form-constrained

Use for:

- simple web forms and one-shot submission flows
- attachment-first experiences

Behavior:

1. rely on a fixed input template
2. do not depend on long follow-up
3. if context is missing, surface gaps and lower interpretation strength

Best for:

- low-friction internal use
- colleague-facing experiences
- demo or lightweight productization

## Profile 4: portable-open

Use for:

- public and open-source versions
- public prompt packs
- low-dependency reuse

Behavior:

1. avoid internal tooling assumptions
2. keep logic conservative and portable
3. make external research optional rather than required

Best for:

- public sharing
- method demonstration
- generic reuse

## Recommended development order

Build and stabilize in this order:

1. local-interactive
2. workflow-confirmed
3. form-constrained
4. portable-open

Reason:

The first two sharpen the real method in live use.
The last two are packaging layers and should inherit a stable core rather than define it too early.
