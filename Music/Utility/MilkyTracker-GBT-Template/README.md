## Credits

These templates were created by Ember#1765 / DeerTears with the help of MelonadeM and richardLULZ

**Thanks to:**

- MelonadeM for being an all-knowing GBT guide
- richardLULZ for assisting with music docs and code review
- chris for making GB Studio
- GB Studio community for being awesome!
- and AntonioND for making GBT Player

## What are these templates for?

If you use MilkyTracker, you can save yourself some time when composing for GBT Player by using these templates. Normally you'd have to hit "save as" on template.mod to work in .xm, but these templates have done it for you. MilkyTracker corrupts .mod files if they are opened and then "save" is pressed, which is why you want to work in the. xm format.

**Basically,** you can hit "save as" on any file to convert to a different file extension, just *never* hit "save" on a .mod file in Milkytracker. Work in .xm files and "save as" .mod when you want to test your song in-game.

## Why do we need templates?

First of all, any GB Studio composers should know that GB Studio relies entirely on GBT Player for .mod file playback. Second of all, GBT Player users should know that it does not read custom sampledata from the .mod file you're making.

GBT Player has a bunch of pre-baked instruments to be called upon, so you're just writing the note, instrument and effect data with the .mod format. These .xm files contain instruments that are examples of what you will hear when your .mod file is played back with GBT Player.

## Which template should I use?

tastytemplate.xm was made to be more useful than template.mod is on its own. If you're reading this, you should use it to save yourself the hassle. template.xm only exists to show the preservation of template.mod to the .xm format in MilkyTracker, and it contains note data that is not necessarily helpful but is kept for historical reasons.

tastytemplate is my own concoction of tweaks to the template to make it much easier to compose. Here's what I changed:

**Instrument Names**

richardLULZ and I analysed the results of GBT's instrument test file in Audacity, and we have given all the wave channels their own names. The noise channels were harder to identify, so I gave them nicknames so they are easier for composers to conceptualise how they can be used. richardLULZ provided really useful information on how they're generated too, which is currently in the gb-studio-site music docs. The noise channel sounds are very uncommon to our ears (except the white noise channel) so this is where I stepped in with artistic liberties. You can rename them however you like, I just wanted *something* better than "ch15" "ch16" "ch17" "ch18" etc.

**Samples and Tuning**

The pulse channels have their 256-sample recordings removed in favour of 32-sample ideal waveforms. It's been infuriating to compose with these out-of-tune recordings and these pulses were super simple to make. I understand that the wave instruments have all been slightly detuned to match the pitch of the pulse channels, but channel 3's square instrument (Ehx / 14 in base10) was way out of tune with the rest, so this instrument got simplified to 32 samples as well (with no instrument detuning).

**All channels have muted notes at C4 with various instruments**

I hope this gets the idea across about what instruments can be used on which channels better. I really wish we could make comments in these things, but MilkyTracker isn't about comments I guess.

Alright, back to talking about both templates at once:

## How are these different from the existing template.mod?

Normally composers can load template.mod that's included with GBT Player and all of GB Studio's new projects so they have access to all of these example instruments, but if you're a Milkytracker user you'll soon discover that Milkytracker corrupts .mod files if the save button is pressed Milkytracker. A corrupted .mod sounds like fast, high-pitched squeaks followed by silence when played by GBT Player. The workaround is just to use "save as" to convert a .mod into an .xm file, and to only press "save" when working in the .xm file. When you want to test your song you'd press "save as" to turn your .xm file into a .mod file for GBT Player.

These .xm templates have the first step done for you, but you will still need to press "save as" to create a .mod file when you want to test your song.

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
