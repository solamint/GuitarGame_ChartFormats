# Pad Instruments

Majority of the Pad instrument implementation is derived from 5-Fret Guitar.

## Track Names

- `PAD GUITAR` - Pad Guitar
- `PAD DRUMS` - Pad Drums
- `PAD BASS` - Pad Bass
- `PAD VOCALS` - Pad Vocals
- `PAD KEYS` - Pad Keys

## Track Notes

| MIDI Note    | Description                           |
| :-------:    | :----------                           |
| Markers      |                                       |
| 127          | Trill lane marker                     |
| 126          | Tremolo lane marker                   |
| 124          | Big Rock Ending marker 1              |
| 123          | Big Rock Ending marker 2              |
| 122          | Big Rock Ending marker 3              |
| 121          | Big Rock Ending marker 4              |
| 120          | Big Rock Ending marker 5              |
| 116          | Star Power marker                     |
| 108          | Solo marker       				  	         |
|              |                                       |
| **Expert**   |                                       |
| 106          | Expert Orange Lift Marker (5th lane)  |
| 105          | Expert Blue Lift Marker (4th lane)    |
| 104          | Expert Yellow Lift Marker (3rd lane)  |
| 103          | Expert Red Lift Marker (2nd lane)     |
| 102          | Expert Green Lift Marker (1st lane)   |
|              |                                       |
| 100          | Expert Orange (5th lane)              |
| 99           | Expert Blue (4th lane)                |
| 98           | Expert Yellow (3rd lane)              |
| 97           | Expert Red (2nd lane)                 |
| 96           | Expert Green (1st lane)               |
|              |                                       |
| **Hard**     |                                       |
| 93           | Hard Blue Lift Marker (4th lane)      |
| 92           | Hard Yellow Lift Marker (3rd lane)    |
| 91           | Hard Red Lift Marker (2nd lane)       |
| 90           | Hard Green Lift Marker (1st lane)     |
|              |                                       |
| 87           | Hard Blue (4th lane)                  |
| 86           | Hard Yellow (3rd lane)                |
| 85           | Hard Red (2nd lane)                   |
| 84           | Hard Green (1st lane)                 |
|              |                                       |
| **Medium**   |                                       |
| 81           | Medium Blue Lift Marker (4th lane)    |
| 80           | Medium Yellow Lift Marker (3rd lane)  |
| 79           | Medium Red Lift Marker (2nd lane)     |
| 78           | Medium Green Lift Marker (1st lane)   |
|              |                                       |
| 75           | Medium Blue (4th lane)                |
| 74           | Medium Yellow (3rd lane)              |
| 73           | Medium Red (2nd lane)                 |
| 72           | Medium Green (1st lane)               |
|              |                                       |
| **Easy**     |                                       |
| 69           | Easy Blue Lift Marker (4th lane)      |
| 68           | Easy Yellow Lift Marker (3rd lane)    |
| 67           | Easy Red Lift Marker (2nd lane)       |
| 66           | Easy Green Lift Marker (1st lane)     |
|              |                                       |
| 63           | Easy Blue (4th lane)                  |
| 62           | Easy Yellow (3rd lane)                |
| 61           | Easy Red (2nd lane)                   |
| 60           | Easy Green (1st lane)                 |

### Note Mechanics

Notes are tap notes by default. Notes can be marked as Lifts by using the Lift markers of each respective difficulty. Typically, due to this instrument type being made for controllers, both hands should be considered for charting. Commonly found is a 2-3 split, but using the middle lane for both hands is allowed.

Sustains shorter than a 1/12th step are cut off and turned into a normal (non-sustain) note. This allows charters using a DAW to not have to make their notes 1 tick long in order for it to not be a sustain.

- This threshold can be changed using the `sustain_cutoff_threshold` song.ini tag.

Chords may have individual notes with different lengths. These are referred to as extended sustains (start at different times) and disjoint chords (start at the same time, end at different times).

### Phrase Mechanics

Star Power phrases mark sections of the chart where the player may gain Star Power. When Star Power is activated, points gained from notes are doubled (this applies on top of the standard combo multiplier), and health gained from hit notes drastically increases.

Solo markers designate sections of the song where a part in the song is playing a solo. These sections display a percentage of notes hit, and award bonus points at the end of the solo based on the percentage of notes hit.

Trill and tremolo lanes are used to make imprecise/indiscernible trills or repetitive taps easier to play. They prevent overhitting and only require you to hit faster than a certain threshold to hit the charted notes. ***Currently, the only game that supports Pad instruments (Encore) does not yet utilize tremolo/trill lanes.***

- Tremolo lanes can be used on chords.
- Trill lanes should only be used with two-note trills.
- These only apply to Expert unless they are marked at a velocity between 50-41, in which case it applies to Hard as well.

Big Rock Endings (BREs) are freestyle phrases at the end of songs with so-called "big rock endings" where the band rocks out for a period of time before playing their final notes. These freestyle phrases let players gain bonus points by playing whatever they want during the phrase. Following the phrase is at least one note, which the player must hit in order to earn those bonus points. If they miss or overstrum, they lose the points.

- BREs are started by placing a `[coda]` text event on the `EVENTS` track. Then, the duration of the BRE markers determines how long the freestyle section will last. All 5 BRE notes must be used to mark the phrase.
- After the freestyle phrase, there must be at least one note for the player to play. If no notes are present, the player cannot get their score.
- Notes still need to be charted under Guitar and Bass BRE sections for the purpose of character animations. In general, notes should still be charted regardless because not every game supports BREs.
- [More than one freestyle phrase may be placed during a BRE](https://youtube.com/watch?v=2iegD-LR8RE&t=208) (warning: this video is loud and the chart is awful), though this was probably never intended as it was never documented, and it might not work in some games. This is *very* edge-case, and almost no charts will have it.
