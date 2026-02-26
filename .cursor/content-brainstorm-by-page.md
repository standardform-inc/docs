# Content brainstorm by page

Use this as an outline when writing each doc page. Aligned with sf-core product behavior, the simplified nav, and **Notion Help Center export** (`Help Center 28777126950c80e59664d50b4768c0ee.html` — welcome copy, 6-step flow, contact details, video link).

---

## 1. Welcome

**From Notion:** “Welcome to Standard Form’s help center! We aim to help you generate your schedule in minutes, so you can get back to more important things like teaching and clinical care.”

- **Watch Our Video:** Include link — https://screen.studio/share/pluhyEwN
- **CTA (from Notion):** “Please [schedule a call](https://calendar.app.google/7i3T12m5yoTfGC3Y6) with us — we’d love to learn about you, your schedules and see if our product may help!”

### Getting Started
- **Main message:** You should receive an email from Standard Form to get access.
- What to expect: invitation email (signup/login or accept-invite flow).
- How to log in for the first time; link to accept invitation if they have a token.
- Where to go after first login (dashboard, or start flow if no schedule yet).
- **Notion flow (map into Creating Block Schedules):** 1. Fill Basic Information → 2. Define your time boundaries → 3. Add Your Team → 4. Add Your Blocks → 5. Define Coverage → 6. Write Rules — plus Troubleshooting and Edit Your Schedule. Use this order in “Getting Started” as a quick overview with links to the detailed pages below.
- Who to contact if they didn’t receive the email (tie to Contact Us).

### What is Standard Form and who is it for
- **What it is:** Residency/physician scheduling software. You define schedules (block-based rotations or shift/call), add physicians, blocks, coverage, and rules; the system generates assignments.
- **Who it’s for:** Chief residents (build and manage schedules), administrators (set up org, invite team, settings), program directors (oversight, understanding how schedules work).
- Key concepts in one sentence each: Schedule, Block, Physicians (with rank e.g. PGY1–4), Coverage, Mandate, Rules (constraints), Leave preferences.
- Optional: one short paragraph on block schedules vs shift/call schedules; link to Creating Block Schedules and Create Shift Schedules.

---

## 2. Creating Block Schedules

*Notion labels: “2. Define your time boundaries”, “3. Add Your Team”, “4. Add Your Blocks”, “5. Define Coverage”, “6. Write Rules”, “Troubleshooting” — map to these pages.*

### Time
- **Notion:** “Define your time boundaries.”
- Schedule date range: start and end date for the schedule (time boundaries).
- Slot size: day, week, two-week, month (how one “slot” is defined for the solver).
- Statutory leave days: how many leave days per person the system accounts for (e.g. for fairness).
- Where this is set: Start flow “Time” step; or schedule details / edit in dashboard.
- Tip: End date must be after start date; slot size affects how blocks are placed.

### People
- **Notion:** “Add Your Team.”
- **What:** Adding and editing physicians (residents) who will be on the schedule.
- Required: first name, last name, email; rank (PGY1, PGY2, PGY3, PGY4).
- Where: Dashboard → Physicians; or Start flow “People” step.
- Roles: each person can have a role (e.g. by rank); roles are used for mandates and coverage.
- Why it matters: number of people and their roles directly affect whether the solver can meet coverage and mandates.
- Optional: bulk add, edit, or remove; unique email per account.

### Leave — how to collect leave via forms
- **Main message:** Residents submit leave preferences via a form; you send them a link (e.g. via email).
- How it works: Standard Form can send a “Leave preferences” email with a link to a form (LeavePreferencesInvitationEmail in product). Resident opens link, selects leave dates/ranges (e.g. vacation, conference), submits. Those dates are stored and used when generating the schedule so the solver avoids assigning them on leave.
- What you do as admin/chief resident: trigger or request that leave preference invitations are sent; share the link if your org uses a different channel.
- What residents see: form with schedule name, date range, and way to select leave (e.g. by slot or date range); optional labels (Personal Leave, Conference, Vacation).
- When to collect leave: ideally before generating or regenerating the schedule so the solver respects leave.
- Link to “People” (who gets the form) and “Failure to Generate” (too much leave can contribute to infeasibility).

### Blocks
- **Notion:** “Add Your Blocks.”
- **What:** Blocks are the rotations or activities you’re scheduling (e.g. “Wards”, “Clinic”, “Nights”, “ICU”, “Leave”).
- Adding/editing: label (name), description, load type, allowed roles (which ranks can be assigned), whether it’s a leave block or on-call.
- Where: Start flow “Blocks” step; or inside a schedule in the dashboard.
- Leave blocks: mark block as leave so the solver can assign leave time; link to Leave (forms) for pre-collected dates.
- Why order matters: blocks are the “columns” or “slots” the solver fills; coverage and mandate are defined per block.
- Optional: tags, colors (UI); unique label per schedule.

### Minimum Coverage
- **Notion:** “Define Coverage.”
- **What:** For each block (and optionally by day of week), you define how many people must be assigned (e.g. “2 residents on Wards at any time”).
- Where: “Coverage” step in Start flow or coverage UI in dashboard; linked to blocks.
- By role: coverage can be per role (e.g. PGY2+); person count per block (and optionally per day).
- Relationship to mandates: coverage = “how many needed at once”; mandate = “how many times each person must do this block.” Both must be satisfiable with your people count.
- Tip: If coverage numbers are too high for your roster, the schedule may fail to generate; link to Failure to Generate.

### Mandate
- **What:** Mandate = minimum number of times each person (by role) must be assigned to a block (e.g. “each resident must do Wards at least 2 times”).
- Where: Set per block (block mandate: role + block count).
- When to use: Only when there’s a real requirement (e.g. program requirements). Product guidance: don’t add mandate just to “balance” the schedule; overuse can cause infeasibility.
- Difference from coverage: coverage = “X people on this block at once”; mandate = “each person does this block at least N times.”
- Link to Failure to Generate: too many or conflicting mandates can make the problem infeasible.

### Rules
- **Notion:** “Write Rules.”
- **What:** Rules (constraints) are free-text descriptions of how the schedule should behave. The scheduling agent turns them into solver constraints (e.g. “no more than 3 nights in a row”, “spread weekends fairly”).
- Where: “Rules” step in Start flow or constraints/rules UI in dashboard; stored as schedule constraints.
- Best practice: Be specific and add examples. Vague or overly broad rules can lead to infeasibility or unexpected results.
- Examples: fairness, rest between heavy blocks, consecutive limits, distribution of unpopular blocks.
- Link to Failure to Generate: conflicting or impossible rules are a common cause of “schedule cannot be generated.”

### Failure to Generate
- **Notion:** “Troubleshooting.”
- **What:** Sometimes the solver returns “infeasible” — the current setup (people, blocks, coverage, mandate, rules, leave) cannot all be satisfied.
- In-app message (align with product): “Schedule cannot be generated. The scheduling constraints you’ve defined are impossible to satisfy with the current inputs.”
- What to review (mirror InfeasibleScheduleDialog):
  1. **Mandate and coverage vs number of physicians.** Ensure enough people to meet every block’s coverage and mandate.
  2. **Mandate use.** Only use mandate when there’s a real requirement; don’t add just for balance.
  3. **Rules.** Be as detailed as possible; add examples. Clear rules help the solver find a solution.
- Practical steps: reduce coverage or mandate, relax or simplify rules, add more people, or reduce leave if appropriate.
- Link back to Time, People, Leave, Blocks, Minimum Coverage, Mandate, Rules so they know where to edit.

---

## 3. Managing Block Schedules

*Notion: “Edit Your Schedule.”*

### Version controlling, when and how to regenerate
- **What:** Each time you generate or regenerate a schedule, the system creates a new “version” (schedule version) — a snapshot of the assignments. You can view the current version and, when you regenerate, the new result becomes the latest version.
- **When to regenerate:** After changing people, blocks, coverage, mandate, rules, or leave; or when you want a fresh solution (e.g. after collecting new leave).
- **How:** Use “Regenerate” / “Refresh” in the schedule view. Product shows a confirmation: “This will regenerate the schedule based on current inputs. Any draft changes to the schedule will be lost.”
- **Version controlling:** Explain that the current view is the latest version; regenerating replaces the current solution with a new one (draft changes are lost). If the product supports viewing or comparing past versions, document that here; otherwise keep it simple (current version only).
- **After regeneration:** If the result is infeasible, the app shows the infeasible dialog; link to Failure to Generate.

---

## 4. Create Shift Schedules

**From Notion (“Our Ask”):** “We’re now developing call schedules, we would love to learn how you develop your call schedules so we can shape our product to your needs. Please reach out!” — use in Call schedules and/or Contact.

### Call schedules
- **What:** Shift (call) schedules are a schedule type where assignments are shifts (time slots within days), not full block rotations. Used for call rotas, shift-based coverage.
- How it differs from block schedules: block = rotation for a slot (e.g. “week 1 = Wards”); shift = specific start/end times and days of week (e.g. “Monday 7a–7p”).
- Where to create: same dashboard “Create schedule” or Start flow; choose schedule type “Shift” / “Call.”
- Key concepts: shifts (time slots, day of week, extended vs standard); coverage and rules still apply but in a shift context.
- Optional: link to Schedule Links if call blocks are linked to a parent block schedule.

### Schedule Links
- **What:** A schedule can be linked to a “parent” schedule (e.g. a yearly block schedule as parent, and a call schedule as child). The child’s availability (when residents are available for call) can be driven by the parent’s block assignments.
- Use case: parent = block schedule (who is on which rotation when); child = call schedule (who is on call which days), so call only assigns people when they’re available per the parent.
- Where: set when creating or editing a schedule (parent schedule selection); or in schedule settings.
- Optional: short note that this is an advanced feature; link to Managing Block Schedules for versioning/regenerate on parent/child.

---

## 5. Settings

### Invite members
- **What:** Account owners (and possibly other roles) can invite team members to the organization (account). Invitees receive an email with a link to accept and join.
- How: Dashboard → Settings → Team (or Invite); enter email and choose role (e.g. owner vs member) if applicable.
- Accept flow: invitee clicks link → signup or login → accepts invite → sees the account in their dashboard.
- Who can invite: typically owners; members may have view-only or limited access (match product RLS/permissions).
- Link to Getting Started for what new users see when they receive an invite.

### App: coming soon
- **Content:** Short placeholder. “App-related settings will be available here soon.” No need for detail until the feature exists.

---

## 6. Contact Us

### Contact
**From Notion (“Need Help?”):**
- **Message or WhatsApp:** +1 415 972 9824 — [whatsapp us](https://wa.me/14159729824) *(Notion export had notion.sowa.me; use wa.me for WhatsApp.)*
- **Email:** [liz@heystandard.com](mailto:liz@heystandard.com)
- **Call:** [Schedule a call](https://calendar.app.google/pmYEbpb4Qk1TWswg7)
- **Copy:** “We’re happy to help! Alternatively, we’d love to chat and call us here.”
- When to contact: didn’t receive invitation email (Getting Started), technical issues, questions about feasibility or billing, feature requests, call schedule feedback (“Our Ask”).
- Optional: link back to Getting Started (no email) and Failure to Generate (stuck on infeasibility).

---

## Cross-links to add while writing
- Welcome → Getting Started, What is SF → Creating Block Schedules, Create Shift Schedules.
- Creating Block Schedules: Time/People/Leave/Blocks/Coverage/Mandate/Rules → Failure to Generate; Leave → People.
- Managing Block Schedules → Failure to Generate; Regenerate confirmation.
- Create Shift Schedules → Schedule Links; Call schedules ↔ Blocks (difference).
- Settings → Invite members ↔ Getting Started (invitation email).
- Contact Us ↔ Getting Started, Failure to Generate.
