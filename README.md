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
from an ordinary IDE run configuration. You see whether a workflow change works before you push it
and wait for CI.

- **Pick the workflow, job and event** from your repository. The jobs it depends on are shown before
  the run.
- **Pick rows of a static matrix.** Choose `node 22` and `integration` and only that combination
  runs. The choice is kept with the run configuration.
- **Preflight before anything starts.** The job and your local Docker are checked first. Each
  finding is marked blocked, warning or unknown and links to its line in the workflow file.
- **Step output in the Run console.** When a step fails, its line in the workflow is one click away.
- **Stop cleans up.** Stop ends the run and removes the containers and volumes Runcradle started
  for it.

## Getting started

1. Start Docker Desktop in **Linux containers** mode.
2. Have a Linux image with the tools your job needs, for example `docker pull node:22`. Runcradle
   never pulls images by itself, so a run only uses images already on your machine.
3. In the IDE, open **Run, Edit Configurations**, click **+** and choose **Runcradle**.
4. Pick the workflow, the job and the event. For a matrix job, tick the rows you want.
5. Map each runner label the job uses to a local image, one per line, for example
   `ubuntu-latest=node:22`. Click **Check runtime**.
6. Read the preflight findings, then press **Run**.

## Share the setup with your team

- Workflow, job, event, matrix choice, runner images and inputs are saved with the run
  configuration. **Export preset** writes them to a file your team can commit, and **Import preset**
  reads one back.
- Secret values are kept in the IDE password store on each machine. They are never written to the
  shared settings or to a preset.
- Local overrides (variables only you need) stay on your machine.

## Requirements and known limits

- A JetBrains IDE based on version 2026.2, on Windows.
- Docker in Linux container mode.
- Jobs on the Ubuntu runner labels `ubuntu-latest`, `ubuntu-24.04`, `ubuntu-22.04` and
  `ubuntu-20.04`, or jobs that set their own `container:`. Windows and macOS runners are not run.
- A local run is a close check of your workflow, and GitHub remains the final word. OIDC tokens and
  deployment environments cannot be reproduced locally, so preflight reports them before the run.
- A dynamic matrix (one built from an expression) is refused in the run configuration. Static
  matrices work.
- Workflow code runs on your machine as trusted code. Run workflows you trust.
- Run output is kept within the IDE console buffer, which you can resize in the IDE settings.

## Pricing

- **Personal:** $2.40 per month, or $24 per year.
- **Commercial:** $7.90 per month, or $79 per year.
- **Every licence starts with a free 30-day trial.** The first time you run a Runcradle
  configuration the IDE offers it, or use **Help, Manage Subscriptions**.

## Privacy

Runcradle sends nothing to the vendor. It has no telemetry and no analytics. A run does what your
workflow says: an action named in a `uses:` step is downloaded from its GitHub repository, and any
network call your own steps make is made from your machine. The full policy is in
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
