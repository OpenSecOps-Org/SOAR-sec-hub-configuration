# Security Hub Configuration

This app propagates Security Hub control settings (the `TEAMFIX` and `AUTOFIXED` controls) from the Security Account to all member accounts. This means that as soon as an admin changes the enabled/disabled status of a Security Hub control in the GUI of Security Hub, that control will be similarly enabled or disabled in all member accounts in that region (and in that region only).

New accounts will automatically be configured similarly as they are created. Log in to the Security account and go to each region in turn. Disable and enable the Security Hub controls in each region as required. 

NB: For each Security Hub control change you make in terms of enabling or disabling it, all accounts will be visited behind the scenes by automation to change the setting. There is no batching. This means: don’t make more than three or four changes per region and minute or you will saturate the Security Hub service quota rapidly, with delays as a result. There’s no way we as AWS customers can influence the size of this quota, so it’s just one of the things to watch out for.


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
