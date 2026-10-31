# Strategy Advisor

A skill that diagnoses a business problem, picks the strategic framework that fits its environment,
and answers in a fixed four-part structure. It works as a Claude Code plugin, a plain Agent Skills
folder, and a prompt you can paste into any chat assistant.

Ask it a strategy question and it answers in four parts, with no preamble:

```
Diagnosis: [the core problem and the environment it sits in]
Framework Selected: [name]. [why it fits]
Strategic Action / Perspectives: [bullets; both sides if frameworks disagree]
Refining Question: [at most two, only if needed]
```

It picks the approach from Martin Reeves's *Strategy Palette* (classical, adaptive, visionary,
shaping, renewal) by asking whether the future can be predicted, whether you can shape the
environment, and whether survival is at stake. When two frameworks give opposing advice it presents
both, asks one or two questions and waits instead of guessing. It declines to write execution plans.

Use it as a skill (the plugin or the [skills/strategy-advisor/](skills/strategy-advisor/) folder), or paste
`strategy-advisor-prompt.txt` (attached to each GitHub Release, built by `tools/build.py`) into the
custom instructions of any chat assistant.

It is framework reasoning over what you tell it. It has no current market data and says so.

---

## Install

**Claude Code plugin**

```
/plugin marketplace add coeurdelion-me/strategy-advisor
/plugin install strategy-advisor@strategy-advisor
```

**As a plain skill**: copy `skills/strategy-advisor/` into your assistant's skills folder (for
Claude Code, `~/.claude/skills/`), or upload `strategy-advisor.zip` from the latest GitHub Release
where your assistant accepts skill uploads.

**As a prompt**: paste `strategy-advisor-prompt.txt` from the latest Release into the custom
instructions of any chat assistant.

## Tests

`skills/strategy-advisor/evals/` holds four test prompts with assertions: a conflict that should
make it ask before recommending, a fast-moving build-or-buy, a survival-mode turnaround, and an
execution-planning request it should decline. Run them with `claude plugin eval .` where available,
or run each prompt with and without the skill and grade the answers against the assertions.

```bash
python3 tools/build.py        # validates the skill, writes dist/
```

## Also by the same author

[Advisory Council](https://github.com/coeurdelion-me/advisory-council): a panel of different AI
models that reviews a proposal in two rounds, like a procurement process.

## Licence

Made by Coeur de Lion. Licensed under [CC BY-NC 4.0](https://creativecommons.org/licenses/by-nc/4.0/):
you can use, share and adapt it for any non-commercial purpose, crediting Coeur de Lion and saying
what you changed. The full terms are in [LICENSE](LICENSE).
