---
name: cinematic-presentations
description: Create or revise cinematic presentation websites with spatial storytelling, connected scenes, and purposeful explanatory animations. Gather the content and presentation requirements, ask the user to design the narrative flow, and implement the agreed story. Use for animated project presentations, pitches, lessons, research talks, portfolios, or visual explainers; native PowerPoint export is a separate deliverable.
---

# Cinematic Presentations

Build a presentation website that makes the audience see the idea working. Use
minimal screen text, meaningful visual transformations, and continuity between
sections. Match the spatial structure to the content; an architecture diagram is
only one possible structure.

## 1. Understand the content and the occasion

Read supplied material and relevant conversation before asking questions. For an
existing presentation, inspect its actual source and current behaviour. Surface
conflicts between old notes and newer steering; preserve the latest user choices.

Collect the relevant information in short batches, normally two or three
questions at a time. Prefill what is known and ask only what remains material:

- **Purpose:** topic, audience, prior knowledge, occasion, desired takeaway or
  action, presentation length, and Q&A arrangements.
- **Content:** source documents, data, examples, required points, exclusions,
  factual limitations, available screenshots/media, and permission to use them.
  Mark missing information instead of inventing evidence.
- **People:** single/group presentation, speaker names and order, section
  ownership, handoffs, and whether someone can operate the presentation.
- **Creative direction:** references, brand/logo, palette, typography, text
  density, desired intensity of motion, and essential visual moments.
- **Delivery:** presenting device/screen/aspect ratio, mobile viewing, browser,
  offline requirements, notes, controls, language, hosting/export needs, and any
  requirement for audio, video, captions or audience interaction.

Do not demand irrelevant fields or repeat an intake already answered. Ask for
files through normal chat when needed; text-only question tools cannot receive
uploads. Browse primary sources when research or factual verification is needed.

## 2. Ask the user to design the flow

For a new story, explicitly ask this before implementation:

> How do you want the presentation to unfold? Give me the sections in order,
> what each should make the audience understand, and who speaks if it is a group.
> Rough bullets are enough. Tell me how you want to open and end, and any reveal
> you want saved for later.

Invite an explanation in the user's own words. Offer to co-design if they are
unsure. If they request recommendations, provide a small editable outline and
ask them to choose or amend it. Do not silently substitute a generic agenda or
build the presentation while a required flow answer is pending.

Clarify the few decisions that change the experience:

- Is the introduction separate from the main visual world?
- What connects the sections: one example, place, timeline, argument, object,
  comparison, or system? Which sections can be combined without losing meaning?
- When may the audience see the complete picture? Is there a final reveal?
- Do animations loop while the presenter speaks, or should sections advance
  automatically? In automatic mode, how are timing and speaker handoffs set?

Turn the answers into a compact, concrete storyboard:

| Section / speaker | Audience takeaway | Visual action and evidence | Connection / reveal |
| --- | --- | --- | --- |

Include the proposed visual direction and playback model with that storyboard.
Ask the user to confirm or edit the plan before substantial visual implementation.
This is creative agreement, not permission to deploy. If the user already
provided an approved flow or explicitly delegated both flow and implementation,
record that and proceed without asking for the same approval again.

## 3. Design the visual explanation

Read [visual-storytelling.md](references/visual-storytelling.md) when translating
the agreed flow into scenes. Choose a structure that fits the subject. A timeline,
map, evolving illustration, evidence board, chart, or sequence of connected
environments can provide continuity just as well as a system diagram.

For every retained visual component, specify:

1. What the audience is looking at and why it matters.
2. What happens or changes, with a meaningful before/after or comparison.
3. What visible result demonstrates the takeaway.
4. How it connects to the neighbouring section.

A moving border, floating card, particle field or generic fade does not satisfy
this demonstration requirement. Motion can explain relationships, comparisons
and uncertainty; it need not imply a physical process. Keep static material static
when movement adds no understanding.

Let demonstrations occupy the main viewing area. Use a short, informative heading
and necessary labels; move explanations and speaking detail to notes. Preserve
useful source imagery, charts and diagrams. Keep their scales, labels and claims
honest. Introduce examples as illustrative when they are simulations.

If the user wants the original reference style, use restrained monochrome,
generous spacing, large sans-serif headings, SF Pro where available with a suitable
system fallback, simple SVG marks/icons, spring-like movement and transient blur.
Do not copy the original project logo, speaker names, subject matter or policies.
Other approved brands, fonts and colours take precedence. Respect font licensing.

## 4. Build the presentation

Read [playback-and-verification.md](references/playback-and-verification.md)
before implementing the controller, motion and delivery behaviour.

- Keep story/content, scene renderers, playback state and styling separable.
  Store scene IDs, order, speakers, notes, focus regions and motion settings as
  editable data. Do not build an authoring platform unless requested.
- Reuse persistent objects and source examples across sections so transitions
  communicate continuity. Build a shared world when the story benefits from it;
  do not force unrelated content into boxes on one huge diagram.
- Use one scene clock to coordinate demonstrations. Keep navigation separate
  from animation progress. Default to manual section advancement with looping
  demonstrations unless the agreed brief specifies otherwise.
- Give movement clear starts and sharp rests. Use intentional easing and bounded
  blur during camera/morph transitions when appropriate to the approved style.
  Honour reduced motion and keep text readable.
- Keep presenter chrome quiet. For a group presentation in the reference style,
  show only the active speaker in the top bar; place notes, speed, chapters and
  fullscreen controls elsewhere. Adapt this convention to the approved brief.
- Make source content editable and controls usable with keyboard and touch.
  Support responsive composition, readable text and at least 44 CSS-pixel touch
  targets. Test paused resizing as well as animation in progress.
- Prefer self-contained web assets for reliable presenting. Confirm whether
  offline delivery means opening a file directly or running a local server.
  Document the actual launch method and test the promised mode.

Use available design/media/document skills when they materially help, following
the user's tool and delegation preferences. The workflow must still work without
a particular design skill or paid service. Generate SVG/HTML/canvas illustrations
directly when they are the appropriate medium.

## 5. Verify and deliver

Verify the actual presentation in a browser, not only its code or screenshots.
Use the behavioural checks in the playback reference and a bounded desktop/mobile
review: inspect once, fix the defects together, then confirm. Focus on functional
demonstrations, narrative continuity, readability and delivery reliability.

Deliver the runnable website, concise launch instructions, editable notes and any
requested offline package. Report what was verified and any genuine limitation.
Include a representative screenshot when possible. Publish, push or change a live
deployment only within the user's authorization. Keep private inputs, credentials
and unrelated application code out of the presentation package.
