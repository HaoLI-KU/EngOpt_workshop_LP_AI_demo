# One linear programme, four AI-made web pages

[![Live site](https://img.shields.io/badge/live%20site-GitHub%20Pages-22577a)](https://haoli-ku.github.io/EngOpt_workshop_LP_AI_demo/)
[![Code: MIT](https://img.shields.io/badge/code-MIT-blue)](LICENSE)
[![Content: CC BY 4.0](https://img.shields.io/badge/content-CC%20BY%204.0-lightgrey)](LICENSE-CONTENT)

A teaching demonstration of how AI coding tools can turn a mathematical concept into an interactive web page,
and why the result must always be checked.

**▶ See the pages: <https://haoli-ku.github.io/EngOpt_workshop_LP_AI_demo/>**

## About

This repository accompanies **Lecture 9, "Git, GitHub and coding with AI"**, of the bachelor course
**Engineering Optimisation** at the Institute of Mechanical Engineering, **University of Southern Denmark (SDU)**.
It was made by the lecturer, Hao Li, in November 2026.

The lecture shows students how AI tools can help them illustrate concepts from the course. As the example we
use the **workshop linear programme from Lecture 2**. The same problem was given to AI agents with prompts of
increasing detail, and to both a free and a paid model. Students can compare the pages that came out and
see how the prompt and the model change the result.

## The problem

```text
max   50 x1 + 100 x2              profit, $ per week
s.t.  10 x1 +   5 x2 ≤ 2500       lathes,   minutes per week
       4 x1 +  10 x2 ≤ 2000       milling,  minutes per week
         x1 + 1.5 x2 ≤  450       grinding, minutes per week
       x1, x2 ≥ 0                 parts I and II made per week
```

Optimum: **(x1, x2) = (187.5, 125)**, with a profit of **$21,875** per week.

The example is Example 3.2 in S. S. Rao, *Engineering Optimization: Theory and Practice*, 5th ed., Wiley, 2020.
It is the workshop example used in Lecture 2.

## The versions

| Version | Model | What the prompt gave | Time | What came out | Links |
|---|---|---|---|---|---|
| Warm-up | Gemini 3.5 Flash-Lite (free, in OpenCode) | A tiny task: a title, one sentence, a date button | 3 s | Correct for a small task. The full LP page was too slow, or no file at all | [page](free/hello/) · [prompt](prompts/v0_warmup.md) |
| v1 | Claude Opus 5.5 (paid, as an agent in the folder, as Claude Code works) | One line: "explain linear programming" | ~4 min | A nine-section textbook chapter: nothing wrong, but no single idea | [page](claude/v1/) · [prompt](prompts/v1.md) |
| v2 | Claude Opus 5.5 | + the Lecture 2 slides and MATLAB code | ~5 min | The lecture retold, with the right optimum, but a loose idea of when the profit line "touches" the region | [page](claude/v2/) · [prompt](prompts/v2.md) |
| v3 | Claude Opus 5.5 | A full specification: plot, profit-line slider, corner table, hover, rules | ~3 min | One idea, built as specified, but the star gives the answer away and the LP box is cut off on a phone | [page](claude/v3/) · [prompt](prompts/v3.md) |
| v4 | Claude Opus 5.5 | v3's two issues described as *seen*, then machine-time sliders and shadow prices | ~8 min more | The checked page: every number equals MATLAB's | [page](claude/v4/) · [prompt](prompts/v4.md) |

The generated pages are published exactly as the agents wrote them, imperfections included. Only the
license line at the bottom has been added.

## What to take away

- **More detail in the prompt gives a better page.** A one-line prompt gives a generic chapter, and a specification
  gives the page you designed.
- **The model matters.** The free model handled a small task well but did not manage the full LP page.
- **Say what you see, not how to fix it.** v4 fixed v3's issues from a description of the symptoms.
- **Every page must be checked.** Even the best page needed fixes, and the agent's own test never looked at the
  screen.

## How each page was checked

1. Every number against the Lecture 2 slides: the corners, the optimum and the shadow prices.
2. The sliders pushed to their extremes and compared with MATLAB's `linprog`.
3. The picture: the profit line slopes down and moves parallel, and the corners sit on the lines.
4. A narrow window: does the page still fit a phone?
5. Asking the agent how the page computes the corners: does the answer make sense?

## Repository layout

```text
index.html          landing page: all versions side by side
claude/v1 … v4/     the pages made by Claude, one folder per version
free/hello/         the warm-up page made by the free model
prompts/            the exact prompts used for each version
images/             the screenshots used on the landing page
```

## Run it locally

Every page is a single self-contained HTML file with no libraries and no internet access. Open `index.html` in
a browser, or serve the folder:

```bash
python3 -m http.server 8000    # then open http://localhost:8000
```

## Not included

The course material (lecture slides, PDF and MATLAB code) is not in this repository. It belongs to the
lecturer, all rights reserved.

## Author

**Hao Li**, University of Southern Denmark: <hli@sdu.dk>

## License

| What | License |
|---|---|
| The web pages: `index.html`, `claude/`, `free/` | [MIT](LICENSE) |
| The prompts, screenshots and this README: `prompts/`, `images/`, `README.md` | [CC BY 4.0](LICENSE-CONTENT) |

You are welcome to reuse this material in your own teaching. Please credit it as:

> Hao Li, *One linear programme, four AI-made web pages*, Engineering Optimisation, University of Southern
> Denmark, 2026. <https://github.com/HaoLI-KU/EngOpt_workshop_LP_AI_demo>
