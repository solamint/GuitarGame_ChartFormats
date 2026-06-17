# Pad Instruments

This document details the format for Pad instruments in .chart files.

## Instrument Sections

### Section Names

Instrument names:

- `PadLead` – Pad Guitar
- `PadBass` – Pad Bass
- `PadDrums` – Pad Drums
- `PadVocals` – Pad Vocals
- `PadKeys` – Pad Keys

Difficulties:

- `Expert`
- `Hard`
- `Medium`
- `Easy`

### Note and Modifier Types

| Note Type | Description                                       |
| :-------: | :----------                                       |
| Notes     |                                                   |
| 0         | Green (1st fret) note                             |
| 1         | Red (2nd fret) note                               |
| 2         | Yellow (3rd fret) note                            |
| 3         | Blue (4th fret) note                              |
| 4         | Orange (5th fret) note                            |
|           |                                                   |
| Modifiers |                                                   |
| 5         | Green (1st lane) lift modifier                    |
| 6         | Red (2nd lane) lift modifier                      |
| 7         | Yellow (3rd lane) lift modifier                   |
| 8         | Blue (4th lane) lift modifier                     |
| 9         | Orange (5th lane) lift modifier                   |

#### Note Mechanics

Notes are tap notes by default. Notes can be marked as Lifts by using the Lift modifier. Typically, due to this instrument type being made for controllers, both hands should be considered for charting. Commonly found is a 2-3 split, but using the middle lane for both hands is allowed.

Sustains do not get cut off if they are shorter than a certain threshold, unlike .mid.

Chords may have individual notes with different lengths. These are referred to as extended sustains (start at different times, end at same or different times) and disjoint chords (start at the same time, end at different times).

### Special Phrase Types

| Special Type | Description                    |
| :----------: | :----------                    |
| Star Power   |                                |
| 2            | Star Power phrase              |

### Local Events

These are far from the only local events that may be seen, these are just the ones that are commonly supported.

| Event Name | Description    |
| :--------- | :----------    |
| `solo`     | Starts a solo. |
| `soloend`  | Ends a solo.<br>Any notes at the same position are included in the solo. |

## Example

```
[ExpertPadLead]
{
  768 = N 0 0
  768 = S 64 768
  864 = N 1 0
  864 = N 3 0
  960 = N 1 0
  960 = N 6 0
  960 = N 3 0
  960 = N 8 0
  1056 = N 3 0
  1056 = E solo
  1152 = N 4 0
  1152 = N 1 0
  1248 = E soloend
}
```
