# Opening Python or JavaScript in Minecraft Code Builder

Minecraft Education Code Builder uses two separate settings:

- The URL fragment selects the **coding editor**: `py` for Python or `js` for
  JavaScript/Static TypeScript.
- Query parameters such as `forcelang=en` select the **interface language**.
  They do not select the coding editor.

For a child-facing activity, use separate NPC buttons and separate tutorial
files. This avoids asking learners to find and change the editor themselves.

## 1. Python

### Tutorial URL

```text
https://minecraft.makecode.com/?forcelang=en&skipgithubcache=1&ingame=1&ipc=1&noRunOnX=1&lockedEditor=1#tutorial:py:github:OWNER/REPOSITORY/python-tutorial
```

The important section is:

```text
#tutorial:py:github:OWNER/REPOSITORY/python-tutorial
```

### Tutorial Markdown

Use `python-template` for starter code and `python` for learner examples:

````markdown
# Bell practice in Python

```python-template
agent.teleport(world(18, 57, 12), EAST)
agent.move(FORWARD, 1)
loops.pause(1000)
```

## Add the missing return

```python
agent.move(BACK, 1)
```
````

Set the project editor in `pxt.json`:

```json
"preferredEditor": "pyprj"
```

### NPC or function command

```mcfunction
codebuilder navigate @s true https://minecraft.makecode.com/?forcelang=en&skipgithubcache=1&ingame=1&ipc=1&noRunOnX=1&lockedEditor=1#tutorial:py:github:OWNER/REPOSITORY/python-tutorial
```

The implemented example in this repository uses
[`python-bell-test.md`](python-bell-test.md).

## 2. JavaScript

MakeCode calls its text language JavaScript, although it uses its Static
TypeScript subset and APIs.

### Tutorial URL

```text
https://minecraft.makecode.com/?forcelang=en&skipgithubcache=1&ingame=1&ipc=1&noRunOnX=1&lockedEditor=1#tutorial:js:github:OWNER/REPOSITORY/javascript-tutorial
```

The important section is:

```text
#tutorial:js:github:OWNER/REPOSITORY/javascript-tutorial
```

### Tutorial Markdown

Use `template` for starter code and `typescript` for text examples:

````markdown
# Bell practice in JavaScript

```template
agent.teleport(world(18, 57, 12), EAST)
agent.move(FORWARD, 1)
loops.pause(1000)
```

## Add the missing return

```typescript
agent.move(BACK, 1)
```
````

Set the project editor in `pxt.json`:

```json
"preferredEditor": "tsprj"
```

### NPC or function command

```mcfunction
codebuilder navigate @s true https://minecraft.makecode.com/?forcelang=en&skipgithubcache=1&ingame=1&ipc=1&noRunOnX=1&lockedEditor=1#tutorial:js:github:OWNER/REPOSITORY/javascript-tutorial
```

## Connecting either language to an NPC

The NPC button should call a function so setup, feedback, and the long URL stay
out of the dialogue JSON:

```json
{
  "name": {"rawtext": [{"text": "Try Python editor"}]},
  "commands": [
    "/execute as @initiator at @s run function bell/open_python_test"
  ]
}
```

The function can prepare the world check and then open Code Builder:

```mcfunction
tag @s add bell_planned
function bell/start_practice
tellraw @s {"rawtext":[{"text":"Add agent.move(BACK, 1), then press Play."}]}
codebuilder navigate @s true URL_FROM_THE_RELEVANT_SECTION_ABOVE
```

For a permanent activity, store the button and message text in `.lang` files
rather than hard-coding English in JSON or commands.

## Why these URL parameters are present

- `skipgithubcache=1` prevents a previously opened GitHub tutorial from masking
  recent changes during development and testing.
- `lockedEditor=1` keeps the learner inside the guided tutorial.
- `ingame=1&ipc=1` connects Code Builder to Minecraft Education.
- `noRunOnX=1` avoids an unintended keyboard run shortcut.
- `forcelang=en` isolates this editor-language test from interface translation.
  Replace or remove it when testing localisation.

## Repository requirements

1. The repository must be public so Code Builder can retrieve it.
2. Add every tutorial Markdown filename to the `files` array in `pxt.json`.
3. Keep `main.ts` empty unless code is intentionally meant to run when the
   tutorial opens.
4. Increment the `pxt.json` version and create a release when publishing changes.
5. Test from a newly imported world and through the actual NPC button.

## Acceptance checks

For each language confirm:

- Code Builder opens automatically from the NPC command.
- The expected text editor appears, not Blocks.
- Starter code is present and editable.
- Pressing Play affects the Agent in Minecraft.
- Correct code produces success feedback.
- Incorrect code leaves the learner with a clear retry path.
- Closing and reopening the tutorial does not fall back to stale content.

## Official references

- [Minecraft MakeCode tutorials in Blocks, Python, and JavaScript](https://minecraft.makecode.com/tutorials)
- [MakeCode tutorial snippets and Python templates](https://makecode.com/writing-docs/snippets)
- [MakeCode tutorial control options](https://makecode.com/writing-docs/tutorials/control-options)
- [Publishing GitHub-hosted MakeCode tutorials](https://makecode.com/writing-docs/user-tutorials)
