### Current behavior:

Renovate fails to update `unleash/client` with error `DEBUG: Dependency unleash/client has unsupported/unversioned value 1.8.081 (versioning=composer)`

**I suspect this is caused by the leading zero in the patch version.**

When I manually updated to `1.8.181`, and then ran renovate again, the error is gone from the logs and renovate created an MR for the upgrade to the latest `1.11.282`.

The composer package [unleash/client](https://packagist.org/packages/unleash/client) (GitLab feature flags) has an unusual versioning strategy where the patch number has 3-4 digits (e.g. `1.11.282`), and the last 2 digits are the php version (xx72 for php 7.2, xx80 for php 8.0, xx81 for php 8.1 etc)

### Expected behavior:

Renovate updates `unleash/client` from `1.8.081` to the latest version.
