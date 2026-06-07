# The Schwwaaa VideoSampler 10 (VS10) TM

A self-contained HTML video sampler that runs entirely in the browser. Load a local video, drop cue markers on the timeline, assign them to keyboard pads, play them live, build sequences, record jam performances, and export everything as JSON.

screenshot here

## Quick Start

1. Download or clone the project.
2. Open `index.html` in a modern browser.
3. Click **Choose File** and select a local video.
4. Add markers or click **Auto-slice 10**.
5. Trigger pads with keys `1–0`.
6. Record, sequence, save, reload, repeat.

## Controls

| Action                        | Control                         |
| ----------------------------- | ------------------------------- |
| Play / pause video            | Spacebar or Play / Pause button |
| Add marker                    | `M` or Add Marker button        |
| Add marker on timeline        | Shift + click timeline          |
| Seek timeline                 | Click timeline                  |
| Trigger pads                  | `1 2 3 4 5 6 7 8 9 0`           |
| Start / stop jam recording    | `R`                             |
| Load recorded jam to sequence | `L`                             |
| Nudge playhead                | `-1s` / `+1s` buttons           |

## Workflow

### 1. Load a Video

Use the file picker to load any browser-supported video file. The video stays local. The app creates a temporary object URL in your browser and does not upload anything.

### 2. Create Markers

Markers are cue points. Each marker has:

* Label
* Pad assignment
* Start time
* Duration

You can create markers manually at the playhead, Shift-click them onto the timeline, or auto-slice the whole video into 10 pads.

### 3. Assign Pads

Each marker can be assigned to one pad key. Pads use keys:

```text
1 2 3 4 5 6 7 8 9 0
```

Only one marker can own a pad at a time. If you assign a used pad to a new marker, the previous marker is unassigned.

### 4. Play Cues

Click a pad or press its key. The video jumps to that marker and plays for the marker duration.

Optional playback modes:

* **Stop at cue end**: pauses playback when the cue duration ends.
* **Loop selected cue**: repeatedly plays the selected marker.

### 5. Build a Sequence

Add pad cues into the sequence panel. Each sequence step can have a custom playback length independent of the marker’s cue duration.

Sequence steps can be:

* Played individually
* Reordered
* Duplicated
* Deleted
* Edited for duration

### 6. Record a Jam

Click **Record Jam** or press `R`, then trigger pads live. The app records the timing of your pad hits and turns the performance into a reusable sequence.

After recording, you can:

* Play the recorded jam directly
* Load it into the editable sequence
* Save it as JSON

## Saving Projects

Click **Save Project JSON** to export:

```json
{
  "version": 1,
  "markers": [],
  "sequence": [],
  "lastRecordedSequence": [],
  "jamEvents": []
}
```

This saves your marker map, current sequence, recorded jam sequence, and raw jam events.

To restore a project, click **Load Project JSON** and select a previously saved project file.

## Saving Recorded Jams

Click **Save Recorded Jam JSON** to export only the most recent recorded jam:

```json
{
  "version": 1,
  "type": "recorded_jam",
  "recordedJam": []
}
```

This is useful for saving performances separately from the full project state.

## Notes

This is currently a single-file prototype. Everything lives in one HTML file: structure, styling, and JavaScript logic.

That makes it easy to run, share, remix, and break apart later.

Possible next steps:

* Add waveform or thumbnail timeline previews
* Add import for recorded jam JSON
* Add MIDI controller support
* Add pad colors
* Add per-pad volume or speed
* Add export to EDL, CSV, or video edit formats
* Package as a reusable JavaScript library
* Add persistent browser storage
* Add project names and metadata

## Browser Support

Use a current desktop browser such as Chrome, Edge, Firefox, or Safari. Supported video formats depend on the browser.

## License

Add your preferred license here.
