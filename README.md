# Edward's Bell Code Builder Language Test

This repository demonstrates how a Minecraft Education NPC can open a guided
MakeCode tutorial directly in a text-code editor. The included world implements
one deliberately small **Python** example. The equivalent JavaScript route is
documented but is not included as a second learner activity.

This is an isolated technical prototype, not finished learner content and not a
replacement for the released Edward's Bell Blocks prototype.

## Download and test

[Download the Python NPC test world](https://github.com/BlockBuilderJoe/edward-bell-makecode-python-test/releases/download/v0.0.1/Quest-2C-Python-CodeBuilder-NPC-Test.mcworld)

1. Import and open the world in Minecraft Education.
2. If Code Builder opens immediately, confirm that it displays Python text,
   then close it so the NPC handoff can also be tested.
3. Talk to the **Technocamps Mentor**.
4. Choose **Try Python editor**.
5. Confirm Code Builder opens the `python-bell-test` tutorial in Python.
6. Add `agent.move(BACK, 1)` after `loops.pause(1000)`.
7. Press Play once. The Agent should ring Bell 1, return to the gold tile, and
   Minecraft should report that practice is complete.

## Test flow

```text
Technocamps Mentor
  → Try Python editor
  → start the existing Bell 1 world check
  → Code Builder loads a public GitHub tutorial
  → #tutorial:py selects the Python editor
  → learner adds agent.move(BACK, 1)
  → Play sends the command to Minecraft
  → the existing world logic checks the result and gives feedback
```

The world uses this tutorial URL:

```text
https://minecraft.makecode.com/?forcelang=en&skipgithubcache=1&ingame=1&ipc=1&noRunOnX=1&lockedEditor=1#tutorial:py:github:BlockBuilderJoe/edward-bell-makecode-python-test/python-bell-test
```

The tutorial itself is [python-bell-test.md](python-bell-test.md). Full Python
and JavaScript implementation instructions are in
[CODEBUILDER-LANGUAGES.md](CODEBUILDER-LANGUAGES.md).

## Scope and status

- Python route: packaged and structurally validated; requires the final
  Minecraft Education client check described above.
- JavaScript route: documented equivalent; not implemented in this test world.
- Production Edward's Bell repository and release: unchanged.
- Welsh content: outside this isolated editor-language test.
