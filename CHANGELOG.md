# Change Log

## v1.4.0
    * New: two CRITICAL alarms on the rule that forwards Security Hub findings to SOAR, in the Security-Adm account in the main Region. `INFRA-SOAR-FindingsForwarding-Failure-CRITICAL` fires on the first delivery that fails permanently. `INFRA-SOAR-FindingsForwarding-Silence-CRITICAL` fires when the rule makes no delivery attempt for 24 hours, for example because it is disabled or deleted, or because Security Hub has stopped sending events. In both cases SOAR receives nothing and cannot report its own missing input. An AWS change in how EventBridge authorises deliveries to an event bus in another account stopped this forwarding without anything reporting it (see Installer v3.1.1); these alarms make such a stop visible.
    * New: both alarms notify the SNS topic `OpenSecOpsSOARFindingsForwardingFailures` in the Security-Adm account, when they fire and when they return to OK. While SOAR receives nothing, this topic is the only way these alarms reach anyone. The template creates no subscriptions.
    * **Action required**: subscribe your AWS administrators to the SNS topic `OpenSecOpsSOARFindingsForwardingFailures` in the Security-Adm account, in the main Region. Email subscriptions only become active once the confirmation link has been clicked.
    * The forwarding rule is now deployed to the main Region only. Security Hub aggregates findings, and the events for them, into the main Region, so a copy of the rule in another Region does nothing useful. Earlier versions deployed it to every Region; `./deploy` does not remove those copies.
    * **Action required**: in the Security-Adm account, delete the CloudFormation stack `INFRA-sec-hub-configuration` in every Region **except the main Region**. Use an administrator role that the `protect-infra-immutable` SCP exempts, such as the `AWSAdministratorAccess` permission set; the SCP denies other principals any change to `INFRA-*` stacks. The main-Region stack holds the forwarding rule, the two alarms and the topic. If it is deleted by mistake, the next deploy recreates it, but until then no findings reach SOAR and no alarm reports it, and the topic comes back without its subscriptions.

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
