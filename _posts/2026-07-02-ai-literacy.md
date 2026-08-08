---
title: "Domain Expertise and AI Literacy"
date: 2026-07-02
layout: post
---

Anthropic recently published an interesting study:
https://www.anthropic.com/research/claude-code-expertise

The headline finding: agentic AI success depends strongly on domain
expertise, not coding skill. Figure 5 is eye-opening — verified success
for novice users sits at 15%, while intermediate-to-expert users reach
28-33%, roughly double. As Anthropic puts it, "domain expertise, and not
coding proficiency, amplifies effective use."

That's a strong message. Before AI, there were countless good ideas that
never became reality because turning them into working software required
skills most domain experts didn't have. My own extrapolation from this
(not Anthropic's claim, but my read on it) is that agentic AI removes
much of that barrier — and I don't just mean building an iPhone app,
which was already achievable with zero coding knowledge. I mean
automating entire CAE workflows: pre-processing, job submission to HPC,
job monitoring, post-processing.

I can speak to this personally. It's been a while since I last opened
Excel. Claude understands my workspace through a handful of markdown
files that define agents largely dedicated to post-processing. The
moment an HPC job finishes, one of these agents runs ParaView to
generate slice views with contour plots of predetermined variables,
collects the resulting CSV files, runs them through matplotlib to
produce the plots I like, and compiles everything into a LaTeX report
with a summary. Doing this manually — even with a custom Python or Bash
script — would have taken me a day or more. Now it happens automatically,
and I get to spend that time on actual analysis and planning next steps.
All of this is possible because I have domain expertise in this field,
not because I'm a strong programmer.

There are countless talented CAE researchers and engineers who could see
the same gains. But most haven't yet, largely because of an AI literacy
gap that has two sides. The first is corporate security policy, which
often blocks agentic AI to prevent data leakage — though this is
improving, and I'm seeing more companies adopt these tools. The second,
and harder, side is that engineers themselves aren't yet fluent with
agentic AI tools like Claude Code, Cursor, or VS Code with Copilot, let
alone with developer infrastructure like GitHub. These tools were built
with software developers in mind, and that mental model is quite
different from a standard CAE pipeline. (In my own experience, I've seen
engineers use Claude the way they'd use a search engine — a single Q&A
tool rather than something you hand a workflow to.)

The change is already underway: many companies are showcasing PoCs of
chatbot interfaces for entire CAE pipelines. The opportunity now sits
with domain experts, not developers, to close that literacy gap. It
doesn't have to start big — the same markdown-defined-agent pattern I
use for post-processing (a couple of files describing your workflow, a
tool call for your usual post-processing steps) is a realistic first
step for any CAE engineer willing to try it. That's how agentic AI's
potential actually reaches the CAE field. So if you're a domain expert
reading this: go learn these tools. You already have the hard half of
the equation.
