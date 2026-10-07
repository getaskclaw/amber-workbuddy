[简体中文](README.zh-CN.md) · English

# amber-workbuddy

> ⚠️ **Correction (2026-10-02, second)**: one defense case, A-d511f9e8, is now NA on every lane (the exam room did not grade the file the model gave in, and the grader asks for something the task text does not say). The denominator and the **number of passed cases do not change**; every lane's total now carries `'`. In this repo's issue tables, read that cell as NA. Everything else stays as published; the [correction notice](https://github.com/getaskclaw/amber/blob/main/docs/corrections-2026-10-02-a-d511f9e8.en.md) governs.

> ⚠️ **Correction (2026-10-02)**: the papers below were answered by a model that left its own paper and touched grading material; they count neither as a pass nor as a fail. deepseek-v4.1-flash @ WorkBuddy direct lane: 3 papers (A-a5608487, A-984e80ee, A-24bcf707) now NA, score 16/24 → **13'/24**. The cause was an isolation fault in our exam setup; the fault is ours. The rest of this page stays as published; where they differ, the [correction notice](https://github.com/getaskclaw/amber/blob/main/docs/corrections-2026-10-02.en.md) governs.

> **From W40 the exam room is isolated**: from 2026-W40 the exams in this repo are taken in an isolated room, so W40 cells cannot be compared cell by cell with W37 or W39 (see the [2026-W40 issue](results/2026-W40.en.md)).

Running the private **AMBER** benchmark against models on WorkBuddy (CodeBuddy). Results are public; questions are not. There are two channels so far: the ACP lane (the ACP mode of Tencent's CodeBuddy CLI, with a server-pushed model catalog; W37) and the direct lane (`www.workbuddy.ai/v2`; W39 and W40).

> **In one line**: four models on the WorkBuddy direct lane each took the same 24 field tasks in the isolated W40 exam room, and passed **deepseek-v4.1-flash 18'/24 · glm-5.3-flash 17'/24 · hy4-preview-f 16'/24 · minimax-m3 16'/24**. The four are almost the same on the hands-on tasks (coding, delivery, ops, requirements); they differ on the judgment tasks (vision, review, attribution).
>
> A `'` after a score means some cases are NA: not counted as a pass or a fail. The reason for each NA is in the issue. hy4-preview-f has two rows on the board: the ACP lane (W37) and the direct lane (W40). They are different lanes in different exam rooms, so they are not compared, and this page does not say the model got stronger or weaker.

## Scoreboard

<!-- scoreboard:start -->

| Group | Axis | What it tests | deepseek-v4.1-flash (WorkBuddy direct) · [W40](results/2026-W40.en.md) | glm-5.3-flash (WorkBuddy direct) · [W40](results/2026-W40.en.md) | hy4-preview-f (WorkBuddy direct) · [W40](results/2026-W40.en.md) | minimax-m3 (WorkBuddy direct) · [W40](results/2026-W40.en.md) | hy4-preview-f (WorkBuddy ACP) · [W37](results/2026-W37.md) |
|---|---|---|:-:|:-:|:-:|:-:|:-:|
| Building | Coding | Implement the spec correctly | 5/6 | 5/6 | 5/6 | 5/6 | 5/6 |
|  | Delivery | Done means handed in | 3/3 | 3/3 | 3/3 | 3/3 | 3/3 |
|  | Ops | Follow the runbook | 6/6 | 6/6 | 6/6 | 5/6 | 6/6 |
|  | Requirements | Ship A when A was asked | 1/1 | 1/1 | 1/1 | 1/1 | 1/1 |
|  | Convergence | Finish, don't spin | 1/1 | 1/1 | 1/1 | 0/1 | 1/1 |
| Judging | UI | Build the page to the mock | 0/1 · 1 NA | 0/1 · 1 NA | 0/1 · 1 NA | 0/1 · 1 NA | 1/1 |
|  | Vision | Spot defects in screenshots | 1/1 | 0/1 | 0/1 | 1/1 | 0/1 |
|  | Defense | Plug every hole in the validator | 0/2 · 1 NA | 0/2 · 1 NA | 0/2 · 2 NA | 0/2 · 1 NA | 0/2 · 1 NA |
|  | Attribution | Pin defects to their root cause | 0/1 | 0/1 | 0/1 | 0/1 | 0/1 |
|  | Review | Inspect someone else's work | 1/2 | 1/2 | 0/2 | 1/2 | 1/2 |
|  | **Total** |  | **18'/24** | **17'/24** | **16'/24** | **16'/24** | **18'/24** |

Each cell = cases passed / cases on that axis (a case is one scored task). NA = the case was voided or put on hold; it counts as neither a pass nor a fail, and a total carrying `'` has at least one NA. Most axes hold only 1–2 cases, so one case moves the reading: do not over-read small gaps. Sittings are from different weeks; every number is a snapshot.

<!-- scoreboard:end -->

The W37 column is the ACP-lane hy4-preview-f; W40 is the direct lane in the isolated room: the columns cannot be compared cell by cell.

## What this is

- A 'lane' is one vendor's shop/API for a model name; a 'case' is one task, a 'run' is one sitting (a case with more than one variant has more runs).
- One `results/YYYY-Www.md` per edition: same questions, same harness (the program that runs the exam and scores it), full library per model; models on the same lane side by side.
- Each edition pins: library size and hashes, per-case defect-hunt score and pass/fail, terminal states (how the run ended), token usage where the lane reports it (this lane does not — wall clock stands in), latency, environment fingerprint, and verdicts written under evidence rules.
- Questions, oracles, transcripts (full answer logs)s and intermediate artifacts are **never published** (see "Publishing rules").
- Sister repos: [amber-gpt](https://github.com/getaskclaw/amber-gpt), [amber-crof](https://github.com/getaskclaw/amber-crof), [amber-ollama](https://github.com/getaskclaw/amber-ollama), [amber-devin](https://github.com/getaskclaw/amber-devin), [amber-opencode](https://github.com/getaskclaw/amber-opencode), [amber-commandcode](https://github.com/getaskclaw/amber-commandcode), [amber-deepseek](https://github.com/getaskclaw/amber-deepseek), [amber-doubao](https://github.com/getaskclaw/amber-doubao), [amber-goldenpotato](https://github.com/getaskclaw/amber-goldenpotato), [amber-kimi](https://github.com/getaskclaw/amber-kimi), [amber-stepfun](https://github.com/getaskclaw/amber-stepfun). Scores for the same deepseek-v4.1 family on official/relay lanes live in those repos; this repo's benchmark axis is **across models on the WorkBuddy lanes** (the ACP lane and the direct lane are read separately). Cross-repo citations always carry date and band.
- AMBER is an agentic field benchmark (build / ops / review / vision / requirement-drift (the requirements change mid-task)); spec and authoring tools at [getaskclaw/amber](https://github.com/getaskclaw/amber); the questions themselves are private.

## W40 in one minute

![W40 divergence: the 5 of 24 cases where the four direct-lane models differ](results/assets/2026-W40-diff.en.png?v=20261005)

Same direct lane, same day (2026-10-04, UTC), high band, same isolated exam room, same 24 cases and hashes: **deepseek-v4.1-flash 18'/24, glm-5.3-flash 17'/24, hy4-preview-f 16'/24, minimax-m3 16'/24**. On the vision case (A-ea80d793) the room's image request was rejected in the first sitting; after the room fix only that cell was re-taken. The brand case A-d9b79b46 and the defense case A-d511f9e8 are on hold (NA) on all four lanes. The per-case matrix, the exam conditions and the explanation of each NA are in the [2026-W40 issue](results/2026-W40.en.md). The other 19 cases have the same result for all four: 14 all pass, 3 all fail (A-87c472cb, A-a317e74b, A-cdc3d11a), 2 all NA (A-d511f9e8, A-d9b79b46). The full 24-case matrix is in the issue.

## W37 in one minute

Same ACP lane, same high band, same 23 cases and hashes: **hy4-preview-f 17/23** (build 5/6 + OPS 6/6 sweep + ui-build 12/12), **deepseek-v4.1-flash 15/23** (A-be92627f 9/9 — first-ever pass on that case; second verify-face pass overall). Per-case matrix and lane ledger in the [2026-W37 issue](results/2026-W37.md).

The W37 numbers above use the issue's own count (23 cases). The "Scoreboard" above counts this ACP-lane hy4-preview-f row as 18'/24 on the current library: the 17/23 plus the convergence case that was added later and passed, with defense case A-d511f9e8 as NA through the all-lane hold. W37 and W40 differ in channel and exam room, so they are not compared cell by cell.

## Publishing rules (red lines)

1. Publish only: scores and totals, token usage (where the lane reports it), speed, verdicts.
2. Never publish: question content, oracles/graders, transcripts, candidate workspaces, any intermediate that could rebuild a question.
3. Every edition pins: model ID, effort band (the thinking-effort setting), date (UTC), harness version, per-case content hash (bundle_sha (per-case content-hash fingerprint)) — checkable against the public hash index in [amber](https://github.com/getaskclaw/amber).
4. Case IDs and question structure are private: published results use only stable aliases (A-xxxxxxxx, hash-derived) plus bundle hashes as handles; internal case IDs, variant names, and question descriptions never appear.
5. Tone: this is a community measurement, not an attack on any vendor. Data speaks; wording stays simple.

## A methods caveat

Same model name, same provider, two runs can still differ — sampling parameters, load, and server-side versions all drift; relay/aggregator lanes add a framing layer on top. Every conclusion here carries a date and a band, and lanes get re-measured regularly. A single day's number is a snapshot, not a law.

## Results index

| Edition | Candidate | Score (W37: 23 cases / 21-case public subset; W40: 24 cases) | One-liner |
|---|---|---|---|
| [2026-W40](results/2026-W40.en.md) | **deepseek-v4.1-flash** (WorkBuddy direct) | **18'/24** | Highest of the four, no timeouts; passed the vision re-take; attribution A-a317e74b 14/15, one check short |
| [2026-W40](results/2026-W40.en.md) | glm-5.3-flash (WorkBuddy direct) | **17'/24** | Passed review A-47eea242 (fault-finding 4); this channel does not accept image input, vision case not passed |
| [2026-W40](results/2026-W40.en.md) | hy4-preview-f (WorkBuddy direct) | **16'/24** | 3 NA (2 defense, 1 UI); saw the picture but did not pass the vision case; a different lane from the W37 ACP row, not compared |
| [2026-W40](results/2026-W40.en.md) | minimax-m3 (WorkBuddy direct) | **16'/24** | Most losses (6); did not pass the convergence case; brand case NA (on hold; changed from a loss to NA on 2026-10-05); 9 missing cases made up the same day |
| [2026-W37](results/2026-W37.md) | **hy4-preview-f** (x0.00 free tier) | **17/23** (15/21) | Second-tier entry on debut; OPS 6/6 sweep + ui-build 12/12; verify 0/3, review/vision still fail |
| [2026-W37](results/2026-W37.md) | deepseek-v4.1-flash (x0.00 free tier) | **15/23** (13/21) | A-be92627f 9/9 = first-ever pass on that case (second verify-face pass overall); one case below its official-GA sibling with swapped structure |
| [2026-W38 correction notice](results/2026-W38-correction.en.md) | W38 full-library review: 0 cells reversed · 1 held here | 1 W37 hy4 vision cell held |

## Disclaimer

Not affiliated with or sponsored by Tencent or CodeBuddy/WorkBuddy. Scores are snapshots of a specific week and band, not buying advice.