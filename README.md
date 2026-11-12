# No-bat sounds

Recordings with no bats in them, recorded at 96 kHz or more, for testing
[Oversample](https://oversample.com)'s bat call detector and sound
classifiers. Any "bat call" the detector finds here is a false positive.

In bioacoustics these are usually called non-target sounds; in machine
learning, negative examples (hard negatives when they fool the detector).

## Contents

| Source | Files | What |
|---|---|---|
| xeno-canto | 69 | Insects (bush-crickets, grasshoppers), shrews and other land mammals, birds, frogs; 192 kHz or more |
| Sonniss #GameAudioGDC bundles | 27 | Sound effects: water, rain and hail, crickets, electrical noise, drones, vehicles, power tools, birds, handling noise |
| Signature Sounds | 10 | Shopping centre and coffee kiosk ambiences, 96 kHz |

`index.json` lists every file. Each audio file has a metadata sidecar:

- `NAME.xc.json`: xeno-canto metadata, including `lic` (licence URL), `rec`
  (recordist) and `grp` (group).
- `NAME.sfx.json`: sound effect metadata: `kind`, `bundle`, `library` (the
  recordist or label), `original_file`, the excerpt's start and length,
  `licence`, and how many bat calls detector calls-3 found in the full
  original file.

## Sound effects

Each sound effect is an excerpt of at most 30 s from the original, first
channel only, at the original sample rate and bit depth. The excerpt is the
30 s window where the call detector found the most bat calls.

The Sonniss files were chosen from 3,830 at 96 and 192 kHz, of which 42%
gave false bat calls. Synthesised-sounding ambiences were left out. The
Signature Sounds files are the 10 of 37 mall recordings with the most false
bat calls.

## Licences

- **xeno-canto recordings**: Creative Commons, one licence per file (in its
  `.xc.json`): 56 CC BY-NC-SA 4.0, 8 CC BY-NC-ND 4.0, 4 CC BY-SA 4.0,
  1 CC BY-NC 4.0. Credit the recordist when using them.
- **Sonniss sound effects**: the Sonniss #GameAudioGDC bundle licence
  (`licences/sonniss-gdc-eula.pdf`). It allows use and redistribution in any
  medium without attribution, but not selling the sounds on their own, and
  copyright stays with each recordist. The recordist or label is in each
  file's `.sfx.json` (`library`).
- **Signature Sounds recordings**: CC0 1.0, from the
  [Mall Recordings Sample Pack](https://signaturesounds.org/mall-recordings-sample-pack-cc0-free-to-download).

## Adding recordings

- xeno-canto: `cargo run -p xc-cli -- fetch <XC number> --cache-dir <this folder>`
  from the Oversample repo, then add the file to `index.json`.
- Your own recordings: see `RECORDING.md` for what to record.
- Sound effects or your own recordings: add the WAV, a `.sfx.json` sidecar
  and an `index.json` entry. Only add files whose licence allows
  redistribution.
