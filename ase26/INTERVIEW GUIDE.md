# Questionnaire / Semi-Structured Interview Guide

**Description:** This document outlines the core questions and targeted follow-up probes used during the semi-structured interviews. The guide is designed to be conversational while ensuring all key qualitative dimensions (Time Impact, Cognitive Load, Trust, Risk Aversion) are captured consistently across participants.

## Intro

> Thank you for participating. This interview is about understanding your experience with CI/CD pipeline failures, specifically cases where builds fail but then pass after rebasing without code changes. <br> <br>
> I'll ask about your workflow, velocity barriers, and ideas for improvement. There are no right or wrong answers — I'm interested in your honest experience.  <br> <br>
> The interview takes about 30-45 minutes. I'd like to record it for transcription purposes — the recording will be deleted after transcription, and all quotes will be anonymized. Is that okay?  <br> <br>
> Consent checklist:
> - [x] Explained purpose and duration 
> - [x] Obtained permission to record 
> - [x] Confirmed anonymity

---

## Section 1 - Context and Experience (RQ1)

**Goal:** To establish a baseline understanding of the interviewee's role, their typical workflow, and their conscious awareness of the spurious failure problem.

**Q1. Overall Experience**
> As a gut feeling, what percentage of your pipeline failures do you think are 'spurious' — meaning they aren't actually caused by your code changes?

**Probes:** *(If estimate is very low/high compared to data):*
* Our data shows X% of your failures were spurious, but you estimated Y%. Why do you think there's a gap between the data and your perception?
* Does this happen more frequently when you work on specific modules or types of changes (e.g., core framework vs. isolated builds)?

---

## Section 2 - Barriers and Impact (RQ1)

**Goal:** To understand the full cost — not just raw hours lost, but the cognitive load, emotional impact, and flow disruption caused by instability.

**Q2. Time Impact**
> When a spurious failure happens, about how much total time does it typically cost you, from the first alert until it's finally green?

**Probes:**
* About how many hours per month would you say these failures cost you in total?
* Is that time mostly spent on passive waiting, active investigating, or just rebasing?

**Q3. Context Switching**
> When you get that failure notification, what are you usually doing? And what do you actually do — do you drop everything to investigate, or do you finish what you're working on first?

**Probes:**
* If you do switch tasks, how much it takes you to get back into your original work?
* Does it matter *when* in your workflow a failure happens (e.g., if you need to merge something urgently vs. if it can wait a couple of days)?

**Q4 / Q5. Most Frustrating Aspect & Productivity Impact**
> What's the absolute most blocking or frustrating part of dealing with these failures? On a scale of 1-10, how would you rate the overall impact of CI instability on your productivity?

---

## Section 3 - Coping Mechanisms & Knowledge Gaps (RQ2)

**Goal:** To uncover the behavioral workarounds and tribal knowledge developers rely on to navigate an unstable CI environment.

**Q6. Tools & Team Knowledge [Knowledge management gap]**
> When you suspect a failure is not your fault, how do you verify this? What is your immediate technical or social action?

**Probes:**
* Do you use specific channels, check raw logs, or troubleshoot locally?
* How easy is it to find out *who* (which domain owner) is actively fixing the broken build?
* Do you ever just "blindly rebase" hoping it will pass, without investigating why it failed?

---

## Section 4 - Tooling Requirements & Risk Aversion (RQ3)

**Goal:** To identify the functional requirements for a mitigation tool by assessing the developer's risk tolerance, demand for certainty, and preferences for automation.

**Q7. Ideal Solution [Big picture]**
> If you had a magic wand to solve the CI instability problem right now, disregarding current technical or organizational limitations, what would the solution look like to you?

**Probes:**
* Are you thinking of an architectural fix (e.g., decoupled code) or a tooling fix (e.g., faster feedback loop)?

**Q8. Trust & Information [UI]**
> If an internal tool were to predict that a failure is spurious and suggest an action, what specific information or evidence *must* it display for you to trust it?

**Probes:**
* Is a "Confidence Score" enough, or do you need to see where it got that information from?
* Do you need to know if it's happening right now to other developers?

**Q9. Preferred Action [Actions]**
> Do you prefer a tool that automatically takes action for you in the background (like auto-rebasing) and doesn't bother you, or a tool that just notifies you so you can take action yourself?

**Probes:**
* Would you be okay with the tool taking action if it guaranteed you wouldn't lose your code approvals?
* Do you prefer it to identify the responsible person and notify them instead?

**Q10. Deal-Breakers [Risks]**
> What behavior from an automated CI mitigation tool would cause you to completely lose trust and turn it off forever?

**Probes:**
* What happens if it gives you a "False Positive" (noise) or its prediction is off?
* What happens if you end up waiting even longer for the tool than you normally would?
* How many times can the tool fail before you lose confidence?

**Q11: If you had to choose between two improvements, which would help you more: making all pipelines 50% faster, or eliminating spurious failures entirely?**

**Probes:**
* If you chose faster pipelines, what is your acceptable target time? (e.g., 5, 10, or 15 minutes?)
* Why are faster pipelines better than entirely eliminating the random failures for your specific workflow? (Or vice versa)

---

## Conclusion

**Q12. Additional Thoughts**
> Is there anything else about your CI experience, developer productivity, or our approach to solving this that we haven't covered today?

**Probes:**
* Any final thoughts on preventive approaches vs. reactive tools?
> Thank you so much for your time and insights!