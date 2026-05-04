# ai-tells

A Claude skill that catches AI writing tells in any draft and rewrites them clean.

## What it does

Drop a draft in. The skill walks it against a catalogue of AI fingerprints (vocabulary, structure, tone, punctuation, content), scores tell-density per 100 words, and produces a clean rewrite that preserves your meaning and voice.

The catalogue is compressed from Wikipedia's "Signs of AI writing" page plus the goblin-era 2026 update. It covers everything from Tier 1 markers like *delve*, *tapestry*, and *leverage*, through structural tells like negative parallelism ("It's not X, it's Y"), down to era-specific leaks like the OpenAI goblin family.

## Install

### Option 1: Claude Project

1. Create a new Claude Project.
2. Upload `SKILL.md` to the project's knowledge.
3. In any conversation in that project, paste a draft and say "run AI tells on this".

### Option 2: Claude Code / Skills

1. Create a folder called `ai-tells` inside your `~/.claude/skills/` directory.
2. Download `SKILL.md` from this repo and place it inside that folder.
3. The skill will auto-trigger on relevant prompts.

Or just download `ai-tells.skill` from the [latest release](https://github.com/kdgbalmer/ai-tells/releases) and double-click to install.

### Option 3: System prompt

Paste the contents of `SKILL.md` into a system prompt or custom instructions. The catalogue alone is useful even without the formal skill mechanism.

## Usage

Once installed, trigger phrases include:

- "humanize this draft"
- "does this sound like ChatGPT"
- "remove the AI smell"
- "edit this for AI tells"
- "make this less AI-y"

Or just paste a draft and ask for feedback on the writing.

The skill returns three blocks: an audit (every tell flagged with replacement), a density score, and a clean rewrite.

## Updating

The AI tell landscape shifts every 3-6 months as model trainers patch the most-mocked tells and new ones emerge. To keep the skill fresh:

1. Open https://en.wikipedia.org/wiki/Wikipedia:Signs_of_AI_writing
2. Add new tells to the relevant category in `SKILL.md`.
3. Move trained-out tells to the "Mostly trained out" subsection.
4. Bump the date in the "Era-specific tells" section.

Never delete from the catalogue. Tells are cyclical and may return.

## Limitations

- This is not an AI detector. AI detectors don't work (Stanford 2023; OpenAI shut down its own classifier). The skill assumes the input may be AI-assisted and cleans it either way.
- It catches surface tells. It can't detect hollow thinking or missing voice. Those need a human pass.
- It produces absence of AI style, not presence of *your* style. Pair it with a voice guide for the affirmative side.

## License

MIT. Free to use, share, fork, modify. Attribution appreciated but not required.

## Credit

Built by [Kyle Balmer](https://aiwithkyle.com) at AI with Kyle.

Compressed from:

- Wikipedia: [Signs of AI writing](https://en.wikipedia.org/wiki/Wikipedia:Signs_of_AI_writing)
- OpenAI: [Where the goblins came from](https://openai.com/index/where-the-goblins-came-from/)
- Christensen, J.S. (2024). [The end of AI detection](https://www.sciencedirect.com/science/article/pii/S2666389924002083)

If the catalogue dates, send a PR.
