# Online Appendix: Qualitative Coding

This appendix documents the thematic analysis supporting the four-dimensional framework presented in the paper. It follows Braun & Clarke's reflexive thematic analysis [3], with first-cycle open coding feeding into nine second-cycle themes, which are in turn synthesized into four dimensions of developer experience (Cognitive Load, Systemic Dependency, Behavioral Style, Risk Aversion). Inter-rater reliability across themes: Krippendorff's α = 0.818.

Quotes and specific internal details have been abstracted for confidentiality.

---

## 1. First-Cycle Thematic Coding: Perception vs. Reality

This first-cycle open coding analyzes the gap between developer perception and objective system data regarding spurious CI failures, establishing baseline cognitive biases and initial behavioral strategies across the 11 interviewees.

| ID  | Perceived Spurious | Observed Spurious | Cognitive Bias                                                                                  | Initial Action / Strategy                                                                          |
| :-- | :----------------- | :---------------- | :---------------------------------------------------------------------------------------------- | :------------------------------------------------------------------------------------------------- |
| I1  | 70–80%             | 76%               | Perception matches data; aware the main branch breaks due to others.                            | **Passive Wait & Blind Rebase**: Waits a couple of hours, then rebases.                            |
| I2  | 5–10%              | 46%               | Minimizes the problem unless the merge is highly urgent.                                        | **Pragmatic Wait**: Switches contexts; treats the failure as a background issue.                   |
| I3  | 25%                | 37%               | Attributes failures heavily to architectural coupling rather than randomness.                   | **Active Mitigation**: Uses rebase command to rebase without losing peer approvals.                |
| I4  | 10%                | 39%               | Displays passive acceptance of failures.                                                        | **Passive Rebase**: Blindly rebases and ignores the pipeline, waiting for an external fix.         |
| I5  | 20–30%             | 34%               | Differentiates between core infrastructure issues and local merge conflicts.                    | **Contextual Analysis**: Actively engages to fix merge conflicts; ignores broader spurious issues. |
| I6  | 20%                | 36%               | Attributes failures to highly coupled code.                                                     | **Immediate Rebase & Verification**: Retries to check for transient error; runs local tests.       |
| I7  | 50%                | 64%               | Aware failures are high due to exposure to core framework code.                                 | **Iterative Rebase**: Rebases continuously because changes must be merged urgently.                |
| I8  | 30–40%             | 24%               | High awareness driven by timezone blockers (waiting on other regions).                          | **Pragmatic Fix**: Temporarily disables or fixes the failing test locally to unblock.              |
| I9  | 40%                | 42%               | High exposure due to touching code that crosses multiple team boundaries.                       | **Active Investigation**: Spends significant time monitoring and investigating.                    |
| I10 | 30–40%             | 38%               | Highly aware due to very long build times (up to 1.5 hours).                                    | **Extreme Verification**: Runs integration pipelines multiple times locally before merging.        |
| I11 | 90%                | 35%               | Feels highly impacted by shared integration tests that fail frequently.                         | **Log Digging**: Spends significant time manually searching through logs to find the root cause.   |

---

## 2. Second-Cycle Coding: Nine Themes

Representative first-cycle codes were synthesized into nine second-cycle themes through axial coding. Each theme captures either a technical manifestation of CI instability or a latent psychological/organizational state.

### 2.1 Themes feeding Cognitive Load

| Theme                           | Definition                                                                                                                                 | Aggregated Codes                                                                                                                                                     |
| :------------------------------ | :----------------------------------------------------------------------------------------------------------------------------------------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Passive Waiting**             | The direct quantifiable cost defined by time spent passively waiting for resolutions, pipeline runs, or other teams.                       | Time waste; Passive wait; Compound failure; Rebase loop failure; Compounded instability; Compounded/dependent MRs; High active troubleshooting time.                 |
| **Cognitive Cost of Uncertainty** | The psychological toll of non-deterministic feedback, where the primary cost is flow disruption and eroded trust rather than time.       | Uncertainty of rebase; Non-determinism; Simple/preventable errors; Timezone issues; Tool friction; Wasted brain cycles.                                              |

### 2.2 Themes feeding Systemic Dependency

| Theme                                      | Definition                                                                                                                                                           | Aggregated Codes                                                                                                                                                                            |
| :----------------------------------------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------- |:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **External Control: Systemic Blockers**    | Organizational and architectural barriers that block the developer's ability to act, confirming the failure is external to their code.                               | Lack of control; Organizational slowness; External ownership / wait for domain owner; Review bottleneck; Systematic instability; Architectural coupling; Organizational accountability.     |
| **Fragmentation and Tribal Knowledge Gaps** | Reliance on social workarounds and non-standardized tools due to the absence of a unified, responsive, and authoritative source of failure information.             | Historical/social validation (checking past commits, chat complaints); git blame to reach authors; Multi-tool fragmentation.                                                                |

### 2.3 Themes feeding Behavioral Style

| Theme                        | Definition                                                                                                                              | Aggregated Codes                                                                                                                                                                                                 |
| :--------------------------- | :-------------------------------------------------------------------------------------------------------------------------------------- |:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Reactive/Passive Coping**  | Immediate offload strategy; developers trade the high friction of active investigation for the tolerable friction of passive waiting.   | Immediate rebase / blind rebase; Passive acceptance / tolerance; Comfortable context switching; Sequential-incremental switch; Push emergency fix.                                                               |
| **Proactive/Investigative Coping** | High-friction technical diagnosis used to regain control and certainty before committing to a fix or rebase.                    | Run failing tasks/tests locally; Module separation / pattern recognition (distinguishing affected parts via domain knowledge and log signature); Recognize clear infrastructure failures (OOMKill, pod startup). |

### 2.4 Themes feeding Risk Aversion

| Theme                              | Definition                                                                                                                                                 | Aggregated Codes                                                                                                                                                                                                                                                 |
| :--------------------------------- | :--------------------------------------------------------------------------------------------------------------------------------------------------------- |:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Trust Calibration**              | Action and speed requirements: Minimal Viable Speed (~15–20 min pipelines) combined with flexible auto-action models prioritizing convenience and control. | Minimal viable speed target; Faster feedback loop; Fail broken tasks/tests faster; Action-confirmation vs. don't-bother-me models; Automatic rebases; Auto-rebase for known infrastructure problems; Notification-with-action vs. notification-requiring-action. |
| **Transparency**                   | Informational safeguards necessary to overcome uncertainty and earn adoption by justifying automated action with clear evidence.                           | Source transparency (confidence score + similar cases); First-occurrence data; Accountability (who is fixing, is there an MR open); Systemic visibility / main branch health; Notify responsible person.                                                         |
| **System Resilience (Trust Erosion)** | Critical deal-breaker risks and the functional requirements necessary to mitigate systemic instability beyond simple classification.                  | Inaccurate prediction; Worsening instability / breaks branch; Delayed false positive; Wasted waiting time; Insulation tag (resource management, visibility); Need for a single source of truth.                                                                  |

---

## 3. Synthesis into Four Dimensions

The nine themes were aggregated into four mutually exclusive and collectively exhaustive dimensions. Each dimension served as an independent ordinal variable in the Phase 3 correlation analysis (see Table 3 in the paper).

| Dimension              | Summary                                                                                         | Underlying Themes                                                                 |
| :--------------------- | :---------------------------------------------------------------------------------------------- | :-------------------------------------------------------------------------------- |
| **Cognitive Load**     | Cognitive overhead from non-deterministic feedback; flow disruption independent of hours lost.  | Passive Waiting; Cognitive Cost of Uncertainty.                                   |
| **Systemic Dependency** | The extent to which velocity is blocked by factors outside the developer's control.            | External Control: Systemic Blockers; Fragmentation and Tribal Knowledge Gaps.     |
| **Behavioral Style**   | The investigative and remediation strategy deployed in response to CI instability.              | Reactive/Passive Coping; Proactive/Investigative Coping.                          |
| **Risk Aversion**      | The developer's demand for certainty and transparency in automated interventions.               | Trust Calibration; Transparency; System Resilience.                               |

### Ranking Heuristics (Phase 3)

For each dimension, developers were ranked 1 (highest severity/need) to 11 (lowest):

- **Cognitive Load** — High (1–3): those citing *uncertainty* and *non-determinism* as the primary cost, reporting inefficient context-switching or "wasted brain cycles." Low (9–11): those demonstrating successful personal adaptation, tolerance, or comfort with waiting. *Certainty about what to do, not raw exposure to spurious failures, distinguishes high-impact from low-impact developers.*
- **Systemic Dependency** — High (1–3): those explicitly citing organizational errors, emergency merge procedures, coupled code, or lack of visibility into external failures requiring reliance on others to unblock them. Low (9–11): those framing the problem as uncertainty or low-cost transient error.
- **Behavioral Style** — High (1–3): those whose initial action involves cognitively expensive approaches (local reproduction, fixing/disabling external tests, dedicated module analysis). Low (9–11): those defaulting to blind rebase and passive waiting.
- **Risk Aversion** — High (1–3): those explicitly demanding near-100% certainty, transparent evidence and source justification, or citing false-negative/positive deal-breakers. Low (9–11): those preferring passive automation and trusting the system by default.

---

## 4. Rank Assignments with Documented Evidence

To support the Phase 3 ordinal conversion, each rank is grounded in documented thematic evidence from the interview transcripts. The tables below summarize the bucket (L/M/H), numeric rank, and a one-line justification per interviewee per dimension.

### 4.1 Cognitive Load

| ID  | Bucket | Rank | Justification                                                                                                                                               |
| :-- | :----- | :--- | :---------------------------------------------------------------------------------------------------------------------------------------------------------- |
| I1  | L      | 10.5 | Low active cost: pipeline failures absorbed by passive review-waiting time; externalizes the bottleneck to reviews rather than CI.                          |
| I2  | M      | 5.5  | Quantifiable cognitive friction (lost approvals across timezones) but tolerates non-urgent delays without flow spiraling.                                   |
| I3  | H      | 1.5  | Explicitly identifies "non-deterministic developer experience" as root cause; describes inefficient context switching across multiple unstable branches.    |
| I4  | L      | 10.5 | Normalizes the issue as "normal annoying"; de-prioritizes failures via reactive social triage rather than deep investigation.                               |
| I5  | M      | 5.5  | High quantified time cost (12–15 h/month) but adapts through fast, practiced context switching.                                                             |
| I6  | M      | 8.5  | Aware of cognitive cost (lost approvals) but controls it with rapid context-switch protocol (~15 min).                                                      |
| I7  | H      | 3.5  | Extreme flow disruption: "takes an hour to get back into your own work"; highest raw time loss (~2 h/day) under time pressure.                              |
| I8  | H      | 3.5  | Loss of agency from lack of domain context drives high cognitive cost; 2–3 h active time per failure.                                                       |
| I9  | H      | 1.5  | Explicit "wasted brain cycles" evidence; compounded flow friction from juggling dependent MRs; half-day loss on urgent patch days.                          |
| I10 | M      | 7    | Comfortable context switching with structural workarounds (avoids Tuesday pushes); frustration directed at organizational errors rather than personal flow. |
| I11 | M      | 8.5  | High active triage cost (~1 h discovery) but insulates personal work from delivery impact.                                                                  |

### 4.2 Systemic Dependency

| ID  | Bucket | Rank | Justification                                                                                                                                       |
| :-- | :----- | :--- | :-------------------------------------------------------------------------------------------------------------------------------------------------- |
| I1  | L      | 11   | Primary barrier is uncertainty, not external blockers; no mention of finding owners or waiting on emergency merges.                                  |
| I2  | M      | 8.5  | Timezone-driven organizational constraint (lost approvals from Amsterdam) but mitigates via active local validation.                                |
| I3  | H      | 5    | Severe fragmentation ("several hoops" across chatting tools, build platforms and version control system); systemic infrastructure failures (container bootstrap, timeouts).                 |
| I4  | H      | 6    | Explicit reliance on emergency merges to unblock; high-toil social triage to identify and delegate to fix owner.                                    |
| I5  | M      | 8.5  | Uses social triage as secondary step; architectural dependency (permissions to run tests locally) rather than organizational failure.               |
| I6  | M      | 8.5  | Explicit loss of agency when master fails, mitigated by structured reporting protocol and short context switches.                                    |
| I7  | H      | 4    | Blocked by critical organizational events (Tuesday release days); high-toil social triage via build scans and pinging known fixers.          |
| I8  | H      | 3    | Maximum external constraint: timezone block + lack of domain context forces mandatory waiting on Amsterdam owners.                                  |
| I9  | H      | 1.5  | Explicitly identifies "finding the right person to solve it" as core problem; infrastructure issues linger as unassigned organizational failures.    |
| I10 | H      | 1.5  | Explicitly frames master breakage as "organizational error"; structurally adapted workflow (no Tuesday pushes) to route around systemic dependency. |
| I11 | M      | 8.5  | Architectural inertia (coupled legacy modules) dominates; high local agency with self-sufficient triage and local reproduction.                     |

### 4.3 Behavioral Style

| ID  | Bucket | Rank | Justification                                                                                                                              |
| :-- | :----- | :--- | :----------------------------------------------------------------------------------------------------------------------------------------- |
| I1  | L      | 10.5 | Default passive wait and rebase; investigation only after 3–4 failures, limited to log/social scanning.                                     |
| I2  | M      | 5    | Structured escalation: rebase first, then systematic local test run and comparison to master.                                               |
| I3  | H      | 2    | Default is local reproduction ("I run the same command that fail at that stage locally"); rebase only as last resort.                       |
| I4  | L      | 10.5 | Blind rebase default; primary effort is log analysis and social delegation rather than technical diagnosis.                                 |
| I5  | H      | 2    | Immediate local run of failing build task before rebasing; high technical agency.                                                          |
| I6  | M      | 6    | Rebase first, then consistent local build task run to confirm externality.                                                                 |
| I7  | H      | 2    | High escalation: local reproduction on exact hash, commit history checks, willingness to fix external failures personally.                  |
| I8  | M      | 4    | Domain-driven triage via build platforms; highest technical agency for fixing ("fix or disable the test by ourselves").                   |
| I9  | M      | 9    | Primary effort is social triage (git blame + direct owner contact) rather than technical reproduction.                                       |
| I10 | M      | 8    | Current triage is reactive; historical proactivity (writing local tooling to mimic CI/CD).                                                  |
| I11 | M      | 7    | High local reproduction toil (~1 h setup) with commitment to technical investigation.                                                       |

### 4.4 Risk Aversion

| ID  | Bucket | Rank | Justification                                                                                                       |
| :-- | :----- | :--- |:--------------------------------------------------------------------------------------------------------------------|
| I1  | H      | 1.5  | Demands 100% certainty; rejects probabilistic confidence scores ("gambling with my time").                          |
| I2  | M      | 6    | Systematic transparency demand: confidence score + similar cases to manage risk.                                    |
| I3  | H      | 3.5  | Demands deterministic system; deal-breaker is tool creating a "mess" that breaks development or main branch. |
| I4  | L      | 10   | Maximal passive trust: prefers passive automation without notification; tolerates risk for successful outcome.      |
| I5  | M      | 7    | Wants source transparency; primary deal-breaker is tool causing longer wait than manual triage.                     |
| I6  | L      | 11   | Lowest explicit feature demand; vague risk concerns; priority is architectural fix over tooling.                    |
| I7  | H      | 1.5  | Absolute certainty demand: "perfectly stable master"; prefers slow/stable over fast/flaky.                          |
| I8  | L      | 8    | Pragmatic/fact-based: needs information only if actionable; prioritizes faster pipelines over transparency.         |
| I9  | H      | 3.5  | Demands automation with accountability: system must assign a fixer, not just notify.                                |
| I10 | M      | 5    | Structural control: prioritizes stability over speed; made workflow changes to mitigate risk.                       |
| I11 | L      | 9    | Speed-driven control: wants step-by-step notification but ultima                                                    