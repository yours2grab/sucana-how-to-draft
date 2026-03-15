# How-To Draft Article Agent — Product Doc

> Updated 2026-03-15

## What This Is

A Claude Code skill that documents everything we build into a step-by-step how-to article. After every build session, this agent reads the conversation, extracts every micro-step, and writes a comprehensive guide that a 10-year-old can follow to get the same result.

## Build Status

| Item | Status |
|------|--------|
| SKILL.md (5-step agent) | DONE ✅ |
| PRODUCT.md | DONE ✅ |
| PRD.md with ASCII architecture | DONE ✅ |
| Step 0: Context interview (one question) | TESTED ✅ |
| Step 1: Load voice | TESTED ✅ |
| Step 2: Extract conversation (PRODUCT.md as source of truth) | TESTED ✅ on 4 builds (dashboard, meeting agent, hooks & angles, SEO pipeline) |
| Step 3: Structure + write article (9 writing rules merged in) | TESTED ✅ full 14-stage article produced |
| Step 4: Checker (6 checks × stages + PRODUCT.md cross-check) | TESTED ✅ caught 10 issues, all fixed |
| Step 5: HTML preview + save to 2 locations | BUILT ✅ |
| Mandatory jargon list (13 terms) | BUILT ✅ |
| Mandatory PRODUCT.md stages (create + update) | BUILT ✅ |

## The 5 Steps

| Step | What |
|------|------|
| 0 | Ask "Tell me why you built this and what problem do you like to solve?" |
| 1 | Load Virgil_Voice_MASTER.md |
| 2 | Extract conversation. PRODUCT.md is source of truth. Document what user said, not what Claude did. |
| 3 | Structure + write the article. 9 writing rules baked in. Full format: Do this, What happens, We tested this by, Why we did this. |
| 4 | Checker. 6 checks per stage. PRODUCT.md cross-check. Fix all failures before showing. |
| 5 | Generate HTML preview, open in browser, wait for approval, save .md to both locations. |

## Key Decisions

- Step 4 (old "Write the Steps") merged into Step 3. Writing rules apply during writing, not as a separate pass.
- PRODUCT.md is the ONLY source of truth. Never produce steps from the README.
- Every stage has 4 parts: Do this, What happens, We tested this by, Why we did this.
- "We confirmed it worked" is NOT a test. Show what you checked and what you found.
- "What happens" is max 2 sentences. Test results go in "We tested this by."
- "Why we did this" is always one sentence.
- Jargon list grows over time. Every new term gets added permanently.
- Two mandatory stages in every article: create PRODUCT.md early, update PRODUCT.md at the end.
- Missing features from PRODUCT.md get added as stages automatically. Don't ask. Don't flag. Just add.
- Article shown as HTML preview before saving. User approves in browser.

## Tested On

| Build | Stages | Checker Result |
|-------|--------|----------------|
| Beehiiv Dashboard | 9 stages | Passed after jargon fixes |
| Meeting Agent (lead magnet) | 14 stages | 84/84 checks passed |
| Hooks & Angles (ad flywheel) | 8 stages | Passed after gap fixes |
| SEO Article Pipeline | 9 stages | Passed, caught missing cover image stage |
| LFG Morning Routine | Blocked (no PRODUCT.md) | Correctly flagged missing source of truth |

## Output Locations

| File | Where |
|------|-------|
| HTML preview | Marketing/Newsletter/Content/how-we-built-[name].html |
| Final .md | Marketing/Newsletter/Content/how-we-built-[name].md |
| Copy .md | Virgil Second Brain/Content/Blog Content/how-we-built-[name].md |

## Files

```
Sucana/Skills/how-to-draft.skill/
├── SKILL.md      — the agent (5 steps, 333 lines)
├── PRODUCT.md    — this file
└── PRD.md        — full spec with ASCII architecture
```

## Trigger Words

"how to draft" or "document this build" or "write the how-to"
