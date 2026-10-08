# Gravity Build — 15 s FPV prompt

Model target: **Seedance 2.5**, reference-to-video, 16:9, 15 s.
Reference: `@Image1` = `references/exterior-hero.jpg`.

The floor plans (`references/plan-*.jpg`) are **not** passed to the model: they are
full of Cyrillic labels and coloured room fills that tend to leak into the frame.
Their layout is written into the prompt as text instead.

## Prompt

```
One continuous, uncut, ultra-dynamic 15-second FPV drone shot, a single take with no cuts: a "gravity build" in which the modern training center from @Image1 assembles itself from materials falling out of the sky.

The building (match @Image1 exactly): a two-storey head volume on the left with floor-to-ceiling glazing on both floors, wrapped by a white faceted corner volume made of sharp angled planes; a tall perforated copper screen panel set between the glazing and the white corner; a cantilevered copper-clad entrance canopy carried by one slanted white column over the two-storey glass entrance. Attached on the right, a long, low, light-grey panelled workshop wing, one tall storey high, with a continuous ribbon of clerestory windows near the top and a large grey sectional door at the far end. Flat roofs throughout. In front, a curving asphalt driveway with bollards, landscaped beds of conifers, large boulders and ornamental grasses.

0-3 s: The drone skims fast and low over a bare, dusty, levelled construction plot under a clear blue sky. Bricks, concrete blocks, bundles of rebar and steel beams rain down out of the sky and slam into place in neat rows, every impact kicking up a puff of dust as the foundations and ground slab form.

3-7 s: Concrete columns and a steel frame shoot up out of the ground all around the camera; floor slabs and then the roof deck drop from above and land precisely on top of them with heavy, dusty impacts. The drone weaves between the columns and climbs up through the open skeleton of the two-storey volume.

7-11 s: Light-grey facade panels, the white faceted corner volume, floor-to-ceiling glass panes, the perforated copper screen and the copper entrance canopy on its slanted column fly in from all sides and lock into position with crisp mechanical precision, closing the building around the camera. The drone bursts out through the two-storey glass entrance, under the copper canopy, into bright daylight.

11-15 s: The drone pulls back and rises in a smooth sweeping arc while conifers, boulders and ornamental grasses drop onto the landscaped beds along the driveway and land softly. The motion decelerates and settles on a calm, steady three-quarter hero view of the finished building, matching @Image1 in composition, materials and light.

Style: photorealistic, premium, elegant architectural film. Realistic concrete, steel, glass, matte light-grey aluminium panels and warm copper; natural daylight with soft shadows, clear blue sky with a few light clouds; real motion blur and FPV speed with smooth stabilisation.

Sound: rushing air, heavy concrete and steel impacts, metallic clicks of panels locking in, a soft glass chime, then calm outdoor ambience at the end.

Constraints: exactly one building, two storeys with a long low workshop wing; not a tower, not a high-rise, not a hotel, no extra floors. No cuts, no text, no lettering, no signage, no logos, no watermark, no floor-plan graphics.
```
