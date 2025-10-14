# Nord Sample Editor Project to SFZ Converter

## [ >>>> CONVERTER HERE <<<< ](https://bartbral.github.io/Nord-Sample-Editor-Project-to-SFZ-Converter)

A simple web-based converter that transforms [Nord Sample Editor `.nsmpproj` project files](https://www.nordkeyboards.com/software/nord-sample-editor-4) into the [SFZ multisample format](https://sfzformat.com).

## Features

- Load your Nord .nsmpproj project file directly from your browser
- Automatic conversion to a minimal SFZ-file with loop points, key ranges, and tuning etc. (see list below)
- Regions are sorted by root-key for logical ordering 
- Musical note key ranges are displayed as comments for clarity 
- Preview the generated SFZ text in the browser
- Copy SFZ text to clipboard or save the .sfz file with the same name as input-file, to your downloads folder
- Works fully offline once loaded — no server required
- No data gets uploaded to ze interwebs, all .nsmpproj and .sfz info stays on your computer


## Supported SFZ opcodes
| SFZ Opcode      | Description                              | .nsmpproj field            |
|-----------------|----------------------------------------|----------------------------------------|
| sample          | Path or filename of the sample WAV     | `m_fullName` (in `audio_file` block)   |
| offset          | Sample offset (start sample frame)     | `m_start` (in `common_stroke`)          |
| end             | Sample end (stop sample frame)         | `m_stop` (in `common_stroke`)           |
| pitch_keycenter | MIDI note number of key center         | `m_rootKey` (in `map_zone`)             |
| lokey           | Lowest MIDI note in region              | `m_btmNote` (in `map_zone`)             |
| hikey           | Highest MIDI note in region             | `m_topNote` (in `map_zone`)             |
| tune            | Pitch tuning in cents                   | `m_detune` (in `map_stroke`)            |
| loop_start      | Sample frame for loop start              | `m_loopStart` (in `common_stroke`)      |
| loop_end        | Sample frame for loop end (calculated)  | `m_loopStart + m_loopLengthLong - 1`    |
| loop_crossfade  | Loop crossfade length in samples        | `m_loopXFadeLengthLong` (in `common_stroke`) |
| loop_type       | Loop direction (usually 'forward')       | Derived from `m_loopEnabled`             |
| loop_mode       | Loop mode (e.g., 'loop_continuous')      | `m_loopEnabled` and `m_isOneShot` flags  |


## Why?
[Nord Sample Editor](https://www.nordkeyboards.com/software/nord-sample-editor-4) a free, and amazingly simple-to-use program designed for sending multi-samples to Nord synthesizers, featuring a clear and user-friendly interface and a musician-friendly user experience. 

You can directly record into this program, and the software will automatically select the sample tone/note/slices data between the silences, looks for the most likely root-key, and automaps this to key-ranges. There is also a quite nice loop option with loop-crossfade option. 

NSE-Projects save detailed multisample instruments but lack a convenient way to export to the widely supported SFZ format. This tool bridges that gap with a simple interface. Please be aware that this converter in no way converts the proprietary Nord sample files (.nsmp) but uses the raw-text-data saved in the project-files (.nsmpproj) and links this to your samples, and other sfz-opcodes. Samples stored on your Nord-synth can not be sent back to your computer, or anything like that. 

# Usage

0. Use the wonderful and free [Nord Sample Editor-software](https://www.nordkeyboards.com/software/nord-sample-editor-4) to make a multisample, and save the project file. Then consolidate the project so all used samples are put into the same folder in the folder where the .nsmpproj project file lives. All info you need to do this can be found on their website. 
1. Open [ => this page <= ](https://bartbral.github.io/Nord-Sample-Editor-Project-to-SFZ-Converter) in a modern web browser
2. Click “Choose File” and select your `.nsmpproj` project file
3. View converted SFZ regions and details instantly on page.
4. Copy the SFZ text to clipboard or download the `.sfz` file.
5. Now put the downloaded .sfz-file into the same folder as your original .nsmpproj project file.
6. Test your sfz-file in your favorite player.

## License

MIT License — free and open source. Contributions welcome!
---
Feel free to open issues or pull requests for feature requests or bug reports... but be aware that code was about 99% created by AI, so most likely I don't know! ;)


---

## Disclaimer:
Nord Sample Editor and the Nord name are registered trademarks of Clavia Digital Musical Instruments AB. This project is an independent tool and is not affiliated with, endorsed by, or sponsored by Clavia or Nord Keyboards in any way. All product names, logos, and brands are the property of their respective owners.
