# Seeing Lab

Four short browser activities for the combined session on sensory systems and vision
(Sessions 13–14) of *Introduction to Neuroscience* (Krea University). Students use it
beside the slides. Built with jsPsych 7.3.4; nothing to install.

1. **The hole in your eye.** Students size the screen with a bank card or ruler (an
   ID-1 card is 8.56 cm wide), enter their viewing distance, cover the left eye and map
   their own blind spot with two sweeps of a moving dot (out, then back in). Averaging
   the two sweeps cancels reaction time. Then a filling-in test places a grey disc on
   stripes inside the measured blind spot.
2. **Kuffler's cat.** Recording from a model retinal ganglion cell: spot size, a ring on
   the surround, and a light/dark edge, with a raster of 5 flashes and a tuning graph
   that builds as students record. Cell A is ON-centre; students work out that Cell B
   is OFF-centre. Optional clicks for spikes.
3. **Same grey?** Simultaneous brightness contrast measured by method of adjustment
   (one check trial with equal surrounds, three test trials), then a Mach-band staircase
   with the luminance profile and the response of a row of model ganglion cells.
4. **Tire out your cones.** Three 20-second fixations on coloured discs (red, yellow,
   green), then students report the afterimage colour. Nothing flashes; there is a skip
   button.

**Pacing:** each part opens only with a password the teacher shows on that part's lab
slide (default words: `lantern`, `pebble`, `harbour`, `violet`). Once unlocked, a part
stays unlocked in that browser tab; the free lab at the end is never locked. To change
the words, edit `PASSWORDS` in `index.html` (search for `var PASSWORDS`) and the matching
`\pwone` to `\pwfour` in the slides. Letter case and spaces are ignored. This paces the
class; it is not security.

**Privacy:** nothing is saved or sent. Everything runs in the student's browser tab.

**Devices:** Part 1 needs about 20° of screen to the right of the cross. Laptops are
fine at 50 cm; phones should be turned sideways at about 30 cm. If the screen is too
narrow, the lab says so. Parts 1 and 4 offer example data or a skip button for anyone
who cannot or prefers not to do the fixation tasks.

## The models

- **Part 1** is a measurement, not a model. Angles are computed as
  atan(on-screen distance / viewing distance). The dot runs along a line 1.5° below the
  fixation cross, because the blind spot's centre sits about 1.5° below the horizontal
  and 12–15° to the temporal side. Accuracy depends on the card sizing and the distance
  estimate.
- **Part 2** is a difference-of-Gaussians receptive field (centre σ = 0.5°, surround
  σ = 1.5°, surround weight 0.85 of the centre). Resting rate is 15 spikes/s; drive adds
  70 spikes/s per unit while the light is on (never below zero), and for 0.25 s after
  light-off there is a rebound of half that size in the opposite direction (the "off"
  discharge). Spikes are Poisson. The best spot is about 2.4° across (about 65 spikes/s);
  whole-screen light gives about 25 spikes/s. These numbers are illustrative, not fitted
  to a particular cell.
- **Part 3** shows plain greys. Results depend on the screen and room lighting, so the
  lab reports the student's own illusion size rather than marking it right or wrong. The
  Mach-band "model cells" curve is the staircase convolved with the same
  difference-of-Gaussians profile as Part 2, scaled to the band width.
- **Part 4** shows colours with a fixation dot; the "many people see" column gives the
  usual complementary afterimages (red → blue-green, yellow → blue, green → pink-purple).

## Running it

Upload this folder to a GitHub repository and turn on GitHub Pages (Settings → Pages →
deploy from branch, root). The lab will be at `https://<user>.github.io/<repo>/`.
Locally, run `python3 -m http.server` in this folder and open `http://localhost:8000/`.
Adding `?fast=1` to the address shortens the timed waits; it is only for testing.

jsPsych is distributed under the MIT licence (`lib/LICENSE-jsPsych.txt`).
