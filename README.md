# tfe-policy-fork-test
TFE Sentinel Policy fork test 

# Test steps

1. Create base policy
2. Set it for workspace in TFE
3. Attach another (minimal) TF code to the same workspace
4. Run (observe policey used)
5. Fork policy repo (this one)
6. Set up FORKED BRANCH as the source of policy for workspace
6. Make commit
7. Check whether the commit is visible - e.g. policy got update in TFE

