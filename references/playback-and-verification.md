# Playback, implementation and verification

Read before building the presentation controller and preparing delivery.

## Separate the clocks

Keep three responsibilities distinct:

1. **Navigation:** selected section and explicit previous/next/chapter commands.
2. **Scene time:** coordinated local demonstrations, result holds and loop reset.
3. **Camera:** framing and the transition to a newly selected focus region.

With manual advancement, scene time wraps within the selected section. Reaching
the duration, scrubber end or loop reset must never invoke navigation. Persisting
the selected section in a URL/hash can make rehearsal and sharing easier.

If automatic advancement was requested, implement it explicitly as a separate
navigation policy with editable timings, pause/resume and clear handoffs. Do not
derive it accidentally from a component animation ending. Ask whether timing is
per section, per speaker or synchronised to narration. Choose a single source of
timing truth and make changing it possible without editing animation geometry.

## Deterministic scene behaviour

- Derive local visuals from scene time so seeking, pausing and replaying produce
  the same state. Avoid uncoordinated timers that drift between components.
- Pause must freeze meaningful local state. Decide whether section changes retain
  playback and position, and implement the agreed behaviour consistently.
- Handle return from a hidden tab without jumping across the presentation.
  Pausing on tab hiding is a useful default. Opening notes/settings should not
  quietly consume the presenter's scene time.
- Give loop resets their own short transition if needed; do not reuse section
  navigation or reveal hidden overview content during the reset.
- Store user-adjusted speed/timing preferences with validation and versioning when
  needed. Keep local storage failures from breaking presentation controls.

## Camera and responsive composition

Frame the current idea using its visible bounds, not the entire world. Connected
objects may remain visible together where their relationship is the explanation.
Constrain the camera's full travel when a later reveal must stay hidden.

Scale can be interpolated in logarithmic space to make large zooms more even.
Use one stable animation loop and frame-rate-independent timing; clamp abnormally
large frame deltas. Prefer transforms/opacity and profile expensive blur or SVG
filters. Keep moving blur bounded and return it to zero at rest. Do not leave
camera or local filters permanently applied after pause or resize.

Recompute composition from the current scene state on resize, including while
paused. Avoid fitting a dense desktop world onto mobile until everything becomes
unreadable; reframe, stack comparisons or use section-specific compositions.
Ensure still frames remain coherent when reduced motion is enabled. Remove
interpolation, repeated decorative movement and blur while retaining meaningful
completed states, navigation and access to results. Do not indiscriminately reset
all CSS filters if other filters carry intentional visual treatment.

## Quiet, usable controls

Support pause/play, previous/next, discoverable chapters, fullscreen and notes as
needed by the approved brief. Keep lower-priority controls in a compact menu.
Use accessible names for icon buttons and a visible focus state. Keep touch
targets at least 44 CSS pixels. Avoid keyboard shortcuts firing while someone is
typing in an input, select, textarea or editable region.

A timeline should make its scope clear: current demonstration or whole talk.
With manual section navigation, current-scene scrubbing is the safer default.
Restore focus when closing menus/dialogs. Do not require dragging to access a
necessary action.

## Browser acceptance checks

Select checks according to what was promised. Use actual browser interaction;
automated controller tests supplement it. Verify meaningful behaviour rather than
only checking labels or taking a still screenshot.

- Play each looping section through at least two complete loops. Confirm its
  visual action reaches the intended result and resets coherently. For one-shot
  sections, check completion and replay instead.
- In manual mode, confirm section ID, speaker and URL stay unchanged across loops
  and at the end of the scrubber. Check explicit navigation and first/last bounds.
- Confirm pause, seek, replay, speed changes and hidden-tab return follow the brief.
- Inspect source → operation → result causality and cross-component agreement.
- Confirm camera paths, not just settled endpoints, obey reveal restrictions.
- Inspect the final reveal using the same objects seen in the detail sections.
- Check keyboard-only use, accessible controls and notes/dialog focus.
- Inspect desktop and a narrow phone viewport: no unintended horizontal overflow,
  clipped names, illegible labels, unreachable menu entries or tiny hit targets.
- Resize while paused. Check portrait/landscape or projector aspect ratios when
  they are part of the delivery requirements.
- Enable reduced motion and verify sharp, meaningful content remains accessible.
- Test the actual promised offline method with network unavailable. Avoid relying
  on cached CDNs, remote fonts or modules that fail under file://.
- Check that the delivered build loads without asset, console or network errors.

Use a bounded review: one batched inspection of the relevant devices/states,
one batch of fixes and a confirmation pass. Broaden testing only for a new defect
or a changed requirement. If verification is blocked, state the specific gap.

## Packaging and release

For a static presentation, package only the HTML/CSS/JS and media required by the
viewer. Keep notes intentionally included and consider whether they contain
private information. Include media provenance/licences where applicable.

Test the offline package independently of the working directory. A local server
is acceptable when documented and agreed; do not promise double-click offline
support until it works. Video and native slide exports require separate checks
and may preserve fewer interactive features.

When hosting is authorized, verify the intended account/project, deploy only the
presentation assets and open the actual public result. A successful local build
does not establish a successful public deployment. Protect existing work and avoid
altering an unrelated app, backend, authentication system or Git history.
