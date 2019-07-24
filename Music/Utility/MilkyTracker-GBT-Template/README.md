## What is this?

It's a template for MilkyTracker. This .xm file that should be used as a template for making .mod files to be used in GBT Player through GB Studio 1.1.0. GB Studio users should know that GB Studio relies on GBT Player for music playback.

## What's the template for?

GBT Player does not read custom sampledata from the .mod file you're making. GBT Player has a bunch of pre-baked instruments to be called upon, so you're just writing the note, instrument # and effect data with the .mod format. This .xm file contains instruments that are essentially examples of what you will hear when your .mod file is played back with GBT Player.

## How is this different from the existing template.mod?

Normally composers can load template.mod that's included with GBT Player and all of GB Studio's new projects so they have access to all of these example instruments, but if you're a Milkytracker user like me you'll soon discover that Milkytracker corrupts .mod files if the save button is pressed Milkytracker. A corrupted .mod sounds like fast, high-pitched squeaks followed by silence when played by GBT Player.

The workaround is just to use "save as" to convert a .mod into an .xm file, and to only press "save" when working in the .xm file. When you want to test your song you'd press "save as" to turn your .xm file into a .mod file for GBT Player. This .xm template has this first step done for you, but you will still need to press "save as" to create a .mod file when you want to test your song. I also added a few things specific to composing with GBT Player that are often overlooked in the regular template.mod

## tldr;

Saving an .xm file is safe, pressing "save as" to .mod is safe (that's how you export your song) just *never* hit "save" on a .mod file in Milkytracker.

## Differences from template.mod

1. **C00 on channels 1 and 2**

In channels 1 and 2 I put effect C00 on the first row to silence these two tracks. Otherwise these channels play a default note on their own if their volume isn't controlled on the first row of the song. The C00 effect can be changed to any other effect if you're intending to play a note on that row with that channel. Putting a non-volume effect like E8x or Fxx will make that channel start at max volume.

2. **F07 on channel 4**

Channel 4 is the only channel that can set the song's tempo silently on the first row. 99% of songs will want to put effect F on channel 4 to start the song. Project settings aren't read by GBT Player at all, so just use F to set your song's speed instead of adjusting it on Milkytracker's interface. You can still set effect F on channels 1 or 2 later on in the song.

3. **No song data**

I got so used to wiping the song data for template.mod I didn't pick up on other important aspects of the file, so I decided to create a new template that starts with ideal settings for use in GBT Player. The tempo setting is setup for songs that are F05 or slower and are to be used in GB Studio 1.1.0 (or future versions if -speed has not been added to it)

4. **Project Tempo at 130 BPM**

When project tempo (or song BPM) is used alongside a speed effect (F1F or faster) MilkyTracker then uses the project tempo to emulate refresh rates. This data won't be read by GBT Player.

For GB Studio 1.1.0 users writing songs at speed F05 or slower, leave it at 130 BPM. There was nothing scientific about 130 BPM, it just sounded like the correct playback speed between the tracker and GB Studio. F04 or faster speeds should have the project BPM set to 150 to better emultae the 50hz refresh rate of the Gameboy.

The project tempo can be adjusted to your liking and it will only impact how fast MilkyTracker plays your song, nothing will be changed in-game. If your project BPM is being overwritten or uneditable from 130, try deleting any F effects that are higher than F1F (includes F20, F21) or enter F96 at the start of your song on channel 3. Your song will not be impacted in-game but your project BPM should be set to 150.

## Tips on In-Game Volume Playback

GBT Player always pulls from the last volume effect that you set for the channel. Example:
```__Channel 1__
C5 01 -- C40
-- -- -- C00
C5 01 -- ---
-- -- -- C00
```
This will only play 1 note in-game, even though MilkyTracker (and others) will play 2 notes.

Channels 1 and 2 will only make volume changes in steps of 4
`0, 4, 8, C, 10, 14, 18, 1C, 20, cont. up to 40`

Channel 3 only makes volume changes in steps of 16
`0, 10, 20, 30 and 40`

Channel 4 shows all volume changes
`...4, 5, 6, 7, 8, 9, A, B, C D, E, F, 10, 11, 12...`

`C3C` is the same as `C40` in all channels for some reason - thanks MelonadeM for discovering this

## Credits

This template was created by Ember#1765 / DeerTears on Github/itch.io

**Thanks to:**

- MelonadeM for being an all-knowing GBT guide
- richardLULZ for assisting with music docs and code review
- chris for making GB Studio
- GB Studio community for being awesome!
- and AntonioND for making GBT Player
