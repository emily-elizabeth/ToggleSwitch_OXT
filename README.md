# Toggle Switch Widget (`org.openxtalk.toggleswitch`)

A LiveCode Builder (LCB) widget that renders an iOS-style pill toggle switch — a pink/magenta track with a white circular thumb.

---

## Preview

```
OFF  ╭──────────────╮        ON   ╭──────────────╮
     │ ●            │             │            ● │
     ╰──────────────╯             ╰──────────────╯
      [grey track]                 [pink track]
```

---

## Requirements

- LiveCode 9.0 or later (LCB widget support)
- Extension Manager (built into the LiveCode IDE)

---

## Installation

1. Open the **Extension Manager** via `Tools → Extension Manager`.
2. Click the **+** button and navigate to `toggleswitch.lcb`.
3. Click **Install**. The widget will appear in the Tools Palette under *Toggle Switch*.

---

## Usage

Drag the widget onto a card from the Tools Palette, or create it in script:

```livescript
create widget "MyToggle" as "org.openxtalk.toggleswitch"
```

### Setting the state

```livescript
-- Turn on
set the toggled of widget "MyToggle" to true

-- Turn off
set the toggled of widget "MyToggle" to false

-- Also works via the hilite alias (compatible with button idioms)
set the hilite of widget "MyToggle" to true
```

### Reading the state

```livescript
if the toggled of widget "MyToggle" then
   answer "Switch is ON"
else
   answer "Switch is OFF"
end if
```

### Responding to user interaction

When the user clicks the widget it posts a `toggled` message to its script object, passing the new boolean state as a parameter:

```livescript
on toggled pIsOn
   if pIsOn then
      show image "Banner"
   else
      hide image "Banner"
   end if
end toggled
```

---

## Properties

| Property  | Type    | Default       | Description                          |
|-----------|---------|---------------|--------------------------------------|
| `toggled` | Boolean | `false`       | The on/off state of the switch       |
| `hilite`  | Boolean | `false`       | Alias for `toggled` (LCS convention) |
| `onColor` | String  | `"252,76,153"`| The track colour when ON             |

---

## Messages Sent

| Message  | Parameter          | When                          |
|----------|--------------------|-------------------------------|
| `toggled`| `pIsOn` (Boolean)  | User clicks to toggle the switch |

The message is posted to the widget's **script object** (the card or stack script, or an attached behavior).

---

## Dimensions

The widget scales gracefully to any size. The default preferred size is **80 × 40 px**. The pill radius, thumb size, and padding all derive from the widget height at runtime, so resizing in the IDE will always look correct.

---

## Customisation

To change the ON colour, set the `onColor` property from your LiveCode script using a standard comma-separated RGB or RGBA color string:

```livescript
-- Blue
set the onColor of widget "MyToggle" to "0,122,255"

-- Green
set the onColor of widget "MyToggle" to "52,199,89"

-- Default pink
set the onColor of widget "MyToggle" to "252,76,153"
```

You can also read the current colour:

```livescript
get the onColor of widget "MyToggle"  -- returns e.g. "252,76,153"
```

---

## File Structure

```
toggleswitch.lcb    — Widget source (compile this)
README.md           — This file
api.lcdoc           — API documentation (LiveCode doc format)
```


