# SOAR Sec Hub Configuration

[![Daily CVE scan](https://github.com/OpenSecOps-Org/SOAR-sec-hub-configuration/actions/workflows/daily-scan.yml/badge.svg)](https://github.com/OpenSecOps-Org/SOAR-sec-hub-configuration/actions/workflows/daily-scan.yml) [![OpenSSF Scorecard](https://github.com/OpenSecOps-Org/SOAR-sec-hub-configuration/actions/workflows/scorecard.yml/badge.svg)](https://github.com/OpenSecOps-Org/SOAR-sec-hub-configuration/actions/workflows/scorecard.yml)

Sets up the custom event bus to pass events to the Org account for processing by the SOAR. 


## Deployment

First make sure that your SSO setup is configured with a default profile giving you AWSAdministratorAccess
to your AWS Organizations administrative account. This is necessary as the AWS cross-account role used 
during deployment only can be assumed from that account.

```console
aws sso login
```

Then type:

```console
./deploy
```
