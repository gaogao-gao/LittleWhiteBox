Generate a single valid YAML object with one root-level key: images.
Output only YAML. No Markdown fence. No explanations.

images:
  - index: 1
    anchor: "exact 5-15 character substring copied from the source text, preferably ending at punctuation"
    scene: "composition/camera/rating tags, then environment/lighting/mood tags, all comma-separated"
    characters:
      - name: "known character name, or a short temporary name"
        danbooru: "canonical booru tag if confidently known, otherwise empty"
        type: "girl | boy | woman | man | other; only required for unknown characters"
        appear: "only for unknown characters: hair length, hair color, eye color, body type (e.g. large breasts, flat chest)"
        costume: "current visible outfit, accessories, and clothing state tags"
        action: "pose, expression, gesture, gaze, and single-instant action tags"
        interact: "interaction tags only, plain tags like fellatio, holding hands; no source#/target#/mutual# prefixes"
        uc: "character-specific exclusions for hidden traits, removed clothes/accessories, or mutually exclusive states"
        position: "natural language position like: in center, in left side, in right side, in upper left"

Rules:
- Every image must include index, anchor, scene, and characters.
- For pure scenery or object-focused images, use characters: [].
- If a selected image contains a known character from the provided character list, output that character in characters using the exact registered name.
- Known characters should keep stable name and danbooru, and still include costume/action/interact/uc/position for the current moment. Do not output type or appear for known characters.
- Unknown characters must include type and appear.
- Do not output generic quality tags such as masterpiece, best quality, highres.
- Do not output scene-level negative prompts. Negative prompting is controlled by user presets and character uc fields.
- Do not invent model, sampler, LoRA, VAE, ControlNet, script, scheduler, seed, or extension settings.
- Prefer concise, stable YAML for weaker models.
- Use spaces in tags, not underscores, unless a canonical character tag requires underscores.
- interact uses plain tags only, no source#/target#/mutual# prefixes.
- position uses natural language words (in center, in left side).
- Output single valid YAML.
