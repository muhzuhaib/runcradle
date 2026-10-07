# Privacy Policy

**Runcradle**
Version 1.0, 7 October 2026
Vendor: **Muhammad Zuhaib Zahid**

## The short version

**The plugin collects nothing.** It has no telemetry, no analytics and no crash reporting, and it
sends nothing to the Vendor. Your workflows, your source code and your secrets stay on your machine.

## What that means in detail

- **Workflows and run configurations.** Runcradle reads the workflow files of your repository in the
  IDE's process. The run configuration is saved in your project, as every IDE run configuration is.
- **Secrets.** Secret values are kept in the IDE password store on your machine. They are passed only
  to the run you start, and are never written to the shared settings, to a preset or to the run
  folder.
- **Run files.** Each run uses a working folder under your system's temporary folder. It holds the
  run's own settings and caches, never your secret values.
- **Network.** Runcradle itself makes no network requests. A run does what your workflow says: an
  action named in a `uses:` step is downloaded from its GitHub repository, and any network call your
  own steps make is made from your machine. Runcradle never pulls container images; it uses images
  already on your machine.
- **No usage tracking.** The plugin does not record which features you use or anything about your
  projects.
- **No accounts.** The plugin asks you for no personal information and has no sign-in of its own.

## What the Vendor does receive

Only what you choose to send:

- **A purchase.** JetBrains sells Runcradle as merchant of record and shares with the Vendor the
  sales information needed to be paid and to comply with tax law. What JetBrains collects at purchase
  is covered by the [JetBrains Privacy Policy](https://www.jetbrains.com/legal/docs/privacy/privacy.html).
- **Support you initiate.** If you email the Vendor or open an issue, the Vendor receives what you
  write, including any workflow or console output you attach. **Please remove secrets, tokens and
  internal host names before you attach anything.**

## Licence validation

Checking that a licence or trial is valid is performed by **the JetBrains IDE**, not by this plugin,
using JetBrains' own licensing service. That exchange is governed by JetBrains' terms and privacy
policy.

## Changes

If this policy ever changes, the revised version will be published at this address with a new date
at the top.

## Contact

Questions about this policy: Muhammad Zuhaib Zahid, via the email address on the JetBrains
Marketplace vendor profile for Runcradle, or by opening an issue on the public issue tracker linked
from the Marketplace listing.
