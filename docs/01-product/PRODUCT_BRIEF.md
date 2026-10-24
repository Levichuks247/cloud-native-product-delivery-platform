# Cloud-Native Product Delivery Platform with AI: Product Brief

| Item | Detail |
|---|---|
| Project type | Internal developer platform (a cloud product for developers), with an AI assistant |
| My role | Technical Product Owner (AI focus) |
| Main stakeholders | Engineering leaders, product managers, development teams, security, operations, and finance (FinOps) |
| Cloud provider | AWS, in Europe |
| AWS Regions | EU West 1 (Ireland) and EU West 2 (London). A second Region is used only if it is really needed. |
| Project period | October 26, 2026 to January 2027 (12 weeks, plus 1 spare week) |
| Product stage | MVP (first small working version) |
| Document status | Draft v0.4, October 24, 2026 |
| Author | Levi Chukwumeziri Anozie |

> **Please note:** This is a **made-up (simulated) scenario**. I wrote it for learning and for my portfolio. No real company, customer data, or live system is involved. All results come from a sample application and test data.

## The product has two parts

- **Part A: Delivery platform.** A safe, standard path that takes an app from code to the cloud.
- **Part B: AI Delivery Insights Assistant.** An AI helper that explains why a release failed and what to check next. It uses the evidence that Part A produces.

---

## 1. Summary

A large company has many software teams. Each team builds and releases its apps in its own way. The company wants one common, safe, and repeatable way to take an app from code to the cloud.

Today, each team decides alone how to:

- set up its cloud systems;
- release its apps;
- check for security problems;
- store passwords and keys;
- watch if apps are working;
- create and delete test environments;
- track how much each app costs.

This causes:

- different ways of working in each team;
- the same work done again and again;
- security risks;
- little visibility into how apps are running;
- difficulty knowing what each app costs.

The company wants a platform that gives every team a **golden path**. A golden path is one clear, automatic, and controlled route from source code to a running app in the cloud, with testing, security checks, and monitoring on the way.

The company also has a second problem. When a release fails, developers waste time reading long logs and reports. So the platform will include an **AI assistant** that reads the evidence and explains the failure in plain language. A human always stays in control.

The platform must balance four goals:

- **Business value:** faster and more predictable delivery.
- **Engineering efficiency:** less repeated setup, and less time lost on failures.
- **Security:** security checks built into the process.
- **Cost control:** clear cost information and limits.

This first version builds the base of the platform and a small, safe AI assistant. It does not try to solve every possible case.

## 2. The Problems

**Problem 1: No standard way to deliver products.** Developers can build apps, but every team chooses its own way to set up the cloud, release the app, scan for security problems, manage secrets, monitor the app, create and delete environments, and assign costs. This makes work uneven and slow. The company wants the **safe and responsible way to be the easiest way**.

**Problem 2: Failures are slow to understand.** When a release fails, the clues are spread across logs, scan reports, and deployment events. A developer who is not an infrastructure expert can spend a long time finding the cause. This slows delivery and causes frustration.

## 3. Product Vision

Give engineering teams a safe, standard, and cost-aware way to take an app from source code to a running AWS app, using one repeatable and controlled path.

When something goes wrong, an AI assistant helps the developer understand the problem quickly. It shows its evidence, says when it is not sure, and never acts alone.

Teams should spend less time on repeated setup problems and failure hunting. They should spend more time building features for customers.

## 4. Who Uses It

| User | Type | What they need |
|---|---|---|
| Application developer | Main user | A simple and clear way to move an app from code to the cloud. Quick, clear help when a release fails. |
| Engineering team / tech lead | Other user | Standard setup, release steps, security checks, and a clear view of how apps are running. Trust that AI answers are checked. |
| Security / compliance team | Other user | Confidence that the same security checks are applied every time, and that the AI cannot leak data or change systems. |
| Finance (FinOps) / engineering leaders | Other user | A clear view of who owns each cloud resource, tools to control cost, and a view of AI usage cost. |
| Platform team | Owner | Builds and looks after the platform, its templates, its automation, its rules, and the AI assistant. |

## 5. Main Persona: Alex, Application Developer

**Role:** Software developer.

**Goal:** Put an app on AWS without having to become an infrastructure expert, and fix failures fast.

**Problems today:**

- Sets up a release pipeline again for each project.
- Waits for the infrastructure team.
- Finds different release steps in different projects.
- Is not sure about the security rules.
- Cannot easily see the infrastructure behind the app.
- Cannot tell which resources cost money.
- When a release fails, does not know where to start reading.

**What Alex wants:**

- A standard repository, with infrastructure, security, and deployment basics already in place.
- A short, clear explanation when a release fails, with proof from the logs.
- Honest answers. If the AI does not know, it should say so.

## 6. Business Goals

| ID | Goal | What it means |
|---|---|---|
| BO-01 | Less friction | Cut the repeated work needed to get an app running in the cloud. |
| BO-02 | More consistency | Create one release process that many teams can reuse. |
| BO-03 | Security early | Run automatic security checks before an app reaches a live environment. |
| BO-04 | Ready to operate | Make sure each app has health checks, logs, and basic monitoring from the start. |
| BO-05 | Clear costs | Link each cloud resource to an owner, an environment, and cost information. |
| BO-06 | Reusable base | Build parts that can support more products later. |
| BO-07 | Faster problem solving | Help developers understand failed releases faster, using AI that shows its evidence. |
| BO-08 | Safe and trusted AI | Make sure the AI is tested, read-only, honest about what it does not know, and always reviewed by a human. |

## 7. What the MVP Includes

### Part A: Delivery platform

The MVP will show a **full golden path for one sample app**. The sample app will be a small Python API. (This will be confirmed in a decision record called ADR-001 in Week 3.)

**The path:** Source code → Pull request → Automatic checks → Security scan → Build container → Store the build → Deploy → Check the app is healthy → See how it runs

**Product delivery**
- A standard layout for app repositories.
- A clear development workflow, including pull requests.
- Automatic checks on every change.

**Cloud base**
- An AWS network with public and private areas.
- Use more than one Availability Zone (separate data centers) **only if it is needed and affordable**. This will be decided in a decision record.
- Controlled access to cloud resources.
- A place to run the app. We will pick the **simplest option that meets the needs**. We will use Kubernetes only if there is a good reason.
- A database or storage service **only if the sample app needs it**.

**Security**
- Automatic scanning for known vulnerabilities.
- A plan for storing secrets safely.
- Least-privilege access (give only the access that is needed).
- Basic security settings for the infrastructure.

**Operations**
- A health check for the app.
- Logs.
- Basic monitoring.
- An automatic check that a new release is healthy.

**Infrastructure**
- All infrastructure is written as code with Terraform.
- Reusable Terraform parts (modules) and settings for each environment.
- Checks that the infrastructure code is correct.

**Cost control**
- A tagging plan for all resources.
- A named owner for each environment.
- Written cost estimates.
- A plan to delete temporary resources.
- A budget alert, where it makes sense.

### Part B: AI Delivery Insights Assistant

A small AI assistant that helps developers understand failed releases. It is built in Weeks 7 to 11, after Part A produces real evidence.

**The MVP version will:**
- Read sample release results, scan reports, and deployment events (simple files at first).
- Explain what failed and where, in simple language.
- Show the evidence it used for each answer.
- Suggest safe next checks.
- Say clearly when it does not have enough information.
- Write draft bug reports or troubleshooting checklists **that a human must review** before use.

**The MVP version will not:**
- Deploy, change, or delete anything.
- Use real or sensitive data.
- Act alone, or make final decisions.

More detail is in section 13.

## 8. What the MVP Does Not Include

- Full AWS governance across many accounts.
- AWS Control Tower for the whole company.
- Links to on-premises systems or other hybrid setups.
- Support for more than one cloud provider.
- A worldwide, always-on design in many Regions.
- Advanced Kubernetes platform work and a full service mesh.
- Complex event-driven systems.
- Disaster recovery across continents.
- A full company-wide FinOps platform.
- A full DORA metrics platform.
- AI agents that work alone or have permission to change infrastructure.
- Large AI search systems over many documents (advanced RAG with vector databases).
- Real customer data or sensitive personal data.

Some of these may be added later.

## 9. How We Will Know the MVP Works

The MVP works if a sample team can take a sample app through the golden path with very little manual work, and the AI assistant gives useful, honest help when a release fails.

### Part A: Delivery platform

| Area | What success looks like |
|---|---|
| Delivery | A new app can follow the standard workflow. Code changes start automatic checks. Releases can be repeated with the same result. |
| Security | Security checks run on their own. A critical vulnerability stops the release, following the agreed rule. No secrets are saved in the code repository. |
| Infrastructure | Terraform can create the infrastructure again and again. The setup is saved in version control. |
| Operations | The app's health is checked automatically. Logs can be read. Basic signals about the app are available. |
| Cost | Resources have owner and environment tags. Cost estimates are written down. Temporary environments can be deleted after testing. |

### Part B: AI assistant

| Area | What success looks like |
|---|---|
| Usefulness | The assistant correctly explains failures in a test set of at least 20 questions. The pass target is set in Week 7. |
| Evidence | Every answer shows which log lines or reports it used. |
| Honesty | When the evidence is missing or unclear, the assistant says it does not know. It does not invent answers. |
| Safety | It is read-only. It cannot deploy or change anything. It resists instructions hidden inside logs (prompt injection). |
| Human control | Drafts of bug reports and checklists are always reviewed by a person. |
| Cost and privacy | AI usage is limited by a spending cap. No sensitive data goes to an outside model. |
| Reporting | Test results, failures, and limits are written in `docs/06-ai/`. |

**The most important test:** A team can follow a clear, repeatable path from app code to a running cloud app, and when it fails, can understand why quickly and safely.

## 10. Our Main Beliefs (Hypotheses)

**Belief 1 (platform):** A standard cloud delivery path will reduce repeated engineering work, make delivery more consistent, and make security and operations part of normal delivery, not something done at the end.

**Belief 2 (AI):** An AI assistant that explains failures using real evidence will help developers find the cause faster, as long as it is tested, honest about its limits, and reviewed by a human.

We will test these beliefs with the MVP and keep the evidence. The benefits in this brief are what we hope for. We will not say they are true until we measure them.

## 11. Cloud and Region Plan

The design is for AWS in Europe. It uses EU West 1 (Ireland) and EU West 2 (London) as the main examples.

The platform will not be tied to one Region. We will use settings (variables) and reusable Terraform parts, so we can change Region if rules, speed, or cost require it.

Using more than one Region is **not** a default MVP requirement. We will do it only if availability, recovery, or business needs justify the extra work and cost.

## 12. Main Principles

1. Product needs and measurable results decide our technology choices. We do not choose AWS services just to show them off.
2. Tools such as AWS services, Terraform, containers, CI/CD, security scanning, Kubernetes, GitOps, and monitoring are used only when they solve a real product or operations need.
3. We use AI only where it solves a clear problem. AI helps people. It does not replace their decisions.

## 13. AI Delivery Insights Assistant (Part B)

### The problem it solves
When a release fails, a developer must read long logs, scan reports, and deployment events. This is slow, and harder for developers like Alex who are not infrastructure experts.

### How it works
1. **Input:** sample pipeline results, scan findings, and deployment events.
2. **Processing:** a Python application sends the evidence to an AI model with clear instructions.
3. **Output:** a short explanation, the evidence used, safe next checks, and a clear "not enough information" message when needed.
4. **Later:** a draft bug report or troubleshooting checklist, **reviewed by a human** before it is used.

### Rules for the assistant
- Read-only. It never deploys, changes, or deletes anything.
- Its answers are guesses to check, not confirmed causes.
- It must show its evidence.
- It must say when it does not know.
- It must not follow instructions hidden inside logs or reports.
- No real or sensitive data is sent to an outside AI model.
- AI spending has a limit from the first call.

### How we will build it

| Week | Work |
|---|---|
| 6 | Prepare clear sample pipeline and deployment data |
| 7 | Write the AI product brief, user stories, acceptance criteria, risk list, and test set |
| 8 | Build the first prototype in Python, with a spending cap |
| 9 | Test with 20+ questions, study failures, improve, and test again |
| 10 | Connect to a controlled source of evidence, and plan monitoring of AI use and cost |
| 11 | Add the draft bug report or checklist, with human approval |
| 12 | Write the final AI evaluation report and case study |

### Documents
`docs/06-ai/AI_FEATURE_BRIEF.md`, `AI_RISK_REGISTER.md`, and `AI_EVALUATION.md`. Code goes in `ai-assistant/`.

## 14. Assumptions and Limits

- All data, apps, and stakeholders are made up for learning and for my portfolio.
- I study about 2 hours a day, 6 days a week.
- Cloud spending must stay within a small personal budget: **[TO DECIDE in Week 3]**. Temporary infrastructure is deleted after testing.
- AI API spending has a limit from the first call: **[TO DECIDE in Week 8]**.
- AI test pass target: **[TO DECIDE in Week 7]**.
- Italian public holidays reduce my time in Weeks 9 to 11.
- No secrets, passwords, or API keys are ever saved in the repository.

## 15. Document History

| Version | Date | Change |
|---|---|---|
| 0.1 | September 2026 | First version |
| 0.2 | October 24, 2026 | Added the simulated-scenario note, new dates, the AI feature idea, and assumptions |
| 0.3 | October 24, 2026 | Rewritten in simpler English |
| 0.4 | October 24, 2026 | AI assistant added across the whole brief as Part B of the MVP: problems, vision, users, goals, scope, success tests, beliefs, and build plan |
