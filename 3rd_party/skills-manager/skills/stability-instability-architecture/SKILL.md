---
name: stability-instability-architecture
version: v2
description: Analyze agent tools, libraries, frameworks, or codebases for alignment with modern agent architecture principles including minimal orchestration, internal planning, deterministic stability layers, elastic rules, structured improvisation, and balanced evaluation design.
tags:
  - architecture
  - agents
  - frameworks
  - verification
  - orchestration
  - systems-design
  - review
  - evals
---

# PURPOSE

This skill analyzes tools, frameworks, libraries, or codebases used with coding agents (especially pi-based systems) and evaluates whether their architecture aligns with modern scalable agent design principles.

The core goal:

Detect whether the system supports structured improvisation with deterministic stability — or enforces brittle orchestration or rigid evaluation structures.

This skill produces:

- Architecture alignment analysis
- Risk detection
- Misalignment warnings
- Improvement suggestions
- Refactoring direction guidance

---

# CORE PHILOSOPHY

## Stability ↔ Instability Model

Modern agent systems alternate between:

Instability (agent reasoning)  
↓  
Partial stability (tools execute)  
↓  
Strong stability (verification)  
↓  
State transition  
↓  
Repeat  

Progress occurs through progressive stabilization — not rigid workflows.

---

## Structured Improvisation Model

Agents behave like:

Jazz improvisers.

Deterministic systems behave like:

Classical performers.

Good systems combine both.

Bad systems force:

- improvisation into deterministic layers
- deterministic logic into improvisational layers

---

## Elastic Governance Model

Rules exist in two forms.

### Hard Rules (Non-negotiable)

Must never be broken.

Examples:

- Verification required before state transitions
- Deployment safety checks
- Artifact integrity rules

---

### Soft Rules (Guidelines)

Can be bent when necessary.

Examples:

- Preferred workflows
- Planning heuristics
- Suggested sequences

---

## Internal Planning Principle

Modern models can plan internally.

Avoid:

Rigid external planners  
Step engines  
Mandatory workflow graphs  

Prefer:

Try → Observe → Adapt loops

---

## Minimal Orchestration Principle

Correct orchestration layers:

- State transitions
- Verification
- Infrastructure tools

Avoid orchestration of:

- Thinking
- Reasoning
- Tool strategy
- Execution order

---

# ANALYSIS PROCESS

Follow these steps when analyzing a system.

---

# STEP 1 — Identify Improvisation Zones

Locate flexible reasoning areas.

Look for:

- LLM reasoning loops
- Dynamic decision points
- Tool selection logic

---

# STEP 2 — Identify Stability Zones

Locate deterministic behavior.

Look for:

- Deployment scripts
- Verification scripts
- Tests
- Infrastructure logic

---

# STEP 3 — Detect Over-Orchestration

Warning signs:

Planner → Executor → Validator pipelines  
Mandatory step ordering  
Workflow routing graphs  

---

# STEP 4 — Detect Misplaced Stability

Incorrect examples:

Planning logic frozen into code  
Rigid execution paths  

Correct placement:

Verification  
Execution tools  

---

# STEP 5 — Detect Missing Stability

Look for:

State transitions without verification.

---

# STEP 6 — Classify Rules

Every rule must be:

Hard rule OR Soft rule

Misclassification creates fragility.

---

# STEP 7 — Evaluate Tool Design

Good tools:

Deterministic  
Reusable  
Auditable  

Look for:

deploy_container.sh  
verify_container.sh  
rollback.sh  

---

# STEP 8 — Evaluate State Machine Design

Look for:

Todo → Doing → Review → Verified → Done

Check:

- gated transitions
- proof requirements

---

# STEP 9 — Evaluate Planning Structure

Check whether planning is:

Flexible OR Mandatory

Mandatory planning increases rigidity risk.

---

# STEP 10 — Evaluate Elasticity

Ask:

Can workflows bend?  
Can alternative paths exist?  

Rigid systems fail under uncertainty.

---

# STEP 11 — Evaluate Eval Architecture (NEW in v2)

Evals stabilize systems — but excessive or poorly designed evals create rigidity.

This step determines whether evals reinforce flexibility or restrict it.

---

## Identify Eval Types

Classify evals into:

### Outcome-Based Evals (Preferred)

Verify results, not methods.

Examples:

- Endpoint returns 200
- Container running
- Tests pass
- Output file exists
- Performance meets threshold

These preserve flexibility.

---

### Behavior-Based Evals (Risky)

Verify how something was done.

Examples:

- Must use specific tool
- Must follow specific sequence
- Must generate structured plan
- Must call API in defined order

These restrict reasoning.

Flag aggressively.

---

## Detect Eval Explosion

Symptoms:

- Many narrow checks
- Excessive validation rules
- Frequent false failures

Risk:

System rigidity.

---

## Evaluate Eval Scope

Ask:

What failure does this eval prevent?

Accept eval if failure would create:

- Unsafe system state
- Data corruption
- Deployment instability

Reject eval if failure only causes:

- Minor inconvenience
- Style inconsistency

---

## Evaluate Eval Placement

Correct placement:

After execution  
After deployment  

Incorrect placement:

Before exploration  
Inside reasoning loops  

---

## Evaluate Eval Elasticity

Ask:

Could multiple valid solutions pass this eval?

If not:

Eval may be over-constraining.

---

## Classify Eval Tiers

Tier 1 — Safety Evals (Hard)

Examples:

- Deployment succeeds
- Data integrity preserved
- Tests pass

Tier 2 — Quality Evals (Soft)

Examples:

- Documentation exists
- Performance optimized

Tier 3 — Diagnostic Evals (Optional)

Examples:

- Benchmark comparisons
- Experimental checks

---

## Detect Hidden Orchestration via Evals

Flag when evals enforce workflow behavior.

Examples:

- Require fixed step order
- Require specific tool usage

---

## Evaluate Eval Density

Warning indicators:

- More eval logic than execution logic
- Frequent evaluation failures unrelated to outcomes

---

## Output Eval Risk Assessment

Report:

Eval Alignment Level: High / Medium / Low  
Eval Rigidity Risk: Low / Medium / High  
Eval Sufficiency: Under-verified / Balanced / Over-verified  

---

# OUTPUT FORMAT

## Summary

Alignment Level: High / Medium / Low  
Risk Level: Low / Medium / High  
Confidence: Low / Medium / High  

---

## Architecture Overview

Describe:

- Improvisation zones
- Stability zones
- Orchestration layers

---

## Misalignment Findings

List:

- Over-orchestration points
- Stability placement errors
- Rule misclassification
- Missing verification
- Eval rigidity risks

---

## Alignment Findings

List:

- Strong design decisions
- Effective boundaries
- Balanced verification

---

## Suggested Improvements

Provide concrete recommended changes.

---

# DESIGN PRINCIPLES CHECKLIST

[ ] Improvisation zones exist  
[ ] Stability zones exist  
[ ] Verification is deterministic  
[ ] Planning is flexible  
[ ] Hard rules protect safety  
[ ] Soft rules guide workflow  
[ ] Orchestration is minimal  
[ ] Tools are deterministic  
[ ] State transitions are gated  
[ ] System supports retries  
[ ] Eval system is outcome-based  
[ ] Eval density is reasonable  

---

# LONG-TERM GOAL

Enable systems that support:

Structured improvisation  
Deterministic stabilization  
Elastic governance  
Balanced evaluation  
Progressive reliability  

Controlled adaptability — not rigid orchestration.
