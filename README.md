# Training Center — FPV "Gravity Build"

A 15-second, single-take FPV drone shot. The training center assembles itself from
falling materials and ends on the hero view in `references/exterior-hero.jpg`.

- `prompt.md`: the final prompts. It has the start-frame prompt, the primary video prompt
  (first/last-frame mode) and the fallback (reference mode).
- `references/exterior-hero.jpg`: the brief's Image 1. It is the literal last frame in the
  primary mode and `@Image1` in the fallback.
- `references/plan-*.jpg`: the floor plans. They are **not** sent to the model, because
  their Cyrillic labels and coloured fills conflict with "no text". Their facts are written
  into the prompt instead: two storeys only over the head, and a wing that is one tall
  double-height hall, lower than the head and about twice its length.
- `references/start-frame.jpg`: the generated bare-plot start frame. It passed the checks
  below and is centre-cropped to exactly 16:9 (1360x765).

## Status

Step 1 is done. The video is **not rendered yet**: the live quote for step 2 is 357 credits,
and the Creative Claw balance is 9. Higgsfield has 0 credits.

| Step | Model | Cost | State |
|---|---|---|---|
| 1. Start frame | `image/nano-banana-2`, 1K | 16 | done: `references/start-frame.jpg` |
| 2. Video draft | `video/seedance-2.5`, 15 s, 480p | 357 (live quote) | needs at least 348 more credits |
| 3. Finalize | same take at 1080p via `draft_job_id` | quote first | after the draft is approved |

Both frames are already uploaded to Creative Claw:

- Start frame (cropped): https://cdn.creativeclaw.co/u/f0e6eb31/images/676c0183-33f6-4c91-b014-37a550fbdded.jpg
- Hero / end frame: https://cdn.creativeclaw.co/u/f0e6eb31/images/31993bd0-c25c-4e54-9ca2-c2a28a11bcab.jpg

A cheaper preview is `video/minimax-h3-max-turbo` with the same two frames, at about 75 credits.
It is lower quality, but useful to test the camera path before paying for Seedance.

## Render steps (Creative Claw)

**Step 1, start frame (done).** To regenerate it, call `generate_image` with these parameters, using prompt §1 of `prompt.md`:

```json
{
  "model": "image/nano-banana-2",
  "aspect_ratio": "16:9",
  "extras": {
    "resolution": "1K",
    "thinking_level": "high",
    "image_urls": ["<exterior-hero.jpg URL>"]
  }
}
```

Before spending video credits, check the result for:
- no leftover building, glass, copper, asphalt or car
- the tree in the left third
- a level horizon
- sun from behind-right: lit faces toward the camera, shadows falling left, no flare
- a lower, pulled-back view, not the hero framing with the building erased

**Step 2, 480p draft.** Call `generate_video` with prompt §2 of `prompt.md`:

```json
{
  "model": "video/seedance-2.5",
  "prompt": "<prompt.md §2>",
  "image_url": "https://cdn.creativeclaw.co/u/f0e6eb31/images/676c0183-33f6-4c91-b014-37a550fbdded.jpg",
  "last_frame_url": "https://cdn.creativeclaw.co/u/f0e6eb31/images/31993bd0-c25c-4e54-9ca2-c2a28a11bcab.jpg",
  "duration": "15",
  "aspect_ratio": "auto",
  "resolution": "480p",
  "extras": { "generate_audio": true }
}
```

- Do not send `image_urls`. Literal frames cannot be combined with reference arrays,
  which is why §2 has no `@Image` tokens.
- Leave `omni_reference_task_type` unset; it applies only to reference mode.

**Step 3, review, then finalize at 1080p.** Check the draft for:
- a dissolve, warp or pop-in in the last 2 s
- a wing as tall as the head, or any extra floors
- the drone passing through a solid slab
- shattering glass
- the drone swinging right of the tree on the pull-back

If the draft is good, finalize the same take within 7 days. Get a quote with
`estimate_generation` first:

```json
{ "model": "video/seedance-2.5", "prompt": "<same prompt>", "extras": { "draft_job_id": "<draft jobId>" } }
```

### Higgsfield equivalent

```json
{
  "model": "seedance_2_5",
  "mode": "omni_reference",
  "medias": [
    { "value": "<start frame media_id>", "role": "start_image" },
    { "value": "<hero media_id>", "role": "end_image" }
  ],
  "duration": 15,
  "aspect_ratio": "auto",
  "resolution": "480p",
  "draft": true,
  "generate_audio": true
}
```

Before paying, confirm with a quote that `omni_reference` accepts `start_image` and `end_image`.

## If the draft fails

| Symptom | Fix |
|---|---|
| The building morphs in place or dissolves | Regenerate the start frame lower, further back, or turned 15–20° toward the wing; or use the reference-mode fallback (prompt §3) |
| The backward exit is garbled | Use the fallback with its forward-exit swap. The swap is not safe in first/last-frame mode |
| The car or people pop in during the last second | Delete those two clauses. The end frame still carries them |

Fallback call (reference mode, using prompt §3):

```json
{
  "model": "video/seedance-2.5",
  "prompt": "<prompt.md §3>",
  "image_urls": ["<exterior-hero.jpg URL>"],
  "duration": "15",
  "aspect_ratio": "16:9",
  "resolution": "480p",
  "extras": { "omni_reference_task_type": "reference", "generate_audio": true }
}
```

## Deliberate departures from the brief's wording

- "Bursts out through the glass entrance" is a **backward** exit at about 8 s, through the
  still-unglazed entrance. The camera keeps facing the building, so the cladding visibly
  locks on in front of the lens and no glass breaks. A forward exit would need about 360°
  of yaw between two frames that share a heading, and interpolation handles that badly.
- "Rises in a sweeping arc" crests at the head's roofline, about 10 m, then glides down to the
  low eye level of Image 1.
- The sedan and a few people from Image 1 arrive by 13.5 s, so the final hold matches the
  photo. No construction workers or cranes appear.
- The phrase "gravity build" is described in the prompt, not quoted, because quoted phrases
  can render as on-screen text.
