# Runcradle

Support, documentation and legal documents for the **Runcradle** plugin for JetBrains IDEs.

**[Get it on the JetBrains Marketplace](https://plugins.jetbrains.com/search?search=Runcradle)**

**This repository holds no source code.** It exists so that the plugin has a real issue tracker and
real documentation, both linked from the Marketplace listing.

- **Report a bug or ask for a feature:** [open an issue](../../issues). Every issue is read and
  answered.

---

## What the plugin does

Runcradle runs one job of a GitHub Actions workflow on your own machine, in local Linux containers,
from an ordinary IDE run configuration. Catch most failures before you push; GitHub remains the final
check.

### Free, with no time limit

- **Pick the workflow, job and event** from your repository's workflow files.
- **Pick rows of a static matrix.** Choose `node 22` and `integration` and only that combination
  runs. The choice is kept with the run configuration.
- **Step output in the Run console**, with each step's and job's result.
- **Stop cleans up.** Stop ends the run and removes the containers and volumes Runcradle started
  for it. Pulled images and networks stay for the next run.
- **One plain line when a job needs something only GitHub has**, such as an OIDC token or a
  deployment environment, before the run starts.

### Runcradle Pro

- **Preflight report** before the run: every finding marked blocked, warning or unknown, each one
  click from its workflow line, with the jobs it needs listed first.
- **Step results linked to their line**, so a failed step is one click away.
- **Team presets.** **Export preset** writes the run setup to a file your team commits, and
  **Import preset** reads one back. Secret values stay in each machine's IDE password store and are
  never written to a preset. Local overrides stay on your machine.
- **Run history** (**Tools, Runcradle Run History**): earlier local runs with their logs, secret
  values masked before anything is saved, and any two runs compared step by step.
- **Compare with GitHub**: a local run side by side with the latest GitHub run of the same job on
  the same branch, step by step with result and duration.
- **Push check**: tick **Run this job before every push from the IDE** on the run configuration's
  Runcradle Pro tab, and a push from the IDE push dialog runs it first and stops when it fails.

## Getting started

1. Start Docker Desktop in **Linux containers** mode.
2. Have a Linux image with the tools your job needs, for example `docker pull node:22`. Runcradle
   never pulls images by itself, so a run only uses images already on your machine.
3. In the IDE, open **Run, Edit Configurations**, click **+** and choose **Runcradle**.
4. Pick the workflow, the job and the event. For a matrix job, pick the rows you want.
5. Map each runner label the job uses to a local image, one per line, for example
   `ubuntu-latest=node:22`. Click **Check runtime**.
6. Press **Run**.

## Requirements and known limits

- A JetBrains IDE based on version 2026.2, on Windows.
- Docker in Linux container mode.
- Jobs on the Ubuntu runner labels `ubuntu-latest`, `ubuntu-24.04`, `ubuntu-22.04` and
  `ubuntu-20.04`, or jobs that set their own `container:`. Windows and macOS runners are not run.
- A local run is a close check of your workflow, and GitHub remains the final word. OIDC tokens and
  deployment environments cannot be reproduced locally, so the run says so before it starts.
- Docker Desktop's own licence terms apply to commercial use.
- A dynamic matrix (one built from an expression) is refused in the run configuration. Static
  matrices work.
- Workflow code runs on your machine as trusted code. Run workflows you trust.
- Run output is kept within the IDE console buffer, which you can resize in the IDE settings.

## Pricing

- **Personal:** $2.40 per month, or $24 per year.
- **Commercial:** $7.90 per month, or $79 per year.
- Running jobs is **free**, with no licence and no trial clock. The prices are for **Runcradle Pro**,
  which starts with a **free 30-day trial** from the run configuration's Runcradle Pro tab, or from
  **Help, Manage Subscriptions**.

## Privacy

Runcradle sends nothing to the vendor. It has no telemetry and no analytics. A run does what your
workflow says: an action named in a `uses:` step is downloaded from its GitHub repository, and any
network call your own steps make is made from your machine. **Compare with GitHub** (Pro) asks
api.github.com, and nothing else, for the latest run of your job, with a token you give it. The full policy is in
[PRIVACY.md](PRIVACY.md).

## Support

Open an issue here. Include the IDE and version (**Help, About**), the plugin version, the preflight
lines from the Run console, and the smallest workflow that shows the problem. **Remove secrets,
tokens and internal host names from anything you paste.**

## Legal

- [End User Licence Agreement](EULA.md)
- [Privacy Policy](PRIVACY.md)
- [Third-party notices](THIRD-PARTY.md)

The plugin itself is not open source. This repository is for support and documentation only.
