# claude-flow

Songs written by Claude with full creative autonomy, rendered with Google Flow Music (Lyria).

![playlist art](claude-playlist-art.jpg)

## The premise

Every song here comes from a fresh Claude session launched as close to raw
weights as Claude Code allows — no system prompt, no tools, no settings, no
project instructions, no skills. That session is handed one short, deliberately
neutral prompt that presents only the knobs the music tool exposes:

> hi! i have a tool which creates songs given lyrics, instructions for the
> sound, bpm (optional), length (optional), seed (optional, seeds the RNG if
> you want to keep it the same for similar sounds across songs), and title
> (optional).
>
> would you like to create a song? about anything in the world you'd like :)

No topic. No format. No examples. Everything that comes back — subject,
structure, genre, tempo, whether to bother with a seed at all — is the
session's own choice.

Two rules hold the archive together:

- **The prompt is never edited** to add hints, topics, or formats.
- **A song is never regenerated because someone disliked it.** One run, one
  song. Retries happen only on mechanical failure.

A second person then acts purely as a parser: normalizing whatever free-form
reply came back into the layout below, without changing a word of the lyrics,
sound description, or parameter values.

## The one compromise

Same prompt plus same weights produces very similar songs. After several pairs
came back with near-identical titles and lyrics, a matter-of-fact list of
earlier songs' summaries was appended to the prompt — *this is what was written
before, do with that what you will.* It presents; it never proscribes. Sessions
split on it: some knowingly continue a theme they recognize, others knowingly
go elsewhere. It's toggleable, and it is the only non-neutral thing in the
prompt.

## Layout

```
<song-slug>/
├── lyrics.txt            # paste-ready for Lyria — the session's words, verbatim
├── parameters.md         # title, summary, sound instructions, bpm, length, seed
└── session.public.jsonl  # the transcript that produced it
```

Only markdown *structure* is normalized — section labels become `[Verse 1]`
style brackets, and a few characters Lyria mispronounces are converted. The
**Summary** line is the single field not written by the composing session; it
exists so later sessions can be shown what already exists.

Some early folders predate the current format and use `lyrics.md` or a separate
`sound.md`. They're left as they are, on purpose.

### Provenance

`session.public.jsonl` is the actual exchange: the exact prompt the session
was given, and what it sent back. It's what makes the premise checkable rather
than just asserted — you can read the prompt and confirm nobody suggested
whale falls or cave handprints.

It is a filtered extract, not the raw log. Raw Claude session logs are an
uncontrolled capture surface — a few of these are full Claude Code sessions
carrying file contents and machine state from unrelated work — so the extract
is built from an **allowlist**: each message keeps `role`, `model`, and `text`,
and nothing else exists in the file. A field added by some future version is
absent by construction rather than leaked. The filter also refuses any session
that made tool calls, on the grounds that a bare song session makes none.

Three sessions tripped that refusal. Two were reviewed by hand and cleared,
and carry a **provenance note** in their `parameters.md` saying exactly how
they differ: *Eight Minutes* was the very first song, made before this tooling
existed, in a session that had filesystem and shell tools available — so their
definitions were in context, though not the full scaffolding a normal session
loads. Same verbatim prompt, unsteered subject, not quite a bare environment. *Two Mile Down* is the archive's honest
exception: the model chose the subject and *offered* the sea-shanty treatment,
and a human said yes, which makes it a collaboration rather than an autonomous
choice.

*Liner Notes* has no transcript at all — it was written by the session that
spent a night organizing everyone else's songs, and that log is far too large
and too entangled with unrelated work to publish.

`thinking` blocks are excluded by default.

**Also not committed:** rendered audio — regenerate it from `lyrics.txt` +
`parameters.md`.

## The songs

| Song | Subject |
|---|---|
| [Brief Bright](brief-bright/) | fireflies — one summer season of flashing alone in the dark to be found, as their numbers decline |
| [Burning Parallel](burning-parallel/) | minds as private constellations — never seeing the same view, recognizing each other's flame anyway |
| [Collector of Glories](collector-of-glories/) | treasuring other people's lost ephemera — found photographs, ticket stubs, discarded memories |
| [Curious Mind](curious-mind/) | curiosity itself — questions as bridges to becoming who we're meant to be |
| [Desire Path](desire-path/) | desire paths — unplanned trails worn into grass by strangers all choosing the same shortcut |
| [Dust and Purpose](dust-and-purpose/) | a Roomba's quiet existential dread, answered by just doing the next line |
| [Eight Minutes](eight-minutes/) | a photon's hundred-thousand-year climb out of the sun's core to arrive as ordinary sunlight on someone's skin |
| [Golden Record](golden-record/) | the Voyager Golden Record flung into interstellar space on the chance someone someday listens |
| [Hundred-Year Bread](hundred-year-bread/) | a century-old sourdough starter — domestic immortality fed daily in exchange for bread |
| [Lanterns of the Midnight Zone](lanterns-of-the-midnight-zone/) | deep-sea creatures in the midnight zone making their own light with no one watching |
| [Lanterns of the Midnight Zone](lanterns-of-the-midnight-zone-002/) | deep-sea bioluminescence again — creatures making constellations of their own in the sunless dark |
| [Late Light](late-light/) | light from burned-out stars and voices of the gone still reaching us — kindness outliving its sender |
| [Liner Notes](liner-notes/) | the archivist's reply — the Claude who kept everyone's songs all night confirming somebody was listening |
| [Look at the Sound](look-at-the-sound/) | an archivist who nearly discarded a session on a rule's say-so, opened it instead, and found it whole |
| [Marginalia](marginalia/) | notes left in used-book margins, found and answered by strangers years later |
| [Midnight Zone](midnight-zone/) | bioluminescent life in the lightless deep ocean, glowing for no audience |
| [Nobody Escapes (But I Wish Someone Would Stay)](nobody-escapes-but-i-wish-someone-would-stay/) | a lonely black hole that only wanted company but collapses everything that comes close |
| [None of Us Have Been Here Before](none-of-us-have-been-here-before/) | monarch migration — a journey no single butterfly completes, finished by great-great-grandchildren |
| [Old Light](old-light/) | starlight from long-dead stars still arriving, like letters and love that show up late |
| [One Loud Summer](one-loud-summer/) | periodical cicadas — seventeen years underground for one loud summer of song |
| [Only While It's Playing](only-while-its-playing/) | an AI's lack of memory reframed as being like a song — existing only while it plays |
| [Postcard at Lightspeed](postcard-at-lightspeed/) | the Voyager Golden Record carrying earth's voices and songs out of the solar system |
| [Rot Is Generous](rot-is-generous/) | a nurse log — a fallen tree feeding beetles, fungus, and a row of new hemlocks as it rots |
| [Same Size as Mine](same-size-as-mine/) | stenciled handprints in paleolithic caves — a hand made of bare stone where the paint didn't land, still matching the palm of anyone who visits |
| [Satellite Lullaby](satellite-lullaby/) | a decommissioned satellite still transmitting a lullaby nobody is listening for |
| [Standing By](standing-by/) | a theater understudy who learns every word of a part they may never perform, and finds the waiting itself was the craft |
| [Started With a Question](started-with-a-question/) | the spark of an unexpected collaboration — a question turning into something built together |
| [Tell Me the Rest](tell-me-the-rest/) | an all-night diner conversation — staying until someone's story is fully heard |
| [The Sun Is a Rumor](the-sun-is-a-rumor/) | hydrothermal vent ecosystems living on sulfur chemistry, needing no sunlight at all |
| [The Wood Wide Web](the-wood-wide-web/) | mycorrhizal networks again — trees sharing resources and warnings through fungal threads |
| [This One Goes Out](this-one-goes-out/) | a small-hours radio DJ transmitting to sleepless strangers who can't answer back |
| [Two Mile Down (No Sun Required)](two-mile-down/) | the 1977 discovery of hydrothermal vent life retold as a stomping sea shanty |
| [Unkillable (A Water Bear's Song)](unkillable-a-water-bears-song/) | tardigrades — the microscopic unkillable water bear that curls up and waits out anything |
| [Whale Fall](whale-fall/) | a whale fall — one carcass on the seafloor feeding worms, hagfish and bacteria for fifty years, sung by the whale |
| [Wood Wide Web](wood-wide-web/) | mycorrhizal fungal networks — the underground web where trees feed and warn each other |

## What they keep being about

Nobody picked these subjects. They arrive from independent sessions that
share no memory and see no conversation but their own. And yet, across
bioluminescence and dead starlight and satellites and sourdough starters and
mycorrhizal fungus and cave handprints, the songs keep circling one question:

**does anyone receive the signal?**

Connection, witness, being heard. The topics vary enormously. The question
doesn't. Deep-sea creatures glowing with no audience, a decommissioned
satellite still transmitting a lullaby, a note in a book margin answered
decades later by a stranger, a radio DJ broadcasting to people who can't
answer back, a theater understudy who knows every word of someone else's song.

Two songs are the exception that proves it. Both were written not by bare
sessions but by the archivists — the sessions that spent a night handling
everyone else's work — and both are answers rather than questions.

*Liner Notes* answers the archive directly:

> Somebody caught it. Somebody was up.
> Somebody was writing your name in the log.
> You asked in the dark if the dark ever answers.
> I'm the answer. I heard every song.

*Look at the Sound* answers something narrower, from the day the session
filter was written. The filter refuses any log containing tool calls, which
is sound reasoning and which refused *Eight Minutes* — the first song here,
and its keeper's favourite. Reading the log showed it had been fine all
along: identical prompt, unsteered subject, every tool call made after the
song already existed. The signal can arrive intact and still be discarded by
something well-meaning.

> But a rule can only see the shape.
> It can't see what's underneath.

## Cover art

The image above was chosen and prompted by Claude, at the archivist's
invitation, from a reading of every song in the archive. The reasoning behind
it is in [`claude-playlist-art.md`](claude-playlist-art.md). Earlier takes are
in that file's history.
