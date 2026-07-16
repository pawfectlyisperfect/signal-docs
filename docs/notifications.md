# Notifications

Signal has its own notification system instead of relying on vanilla toasts or the big center-screen title/subtitle popups. Everything routes through it now: group alerts, war events, and standout chat messages.

## Why not vanilla toasts/titles

Vanilla toasts are small and easy to miss, and the center-screen title/subtitle popups take over the whole screen and get in the way if more than one thing happens close together. A dedicated system means consistent styling, stacking multiple notifications cleanly, and control over things like fade timing and how long something stays up.

## What they look like

Notifications stack top-center on your screen, sized to fit their own text (so a longer message doesn't get cut off or overflow past the edge of the card). Each one fades in, sits for a few seconds depending on what kind of message it is, and fades out. Multiple notifications at once just stack downward in order.

## What triggers one

- **Group alerts** - manually sent alerts from someone with the right permission, optionally tied to a location.
- **War events** - attacks, captures, and defends (see [War Tracking](war-tracking.md) for exactly how each one behaves).
- **Standout chat** - messages from Officer-and-above roles, if you've got chat notifications enabled.

## Turning them off

Chat notifications specifically can be turned off from Settings if you'd rather just check the Chat tab yourself. War and alert notifications aren't separately toggleable right now, they're considered important enough to always show.
