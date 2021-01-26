# Credits

**Ember:**

- `Ember Triangle.s` - The usual waveforms, but instrument 9 (Ringy) is replaced with a stuttery triangle wave that goes from 0hx to 8hx and back. I like low-fidelity triangle waves and this has been a long time coming.

## How to alter GBT Player Banks for Channel 3

[It is highly recomended you read the music documentation before continuing.](https://gbstudio.dev/docs/music)

GBT Player can be compiled to use a different set of 8 pre-determined waveforms for Channel 3, compared to the defaults that are mentioned in the music docs. This lets you edit all 8 waveforms for Channel 3 on a per-game basis. These 8 waveforms can not be swapped-out during gameplay.

After using Engine Eject (2.0.0 and above) the file `gbt_player_bank1.s` can be found inside of `assets/engine/src/core`. Lines 40 to 47 contain sets of nibbles that determine the waveform shape for each of Channel 3's instruments.

Each line contains 32 nibbles joined together in groups of 2. Each nibble represents the amplitude of a sample from 0 to F.

**Example:**  
```
gbt_wave: ; unofficial edit
	.DB	0xFF,0xFF,0xFF,0xFF,0xFF,0xFF,0xFF,0xFF,0x00,0x00,0x00,0x00,0x00,0x00,0x00,0x00 ; square wave
	.DB	0x79,0xBC,0xDE,0xEF,0xFF,0xEE,0xDC,0xB9,0x75,0x43,0x21,0x10,0x00,0x11,0x23,0x45 ; sine wave
	.DB	0xFF,0xEE,0xDD,0xCC,0xBB,0xAA,0x99,0x88,0x77,0x66,0x55,0x44,0x33,0x22,0x11,0x00 ; sawtooth
	.DB	0x00,0x11,0x22,0x33,0x44,0x55,0x66,0x77,0x88,0x77,0x66,0x55,0x44,0x33,0x22,0x11 ; triangle
	.DB 0xFE,0xDC,0xBA,0x98,0x76,0x54,0x32,0x10,0x12,0x34,0x45,0x56,0x78,0x9A,0xBC,0xDE ; double-speed triangle
```

**Example**: 0xFF represents two samples of maximum amplitude. One set to `F` amplitude, the other set to `F` amplitude.  
**Example**: 0x00 represents two samples of minimum amplitude. One set to `0` amplitude, the other set to `0` amplitude.  
**Example**: 0x0F represents two samples of mixed amplitude. One set to `0` amplitude, the other set to `F` amplitude.  

So long as the formatting of the nibbles remain the same, their values can be changed to any 16-bit value to create waveforms other than the GBT Player defaults. Changing the in-game samples here will not update the samples in template.mod, so adjust these samples with this in mind. hUGETracker features a sample-drawing tool that shows the necessary nibbles to create your desired waveform.

Here's a new waveform that can not be found in GBT Player by default:  
```
gbt_wave: ; unofficial edit
	.DB	0x00,0x11,0x22,0x33,0x44,0x55,0x66,0x77,0x88,0x77,0x66,0x55,0x44,0x33,0x22,0x11 ; triangle wave
```

Replacing one of the instruments with the above code will change the corrosponding instrument to your new waveform.
