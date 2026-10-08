# Training Center — FPV "Gravity Build"

A 15-second, single-take FPV drone shot. The finished training center assembles
itself from falling materials, and the shot ends on the hero view in
`references/exterior-hero.jpg`.

- `prompt.md` is the final prompt, written for Seedance 2.5 reference-to-video.
- `references/exterior-hero.jpg` is `@Image1`, the building identity and the final frame.
- `references/plan-ground-floor.jpg` and `references/plan-second-floor.jpg` are the floor plans.
  They are used only to describe the footprint in text and are not sent to the model.

## Status

**Not rendered yet.** At the time of writing neither connected generator had
enough credits:

| Service | Model | Settings | Est. cost | Balance |
|---|---|---|---|---|
| Creative Claw | `video/seedance-2.5` | 15 s, 480p draft | ~360 | 25 |
| Creative Claw | `video/seedance-2.5` | 15 s, 1080p | ~1980 | 25 |
| Creative Claw | `video/minimax-h3-max` | 15 s, 480p | ~150 | 25 |
| Higgsfield | `seedance_2_5` | 15 s | — | 0 |

The cheapest path to 1080p is a 480p draft first. If the draft looks right,
finalize the same take to 1080p within 7 days by passing the draft's job ID as
`extras.draft_job_id`. Finalizing is billed as a separate job.

## Render parameters

Upload `references/exterior-hero.jpg` first. Then call the generator with the
prompt block from `prompt.md`.

Creative Claw `generate_video`:

```json
{
  "model": "video/seedance-2.5",
  "prompt": "<prompt block from prompt.md>",
  "image_urls": ["<uploaded exterior-hero.jpg URL>"],
  "duration": 15,
  "aspect_ratio": "16:9",
  "resolution": "480p",
  "extras": { "omni_reference_task_type": "reference", "generate_audio": true }
}
```

Higgsfield `generate_video`:

```json
{
  "model": "seedance_2_5",
  "prompt": "<prompt block from prompt.md>",
  "medias": [{ "value": "<exterior-hero.jpg media_id>", "role": "image_references" }],
  "mode": "omni_reference",
  "duration": 15,
  "aspect_ratio": "16:9",
  "resolution": "1080p"
}
```

## If the last frame drifts from the reference

Reference mode keeps the building's identity but may not land on the exact
framing. To guarantee the ending, switch to first/last-frame mode:

1. Generate a start frame: the same plot, bare and dusty, seen from a low FPV height.
2. Pass that start frame as `image_url` and `exterior-hero.jpg` as `last_frame_url`.
3. Drop `image_urls`. Seedance does not combine literal frames with reference arrays.
