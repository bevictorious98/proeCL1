# Gravity Build — prompts

Model target: **Seedance 2.5**, 15 s.

- **Primary**: first/last-frame mode. The start frame is a generated bare-plot image,
  and the last frame is `references/exterior-hero.jpg`, unmodified. This is the only mode that
  guarantees the brief's "settles on a hero view exactly as in Image 1".
- **Fallback**: reference mode, with `exterior-hero.jpg` passed as `@Image1`.

Neither video prompt contains double quotes. Seedance treats quoted phrases as requests
to render text on screen.

## 1. Start frame (image/nano-banana-2, 16:9, 1K, thinking high, exterior-hero.jpg as reference)

```
Use the reference photo only to match the location, camera heading, sky colour, cloud placement, warm afternoon sunlight from behind the camera on the right, colour grade and the mature tree. Do not copy its framing. Remove the building, canopy, glazing, copper screen, landscaping, driveway, curbs, bollards, car and people entirely, and show this same site before construction began.

Photorealistic 16:9 frame from an FPV drone at the very start of a fast, low flight, about 0.7 m above the ground.

Camera: it faces the same direction as the reference photo but is much lower and about 30 m further back, so a wide empty plot stretches out ahead. The horizon is level and sits slightly above the middle of the frame.

Ground: a bare, flat, levelled construction plot of dry, compacted pale-tan earth and fine gravel, covered in loose dust, with faint tyre tracks. A few wooden survey stakes with taut string mark a long, low rectangular building footprint. It begins in the middle distance just right of the tree and runs away to the right.

Tree: the same mature deciduous tree, with slender pale trunks and airy yellow-green foliage. Seen from further back, it stands about 40 m ahead, about a third of the way in from the left edge, at the edge of the plot.

Background: a low belt of dark-green trees on a flat horizon; no buildings, no hills.

Sky and light: clear, saturated blue sky, deeper at the top and paler near the horizon, with a few small soft white clouds in the upper right. Warm afternoon sun from behind the camera's right shoulder lights the camera-facing sides of the stakes and the tree with golden light; soft shadows fall to the left and slightly away from the camera. The sun itself stays out of frame, with no lens flare. A thin haze of sunlit dust hangs just above the ground.

Lens: slight forward motion blur on the nearest ground at the bottom edge; everything beyond it is crisp. Natural colours, rectilinear wide-angle lens, no fisheye distortion.

The site is completely empty: no building, no foundations, no construction materials, no machinery, no cranes, no vehicles, no people, no text, no logos, no watermark.
```

## 2. Primary video prompt (first/last frame)

```
One continuous, uncut, ultra-dynamic 15-second FPV drone shot: a modern training center builds itself from materials falling out of a clear blue sky. It starts exactly on the first frame, an empty dusty plot, and ends exactly on the final frame, the finished building in a calm three-quarter hero view. The camera faces into the site throughout, flying forward into the building, then pulling back out and swinging right to the hero spot.

0-3 s: The drone skims fast and low over the bare, dusty plot, racing past the lone mature tree on its left. Bricks, concrete blocks, rebar and steel beams rain down out of the sky and slam into place as footings and a ground slab, each impact kicking up a burst of sunlit dust.

3-7 s: Concrete columns and a steel frame shoot up all around the camera and stop dead: a tight grid for the two-storey head on the left, long rows for the wing on the right. The drone weaves between them and climbs through the open frame of the head to roof height, then dives back to the ground floor as the head's floor slab slams down above it. Then the roofs slam down, higher on the head, lower on the wing, which stays one tall open hall.

7-11 s: The drone bursts out backward at ground level, still facing in, through the open, unglazed two-storey entrance on the head's left face into bright daylight at about 8 s. The envelope flies in from all sides and locks on in front of the lens with crisp mechanical precision: floor-to-ceiling glass slides into the entrance and across both floors of the head, clean and intact; the perforated copper screen swings into its frame; white faceted panels lock edge to edge into the tall blade-like prow; light-grey panels and a clerestory window ribbon clad the wing; last, the copper entrance canopy flies in on its slanted silver column and locks on over the entrance. Warm interior lights come on.

11-15 s: Still facing the building, the drone pulls back, swings out to the right, wide of the tree, and rises in a sweeping arc that reveals the whole wing. Asphalt, white curbs and black bollard lights drop into place along the curving driveway; conifers land root-ball first and sway, boulders thud, ornamental grasses settle. A dark-grey metallic sedan rolls in from the left edge and parks at the lower left, and a few staff and students step out to the entrance doors. By 13 s everything is in place and the dust has cleared; the arc crests at about the head's roofline, roughly 10 m up, then glides down into a steady hold at low eye level by 14.5 s, looking slightly up at the head: the final frame.

Final state, as in the final frame: the tree at the far left; the glazed two-storey head with the copper canopy over its left-face entrance; the copper screen and white faceted prow where the head meets the wing; the lower, twice-as-long light-grey wing receding to the right.

Style: photorealistic, premium, elegant architectural film. Heavy pieces land with real weight and a dead stop; nothing floats or bounces. Raw concrete, steel, glass, matte light-grey aluminium, crisp white panels, warm copper. Unchanged daylight: clear blue sky, a few small clouds on the right, warm afternoon sun from behind the camera on the right, front-lighting the facades, shadows falling left. Real motion blur, smooth stabilised flight, crisp final hold.

Sound: rushing air, heavy impacts, metallic clicks of panels locking, then calm birdsong; no dialogue.

Constraints: one low, horizontal building throughout, a two-storey head and a long double-height wing, nothing taller; not a tower, not a hotel. One continuous take with no cuts or dissolves, assembled physically, piece by piece. Only the drone, the falling materials, the landscaping, the sedan and the few people move. No text, signage, logos or watermark.
```

## 3. Fallback video prompt (reference mode, @Image1 = exterior-hero.jpg)

```
One continuous, uncut, ultra-dynamic 15-second FPV drone shot: the training center from @Image1 builds itself from materials falling out of a clear blue sky, on one fixed footprint, under one sun. It opens on an empty, dusty plot where no part of the building exists yet and ends on the three-quarter hero view of @Image1. The camera faces into the site throughout, flying forward into the building, then pulling back out and swinging right to the hero spot.

0-3 s: The drone skims fast and low over the bare, dusty plot, racing past a lone mature tree with airy yellow-green foliage on its left. Bricks, concrete blocks, rebar and steel beams rain down out of the sky and slam into place as footings and a ground slab, each impact kicking up a burst of sunlit dust.

3-7 s: Concrete columns and a steel frame shoot up all around the camera and stop dead: a tight grid for the two-storey head on the left, long rows for the wing on the right. The drone weaves between them and climbs through the open frame of the head to roof height, then dives back to the ground floor as the head's floor slab slams down above it. Then the roofs slam down, higher on the head, lower on the wing, which stays one tall open hall.

7-11 s: The drone bursts out backward at ground level, still facing in, through the open, unglazed two-storey entrance on the head's left face into bright daylight at about 8 s. The envelope flies in from all sides and locks on in front of the lens with crisp mechanical precision: floor-to-ceiling glass slides into the entrance and across both floors of the head, clean and intact; the perforated copper screen swings into its frame; white faceted panels lock edge to edge into the tall blade-like prow; light-grey panels and a clerestory window ribbon clad the wing; last, the copper entrance canopy flies in on its slanted silver column and locks on over the entrance. Warm interior lights come on.

11-15 s: Still facing the building, the drone pulls back, swings out to the right, wide of the tree, and rises in a sweeping arc that reveals the whole wing. Asphalt, white curbs and black bollard lights drop into place along the curving driveway; conifers land root-ball first and sway, boulders thud, ornamental grasses settle. A dark-grey metallic sedan rolls in from the left edge and parks at the lower left, and a few staff and students step out to the entrance doors. By 13 s everything is in place and the dust has cleared; the arc crests at about the head's roofline, roughly 10 m up, then glides down into a steady hold at low eye level by 14.5 s, looking slightly up at the head: the three-quarter hero view exactly as in @Image1.

Final state, identical to @Image1, left to right: the tree at the far left edge; the two-storey head, glazed floor-to-ceiling with slim dark mullions under a thick white fascia, with a wedge-shaped copper-soffit canopy on one slanted silver column over the entrance on its left face; a full-height perforated copper screen and a white faceted prow where the head meets the wing; the lower, twice-as-long light-grey wing, one double-height storey with a high clerestory ribbon and a grey sectional door at the far end, receding to the right edge; planted beds, boulders and the sedan in the foreground; blue sky with a few small clouds on the right.

Style: photorealistic, premium, elegant architectural film. Heavy pieces land with real weight and a dead stop; nothing floats or bounces. Raw concrete, steel, glass, matte light-grey aluminium, crisp white panels, warm copper. Unchanged daylight as in @Image1: warm afternoon sun from behind the camera on the right, front-lighting the facades, shadows falling left. Real motion blur, smooth stabilised flight, crisp final hold.

Sound: rushing air, heavy impacts, metallic clicks of panels locking, then calm birdsong; no dialogue.

Constraints: one low, horizontal building throughout, a two-storey head and a long double-height wing, nothing taller; not a tower, not a hotel. One continuous take with no cuts or dissolves, assembled physically, piece by piece. Only the drone, the falling materials, the landscaping, the sedan and the few people move. No text, signage, logos or watermark.
```

### Optional forward-exit swap (reference mode only)

Do not use it in first/last-frame mode. It adds about 360 degrees of total yaw between two frames that share a heading. Make all three replacements in fallback_video_prompt:
(1) Opening: replace 'The camera faces into the site throughout, flying forward into the building, then pulling back out and swinging right to the hero spot.' with 'The drone flies forward into the building, whips round inside the lobby, shoots out of the entrance, then banks right, wide of the tree, in a wide turn to face the building.'
(2) 7-11 s: replace its first two sentences, from 'The drone bursts out backward' through 'in front of the lens with crisp mechanical precision:', with 'At ground level the drone whips round inside the lobby to face the entrance and shoots forward out through the still-open doorway of the two-storey entrance on the head's left face into bright daylight at about 8 s, then banks right, wide of the tree, in a wide turn to face the building. As it comes round, the envelope flies in from all sides and locks on in front of the lens with crisp mechanical precision:'. Keep the lock-on list unchanged; the glass still slides in clean and intact.
(3) 11-15 s: replace its first sentence with 'Now facing the building, the drone pulls back and rises in a sweeping arc that reveals the whole wing.'
