# osu!trainer+

A small Windows tool for osu!stable that lets you modify a beatmap's **rate/BPM, AR, OD, CS and HP**, with optional automatic note spacing to create easier or harder maps.

It detects the beatmap currently selected in osu!stable, generates a modified difficulty with your chosen settings, processes the audio to match the new rate, and packages everything into a new `.osz` ready to import into osu!.

## Features

- Modify playback rate from **0.5x to 2.5x**, or set a target BPM directly.
- Adjust **AR, OD, CS and HP** independently.
- Optional **AR/OD scaling** when changing rate.
- Adjustable automatic note spacing that preserves short streams/bursts, stacks, and slider shapes while adapting to playfield borders.
- Audio is automatically processed to match the selected rate.
- Optional pitch preservation when changing playback speed.
- Generates a **new `.osz` difficulty** without modifying the original beatmap.
- Automatically imports the generated `.osz` into osu! after generation.
- Automatically detects the beatmap currently selected in **osu!stable**.

## Requirements

- Windows
- osu!stable

The distributed executable includes the required FFmpeg binary for audio processing.

**osu!lazer is not currently supported.**

## Usage

1. Download `osu!trainer+.exe` from the [latest release](../../releases/latest).
2. Open **osu!stable** and select the beatmap you want to train.
3. Launch `osu!trainer+.exe`.
4. Adjust the rate/BPM and difficulty settings.
5. Enable spacing if desired and choose its intensity.
6. Generate the modified beatmap.
7. The generated `.osz` is automatically imported into osu! and can be played normally.

If osu!trainer+ cannot detect the currently selected beatmap, make sure osu! is running and, if necessary, run osu!trainer+ with administrator privileges.

## How it works

osu!trainer+ reads the currently selected beatmap from osu!stable and creates a modified `.osu` difficulty.

The transformation is applied in the following order:

**Rate → AR/OD/CS/HP → Spacing**

Spacing is applied after rate scaling so that stream and stack detection uses the timings and difficulty parameters of the resulting map.

For spacing, longer movements are scaled while short streams and bursts are protected. Sliders are translated as complete shapes, stacked objects are moved together, and spacing is reduced automatically when objects approach the playfield borders.

The modified difficulty, audio and referenced media are then packaged into a new `.osz` file.

## Credits

osu!trainer+ is based on [osu-crosscreenify](https://github.com/Seily/osu-crosscreenify) by **Seily**.

Additional training features are inspired by [osu-trainer](https://github.com/FunOrange/osu-trainer) by **FunOrange**.

## Disclaimer

This is a fan-made training tool, not affiliated with or endorsed by osu! or ppy.

Generated maps are modified versions of existing beatmaps and are intended for training and practice. Check the current osu! ranking criteria and rules before submitting or sharing modified maps in any official capacity.

## License

MIT — see [LICENSE](LICENSE).
