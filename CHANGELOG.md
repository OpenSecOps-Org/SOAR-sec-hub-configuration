# Change Log

## v1.3.13
    * `README.md` gains the OpenSSF Best Practices Passing-level badge (project entry [bestpractices.dev/projects/12827](https://www.bestpractices.dev/projects/12827)).

## v1.3.12
    * Converted to OpenSecOps supply-chain framework (libraryless variant). This component ships a SAM template + CloudFormation snippets with no Python library dependencies (empty `__init__.py`, no runtime Python), so the release pipeline emits a deterministic source archive (`git archive HEAD`) + SLSA Build L1 in-toto provenance attesting to it, both Sigstore-signed (`.bundle` files alongside each artefact). The customer-side `scripts/deploy.py` (Installer v3.0.11+) verifies the signatures against the maintainer identity (`peter@peterbengtson.com` via `https://github.com/login/oauth`) before any `cfn deploy`. Adds daily CVE scan and OpenSSF Scorecard workflows (both trivially pass — no library deps to scan). See `SECURITY.md`.

## v1.3.11
    * Enable auto-close workflow for external pull requests, enforcing the cathedral governance policy uniformly across all OpenSecOps repositories. Pull requests from non-team authors are closed automatically with a redirect comment pointing to the bug-report template, the GitHub Security Advisory flow, and the fork-under-MPL-2.0 path.

## v1.3.10
    * Updated GitHub remote references in publish.zsh script to use only OpenSecOps-Org, removed Delegat-AB

## v1.3.9
    * Updated GitHub organization name from CloudSecOps-Org to OpenSecOps-Org.
    * Updated references to CloudSecOps-Installer to Installer.

## v1.3.8
    * File paths corrected for the new name of the installer.

## v1.3.7
    * Updated LICENSE file to MPL 2.0.

## v1.3.6
    * Updated publish.zsh to support dual-remote publishing to CloudSecOps-Org repositories.

## v1.3.5
    * Python v3.12.2.
    * `.python-version` file to support `pyenv`.

## v1.3.4
    * Updated the README.

## v1.3.3
    * Recreated repo.
