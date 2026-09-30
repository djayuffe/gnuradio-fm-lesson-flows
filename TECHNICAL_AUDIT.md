# Technical Audit

This audit summarizes code, functions, and feature coverage for `gnuradio-fm-lesson-flows`.

## Scope

- Flowgraphs audited: 2 modern files plus archived originals in `flows/`.
- Tools audited: `tools/audit_flows.py` and `tools/validate_grc.py`.
- Reports regenerated locally before publication.

## Code and Function Review

- `tools/audit_flows.py` parses XML with `xml.etree.ElementTree`, hashes each file, lists block counts, connection counts, hardware endpoints, transmit-capable sinks, explicit file paths, duplicate block IDs, and exact duplicate payloads.
- `tools/validate_grc.py` uses the installed GNU Radio Companion core API, not text matching, to load, rewrite, and validate each modern `.grc` file.
- Shell examples avoid executing generated RF graphs automatically; generation and validation are separate from runtime operation.

## Feature Coverage

- Lesson starter and solution-style FM receiver graphs
- osmocom SDR source input
- Audio sink output
- Qt GUI spectrum display
- Preserved educational flowgraph structure

## Technical Parameters

| Flowgraph | Blocks | Connections | Key Parameters | Hardware/Audio Blocks | Transmit Blocks |
| --- | ---: | ---: | --- | --- | --- |
| `lesson1.grc` | 16 | 9 | channel_width=200e3; channel_freq=96.5e6; center_freq=97.9e6; samp_rate=20e6 | osmosdr_source_0 (osmosdr_source); audio_sink_0 (audio_sink) | - |
| `lesson1solution.grc` | 24 | 16 | samp_rate=4e6; center_freq=172.4e6; channel_width=200e3 | audio_sink_0 (audio_sink); osmosdr_source_0 (osmosdr_source) | - |

## Known Operational Gaps

- Runtime hardware behavior is not asserted by validation; actual SDR/audio devices must be configured locally.
- External sample/capture files named in legacy graphs are not bundled unless present in `flows/`.
- Transmit-capable graphs require separate RF lab controls and legal authorization.

## Verification

- `VALIDATION.md` has no `Result: FAILED` entries.
- `SHA256SUMS.txt` verifies all committed files.
