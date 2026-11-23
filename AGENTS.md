# Requirements-first workflow (Codex)

These rules apply to work in this repository. Follow existing higher-priority instructions and preserve any previously confirmed user requirements.

## 1. Perform clear tasks immediately

- Fix typos, perform simple lookups, and carry out unambiguous, clearly specified operations without asking questions.
- Do not invoke `interview-me` for a mechanical edit, simple informational query, or other self-contained request.
- Avoid unnecessary interviews when already-established context provides the information needed.

## 2. Mandatory interview gate before planning or coding

Before writing a plan, specification, or code for a non-trivial request, check four dimensions:

- **Why:** The higher-level purpose or problem the user needs solved.
- **Who:** Who the deliverable is for and who will use or benefit from it.
- **Success:** Observable completion criteria or how the user will judge success.
- **Constraint:** Binding limits and trade-offs (such as time, cost, platform, privacy, or quality).

If **any one** of these is absent or unresolved **and** a reasonable interpretation of it could materially change the approach, **invoke the `interview-me` skill first**, before planning or coding. Read and follow `.agents/skills/interview-me/SKILL.md`.

During the interview, offer one question at a time with a tentative guess, state confidence and key uncertainties, reflect the user's actual intent, explicitly identify out-of-scope work, and require explicit confirmation of the complete restatement. Do not silently fill consequential gaps with guesses. If an interview cannot run interactively, stop and flag the missing decision rather than pretending it was resolved.

## 3. Save confirmed intent and stop the turn

Once the user explicitly confirms the interview's statement of intent:

1. Save the confirmed intent in `docs/intent/<topic>.md` (create the directory as needed; use a descriptive topic name). Include **Why**, **Who**, **Outcome**, **Success**, **Constraints**, and **Out of scope**. Preserve the user's confirmed decisions; do not add unconfirmed assumptions.
2. Tell the user which file was saved. If the file cannot be saved, clearly report the blocker without claiming success.
3. **End the turn immediately after saving/reporting.** Do not draft a spec, create a plan, write implementation code, or perform any other downstream work in that turn. A fresh session can implement from the saved file.

This project's explicit save-then-stop rule overrides the upstream skill's default instruction to offer saving and stop before invoking any tool. The user asked for automatic saving of confirmed intent and a clean session boundary.

## 4. New-session handoff

At the start of a later implementation session, read the relevant `docs/intent/<topic>.md` before planning or coding. Respect its **Why** and **Out of scope**; only re-interview if a material new ambiguity arises.
