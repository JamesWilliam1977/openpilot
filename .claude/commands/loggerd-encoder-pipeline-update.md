---
name: loggerd-encoder-pipeline-update
description: Workflow command scaffold for loggerd-encoder-pipeline-update in openpilot.
allowed_tools: ["Bash", "Read", "Write", "Grep", "Glob"]
---

# /loggerd-encoder-pipeline-update

Use this workflow when working on **loggerd-encoder-pipeline-update** in `openpilot`.

## Goal

Adds or modifies components in the loggerd encoder pipeline, often touching multiple C++ source/header files and build scripts.

## Common Files

- `openpilot/system/loggerd/encoder/v4l_decoder.cc`
- `openpilot/system/loggerd/encoder/v4l_decoder.h`
- `openpilot/system/loggerd/encoder/v4l_encoder.cc`
- `openpilot/system/loggerd/encoder/v4l_encoder.h`
- `openpilot/system/loggerd/clip_encoder.cc`
- `openpilot/system/loggerd/clip_encoder.h`

## Suggested Sequence

1. Understand the current state and failure mode before editing.
2. Make the smallest coherent change that satisfies the workflow goal.
3. Run the most relevant verification for touched files.
4. Summarize what changed and what still needs review.

## Typical Commit Signals

- Edit or add C++ source/header files in openpilot/system/loggerd/encoder/ (e.g., v4l_decoder.cc, v4l_decoder.h, v4l_encoder.cc, v4l_encoder.h).
- Edit or add related files in openpilot/system/loggerd/ (e.g., clip_encoder.cc, clip_encoder.h, encoderd.cc, video_writer.cc, video_writer.h).
- Update build scripts (SConscript) as needed.
- If applicable, update tools/replay/ files for replay support.

## Notes

- Treat this as a scaffold, not a hard-coded script.
- Update the command if the workflow evolves materially.