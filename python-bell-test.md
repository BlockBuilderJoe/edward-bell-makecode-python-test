### @explicitHints 1

# Edward's Bell: Python editor test

```python-template
agent.teleport(world(18, 57, 12), EAST)
agent.move(FORWARD, 1)
loops.pause(1000)
```

## Check the editor @showdialog

This is a small test of Python inside Minecraft Code Builder. You should see
text code rather than draggable blocks. The starter sends the Agent from the
gold tile to Bell 1 and pauses, but it does not bring the Agent back.

## Add the missing Python line

Click after `loops.pause(1000)` and add this line:

```python
agent.move(BACK, 1)
```

The word `BACK` must remain in capital letters. Keep the distance as `1`.

## Predict, then run

Before pressing Play, predict where the Agent will finish. Then press the green
Play button once. It should move forward to ring Bell 1 and move back onto the
gold tile.

If the Agent stays on the bell, check the spelling, brackets, comma, and
indentation of the line you added, then run it again.

```python
agent.teleport(world(18, 57, 12), EAST)
agent.move(FORWARD, 1)
loops.pause(1000)
agent.move(BACK, 1)
```
