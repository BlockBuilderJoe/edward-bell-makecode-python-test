# Edward's Bell Python Code Builder Test

This temporary public repository tests whether a Minecraft Education NPC can
open a guided MakeCode tutorial directly in the Python editor.

It is a technical prototype only. It is not part of the released Edward's Bell
activity and should not be treated as finished learner content.

Open the test tutorial:

https://minecraft.makecode.com/?skipgithubcache=1&ingame=1&ipc=1&noRunOnX=1&lockedEditor=1#tutorial:py:github:BlockBuilderJoe/edward-bell-makecode-python-test/python-bell-test

## Expected test flow

1. Import the matching local `.mcworld` test artifact.
2. Talk to the Technocamps Mentor and choose **Try Python editor**.
3. Code Builder should open a text editor containing Python starter code.
4. Add `agent.move(BACK, 1)` after the pause.
5. Press Play. The Agent should ring Bell 1 and return to the gold tile.
6. Minecraft should report that the practice is complete.

The normal Blocks route remains in the world so the two experiences can be
compared without changing the production tutorial repository.
