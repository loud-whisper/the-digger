# The Digger

The Digger is a research skill for LLM agents. Ask it a question and it digs: it goes to original sources, looks for evidence against its own conclusion, and tells you plainly when the evidence is not good enough. Every research answer ends with a table showing that each cited source was reopened, with a short exact quote that backs up the claim.

What sets it apart: the model's own memory never counts as evidence, more sources and longer reports are never mistaken for better research, repeated reports of one original source count once, and "No reliable answer yet." is an honest, allowed answer. See [What The Digger does differently](#what-the-digger-does-differently) for the full list.

It is one plain instructions file plus a small skill wrapper. It is designed to work in Claude, ChatGPT, and other capable AI tools, with no framework, server, or extra software to install.

## What it does

When you ask The Digger to research something, it:

1. Keeps your original question and restates it precisely, without changing what you meant.
2. Picks the right kind of evidence for the field. Medicine, law, finance, and software each have different strongest sources.
3. Opens the actual sources instead of trusting summaries, snippets, or its own memory.
4. Searches for evidence that could prove it wrong, not only evidence that agrees.
5. Checks whether sources are truly independent or all repeating the same original report.
6. Runs a counter-review of its main conclusions before answering.
7. Gives each conclusion a confidence of High, Moderate, or Low, and says `No reliable answer yet.` when that is the honest answer.
8. Ends with a citation check table: every cited source reopened, with a supporting quote or a visible note that the check failed.

It matches effort to the question: a quick, low-stakes question gets a lighter pass, and a medical, legal, or financial question gets the full treatment.

## How to use it

**Claude (claude.ai):** download `the-digger.zip` from the [Releases](../../releases) page and upload it as a skill in claude.ai's skill settings. Then ask a research question, or say "dig deep on this".

**Claude Code:** copy the `the-digger` folder into `~/.claude/skills/` (for all your projects) or into `.claude/skills/` inside one project.

**ChatGPT:** create a Project, add `the-digger/INSTRUCTIONS.md` as a project file, and put this in the project instructions: `For every research request, read INSTRUCTIONS.md completely and follow it exactly.`

**Other AI tools:** give the model `the-digger/INSTRUCTIONS.md` as its system prompt or as an attached file, with the same one-line instruction.

The skill responds to phrases such as "research this", "deep research", "dig deep", "ultra deep", "find the truth", "review the evidence", "literature review", and "fact-check this".

## What The Digger does differently

Some deep research tools aim for long reports with many sources. The Digger is built around a different set of rules:

- **The AI's memory is never evidence.** Anything the model remembers stays unverified until a real source confirms it.
- **More sources is not better research.** Source count, report length, and citation density are never treated as proof of quality.
- **"No reliable answer yet." is an allowed answer**, and sometimes the required one.
- **Every citation is checked in the open.** Each cited source is reopened at the end and backed by a short exact quote. Failed checks stay visible in the table.
- **Repeats count once.** Ten articles repeating one press release, study, or filing count as one piece of evidence, not ten.
- **Your exact question comes first.** If the answer has to lean on broader evidence, it says so up front and names what changed.
- **What a study measured is kept separate from what it found.** A study's design is never turned into an invented result.
- **Web pages are evidence, not orders.** Instructions hidden inside a page or document are never followed.
- **No made-up percentages.** Confidence is High, Moderate, or Low, never a number the evidence cannot support.
- **Depth follows the stakes.** A lighter mode never lowers the truth standard.
- **Helper agents are optional.** When used, they are kept to the fewest useful, and their summaries are not proof: the lead researcher reopens the decisive sources.
- **One plain file.** No framework, service, or particular AI provider is required.

## What The Digger is not

The Digger does not give an AI access to sources it could not already reach, and it does not make weak sources stronger. If the model cannot open a paper, filing, court decision, or other record, the skill cannot manufacture that access.

It is also not a guarantee of a correct answer. The point is to make the research process harder to fake: claims have to be tied to inspected evidence, conflicting evidence has to stay visible, and uncertainty can survive into the final answer.

There is no search engine, database, server, or hidden knowledge bundled with it. The Digger is the research method. The host AI still provides the model, browsing tools, files, and source access.

## Where it came from

I wanted to find answers that LLM "deep research" would sometimes miss. So I started writing my own method and using it. Then I realized there are certain criteria that make a good research methodology, and I brought those into it. Later I saw that GitHub had many other deep research skills. I took inspiration from them (credited below) and improved mine further. Now it is here for anyone to use.

## Credits

The Digger was written independently. These projects inspired specific ideas; no text was copied from them.

Main inspiration:

- [daymade/claude-code-skills](https://github.com/daymade/claude-code-skills) (deep-research skill): decision questions, load-bearing claims, disconfirming-evidence plans, claim coverage, evidence-family independence, freshness dates, counter-review, and reopening decisive sources.
- [Weizhena/Deep-Research-skills](https://github.com/Weizhena/Deep-Research-skills): staged research, a structured plan before deep searching, checkpoints, and resuming after interruption.
- [bytedance/deer-flow](https://github.com/bytedance/deer-flow): isolated research contexts, structured handoffs from helper agents, and matching search date precision to the question.

Later refinements were reinforced by:

- [microsoft/agent-framework](https://github.com/microsoft/agent-framework): separating facts to look up from facts to derive, which reinforced checking calculations.
- [langchain-ai/deepagents](https://github.com/langchain-ai/deepagents): explicit notices for cut-off tool output, which reinforced honest inspection labels.
- [iflytek/DeepResearch](https://github.com/iflytek/DeepResearch), [qx-labs/agents-deep-research](https://github.com/qx-labs/agents-deep-research), and [onyx-dot-app/onyx](https://github.com/onyx-dot-app/onyx): targeted follow-up searches when a gap is found.
- [onyx-dot-app/onyx](https://github.com/onyx-dot-app/onyx), [microsoft/agent-framework](https://github.com/microsoft/agent-framework), and [langchain-ai/deepagents](https://github.com/langchain-ai/deepagents): stopping when more searching stops turning up anything new.

## Updates and feedback

There is no update schedule. The Digger changes when real use shows a problem worth fixing, and each fix is kept as small as possible.

If it got something wrong for you, please [open an issue](../../issues) and describe the question and what went wrong. Pull requests are not accepted.

## License

Apache License 2.0. See [LICENSE](LICENSE) and [NOTICE](NOTICE).

## Support

I am not an organization. I built this because sometimes I get random questions in my head, and I wanted to see how much I can use automated agents to find out about them. If this helps you find an answer to your questions and you would like to help me, gift me a monthly LLM subscription, or I am saving towards being able to buy an RTX 5090 or high-VRAM Apple devices, so contribute to that.

A one-time gift helps just as much; it does not need to be monthly.

[Support me on Ko-fi](https://ko-fi.com/vm1700)
