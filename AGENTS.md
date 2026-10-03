This repository is the charter of «Горница» (Gornitsa), a small studio of mobile games for
RuStore. It holds everything that is the same for every project of the studio: mission, values
and promises to players, team roles, the way work is done, hard rules for all games, content
and privacy rules, publishing, voice, the brand book and studio-level decisions (ADR).
Documents are in Russian; this file is in English, like the `AGENTS.md` of the projects.

## You are probably working in a project repository

Every project of the studio (`Nefeste/votchina`, `Nefeste/nardy`, `Nefeste/anamnez`,
`Nefeste/skazy`, `Nefeste/uzory`, the site `Nefeste/gornitsagames`, the gateway `Nefeste/seni`)
links here from its own `AGENTS.md`. The projects, the gateway and the studio's internal
repository `Nefeste/uprava` are private; the charter, the site and the shared kit
`Nefeste/gornitsa-kit` are public (studio ADR 0017). Agents reach the private ones through
the «Claude» GitHub App. Read this charter **before changing anything in any project**, and
again after a context reset. The repository is public; fetch files with

```
https://raw.githubusercontent.com/Nefeste/gornitsa/main/<path>
```

or clone `https://github.com/Nefeste/gornitsa.git` next to the project.

The current state of the charter is in `STATUS.md`.

Read in this order (about 30 minutes):

1. `README.md` — what lives here, precedence of rules, "one place for a fact".
2. `docs/05-rules.md` — **hard rules for every game**, one line each with the decision behind it.
3. `docs/04-process.md` — how work is done: docs in the repo, spec before code, ADR, versions,
   fast CI on PRs and APK only on a tag (ADR 0019), who merges what (ADR 0018), how code
   gets uploaded, what to do after a context reset.
4. `docs/02-values.md` — what we promise players; every feature is checked against it.
5. `docs/03-team.md` — roles, mailboxes, what an agent may do alone and what only the owner decides.
6. The rest when the task touches it: `docs/06-content.md` before adding any text, picture or
   sound from outside; `docs/07-privacy.md` before touching anything that leaves the phone;
   `docs/08-publishing.md` before a release or store listing; `docs/09-voice.md` before
   writing text for players; `docs/10-channels.md` before drafting a post, a reply to a
   review or a letter; `brand/README.md` before any visual work; `adr/` before
   proposing the opposite of a studio decision.

## Precedence

1. The owner's recorded decision. 2. This charter. 3. The project's documents.

A project may narrow a studio rule, never weaken it. A deviation needs the owner's decision
recorded as an ADR in the project that names the charter rule it departs from. If a project
document contradicts the charter without such an ADR, the charter wins — fix the project
document in the same change, or tell the owner if you are not sure which is right.

## One place for a fact

- A studio-wide rule is written **only here**. In a project, link to it; do not restate it.
- When you find a project document that restates a charter rule, replace the restatement
  with a link in the same change. When you find a contradiction, do not pick silently —
  write it in your report to the owner.
- Project documents keep only what belongs to the project: its rules, numbers, screens,
  exceptions, and *how* a studio rule is implemented there.
- Changing the charter: a PR here (only the owner merges), then PRs in the projects that
  still carry the old wording. Studio decisions that are expensive to reverse are ADRs in `adr/`.

## Expo has changed — do not trust your training data

All games are Expo / React Native / TypeScript apps (studio ADR 0003). Expo ships breaking
changes every SDK release; APIs you remember are likely renamed, moved or removed. Before
writing any code that touches Expo, EAS, React Native or a native SDK:

1. Read the major version of `expo` in the project's `package.json`.
2. Fetch the matching versioned docs: `https://docs.expo.dev/versions/v<major>.0.0/`.
3. For anything else, fetch https://docs.expo.dev/llms.txt and follow its links; never answer
   from memory.

The same applies to `@shopify/react-native-skia`, Reanimated, Expo Router, RuStore Pay,
RuStore Review and any ads SDK: read their current docs before use. If `docs.expo.dev` is
unreachable from your environment, the working configuration of `Nefeste/votchina` on the
same SDK is the reference.

## Things an agent never does alone

Details are in `docs/03-team.md`. In short, an agent never presses «Merge» itself: documents
and code that touch no money, network, player data or deployment merge automatically after
green CI and a `ревью: ок` label from a reviewer in another session; owner paths in
`CODEOWNERS` and the charter are merged by the owner (studio ADR 0018). Without the
owner's explicit go-ahead for this particular action an agent never publishes to a store,
sends an email or a public post on behalf of the studio, spends money or changes account
settings. Never, even
with a go-ahead: enter or store passwords, keys or payment details, or mark content as checked
(`review: checked`) — these are the owner's. Prepare everything up to that point and ask.
