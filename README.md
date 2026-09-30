# GNU Radio FM Lesson Receiver Flows

Modernized GNU Radio lesson flowgraphs for FM receiver practice and solution comparison.

This public repository is split from the audited `modern-gnuradio-sdr-flows` workspace. It keeps a focused GNU Radio Companion flow family with archived originals in `flows/` and validated modern ports in `modern/`.

## Features

- Lesson starter and solution-style FM receiver graphs
- osmocom SDR source input
- Audio sink output
- Qt GUI spectrum display
- Preserved educational flowgraph structure

## Standards and Signal Context

- Wideband FM receiver lesson patterns
- Broadcast FM-style channel widths in the starter graph
- GNU Radio Companion XML validated with GNU Radio 3.8.5.0

## Flowgraph Inventory

| Flowgraph | Blocks | Connections | Key Parameters | Hardware/Audio Blocks | Transmit Blocks |
| --- | ---: | ---: | --- | --- | --- |
| `lesson1.grc` | 16 | 9 | channel_width=200e3; channel_freq=96.5e6; center_freq=97.9e6; samp_rate=20e6 | osmosdr_source_0 (osmosdr_source); audio_sink_0 (audio_sink) | - |
| `lesson1solution.grc` | 24 | 16 | samp_rate=4e6; center_freq=172.4e6; channel_width=200e3 | audio_sink_0 (audio_sink); osmosdr_source_0 (osmosdr_source) | - |

## File and Capture Paths

- `lesson1.grc`: no explicit file paths found
- `lesson1solution.grc`: no explicit file paths found

Update these paths before running graphs on a different machine. Generated files, captures, recordings, and raw samples are intentionally ignored by git.

## Usage Examples

```sh
# Validate modernized flowgraphs
/opt/local/Library/Frameworks/Python.framework/Versions/3.9/bin/python3.9 tools/validate_grc.py modern/* --report VALIDATION.md

# Generate Python without running RF hardware
mkdir -p generated
for f in modern/*; do /opt/local/bin/grcc -o generated "$f"; done

# Verify committed file integrity
shasum -a 256 -c SHA256SUMS.txt
```

To open a graph interactively:

```sh
gnuradio-companion modern/<flowgraph>.grc
```

To run generated Python, inspect the generated script first and confirm hardware, frequency, gain, sample rate, and file paths. Do not run transmit-capable graphs directly from generated code without RF isolation and legal authorization.

## Safety

Receive-only flows. Tune only to legal receive bands for your jurisdiction.

## Audit Status

- Archived originals parse as XML. See `AUDIT.md`.
- Modernized flowgraphs validate OK. See `VALIDATION.md`.
- Python generation was verified with GNU Radio Companion Compiler 3.8.5.0. See `COMPILE.md`.
- Checksums are tracked in `SHA256SUMS.txt`.

## Repository Layout

- `flows/` - archived original flowgraphs and related data files.
- `modern/` - modernized GNU Radio Companion flowgraphs for normal use.
- `tools/` - repeatable audit and validation helpers.
- `README.md` - usage and technical overview.
- `DESCRIPTION.md` - short project description.
- `AUDIT.md`, `VALIDATION.md`, `COMPILE.md` - generated audit/verification reports.

## License

No new license is asserted for the archived flowgraphs. Preserve original ownership/history before redistribution or publication.
