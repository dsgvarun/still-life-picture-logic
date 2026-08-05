# Still Life: Picture Logic — public pages

The privacy policy and support page for the iOS app, served by GitHub Pages.

**This repository is public and deliberately contains nothing but pages and packs.** The game's source
lives in a private repository; publishing a privacy policy is not a reason to expose a content pipeline
and its entire git history.

`packs/` serves the remote content manifest and the packs it points at (T-4). Same host as the pages,
because the marginal cost of one more static file on a host that already exists is nothing — which was
the argument for un-cutting remote delivery in the first place.

| page | URL |
|---|---|
| Privacy policy | `/privacy.html` — the Privacy Policy URL in App Store Connect |
| Support | `/support.html` — the Support URL in App Store Connect |
| Pack manifest | `/packs/manifest.json` — the value of `EXPO_PUBLIC_PACK_MANIFEST_URL` |
| Packs | `/packs/starter-<revision>.json` — never overwritten; a new revision is a new file |

Plain HTML and one stylesheet, no build step and no Jekyll. A privacy policy has to load for anyone on
anything, including an App Review reviewer on a bad connection.

## Editing

Both pages must stay **true**. The privacy policy describes what the app actually does, and the app is
the source of truth:

- what is collected, and the consent gate: `src/analytics.ts`, `src/game/consent.ts`
- the wording the player agrees to: `src/screens/ConsentScreen.tsx`
- what Apple is told: `ios.privacyManifests` in `app.config.ts`

If any of those change, this changes in the same breath. A policy that describes an older version of the
app is worse than no policy.
