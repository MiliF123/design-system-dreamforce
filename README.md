# Neocol · Dreamforce 2026 design system

Campaign token layer and reference builds for the DF26 social/event assets.
The token layer extends the site's existing `--nc-` variables — never create
parallel tokens, never hardcode a hex value.

## Layout

```
assets/
  df26-tokens.css       Campaign token layer (colour, type, spacing, components)
  df26-spotlight.html   Session spotlight · 1080×1080 reference build
uploads/                Image assets referenced by the builds (see below)
```

`assets/df26-spotlight.html` links `./df26-tokens.css` and pulls images from
`../uploads/`, so the two folders must stay siblings.

## Missing image assets

`uploads/` is empty in this repo. The spotlight build expects:

- `neocol_logo_color_horiz (1).png` — Neocol logo (rendered white-knockout)
- `df-logo-desktop.svg` — Dreamforce mark (sits in a white pill)
- `Dave-Walsh-web.jpg` — speaker headshot
- `pasted-1788182650771-0.png` — speaker headshot (Darryl Lutchmipersad)

Drop them in with those exact filenames and the build renders complete.

## Token layer at a glance

| Group | Tokens |
|---|---|
| Colour (from site) | `--nc-navy` `--nc-tealmid` `--nc-teal` `--nc-tealb` `--nc-tint` `--nc-white` `--nc-graybg` `--nc-border` `--nc-gray` `--nc-logomute` |
| Colour (campaign) | `--nc-coral` — the one warm accent |
| Type | `--nc-fh` (Prompt) · `--nc-fb` (Open Sans) + size/leading/tracking scale |
| Spacing | `--nc-s1`…`--nc-s5` on an 8px scale, `--nc-pad-asset` |

### Coral rules — non-negotiable

Coral does three jobs: the date/time badge (which becomes the "live now" badge
during the event), the subhead rule, and the CTA. Nothing else.

- OK — coral fill + navy text (6.02)
- OK — coral rule/marker on navy (6.02)
- NEVER — coral text on white or tint (2.43, fails AA)
- NEVER — coral fill touching `--nc-tealb` fill (1.83)

Full measured WCAG AA contrast table lives at the top of `df26-tokens.css`.

## Asset shells

| Class | Ground | Use |
|---|---|---|
| `.nc-asset--spotlight` | navy | session spotlights |
| `.nc-asset--eventwide` | tint | event-wide posts |
| `.nc-asset--live` | navy + `.nc-scrim` | live-from-event photography |

Default shell is 1080×1080. Add `.nc-asset--45` for the canonical LinkedIn
1200×1500.

## Production

- **File naming:** `df26_[template]_[session-slug]_[version].[ext]` — lowercase,
  no spaces. e.g. `df26_spotlight_slack-approvals_v2.png`
- **UTM:** every RSVP/session link carries a per-channel UTM (company page ·
  speaker profiles · Slack)
- Never place hashtags or links inside the image — they go in the post copy.
