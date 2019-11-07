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

# Tesr journal
1. Create base policy
2. Attached GitHub to tfe-pm-3 instance , organization "acme"
3. Created **main** policyt set , pointing right now to : 
  Galser/tfe-policy-fork-test ⋅ a562440 . , at 10:39
4. Repointing main policy set to branch : "https://github.com/Galser/tfe-policy-fork-test/tree/f-NEW-FORK" 
5. Infor in Poli Set window, still showing the same commit : https://github.com/Galser/tfe-policy-fork-test/commit/a562440557cfcae0943dc4c5e9bbbdcf0fae0f7a
6. Making new commit into new branch.
  - RESULT :  commit is not VISIBLE, dashboard still showing top-commit from 10:39  a562440
7. Creating new branch **"fork2"**
8. Right now run is failing as it should be in policy : 
```
Sentinel Result: false

Sentinel evaluated to false because one or more Sentinel policies evaluated
to false. This false was not due to an undefined value or runtime error.

1 policies evaluated.

## Policy 1: tfe-policy-fork-test/fake_hour.sentinel (hard-mandatory)

Result: false

FALSE - tfe-policy-fork-test/fake_hour.sentinel:2:1 - Rule "main"
  TRUE - tfe-policy-fork-test/fake_hour.sentinel:2:15 - hour >= 0
  FALSE - tfe-policy-fork-test/fake_hour.sentinel:2:29 - hour < 12
```
Interesting - after run "Policy Stes" dashboard still showing only repo main path, but - last commit - `d339199` ,
this one : https://github.com/Galser/tfe-policy-fork-test/commit/d3391999d215b29c34924d1ceacc2c60e9f34ef6
9. Updating policy ib branch **"fork2"** to pass
  Branch is now on `0d0c531`: https://github.com/Galser/tfe-policy-fork-test/commit/0d0c531e7a42309fcb47df044f363fbb1eb3a0b0
10. No changes in TFE Policy Sets Dashboard, even after refresh, still showing OLD commit `d339199` but on correct branch - fork2. So now -= run still SHOULD FAIL if TFE reading incorrect com,mit. and pass - if CORRECT
Previous run : https://tfe-pm-3.guselietov.com/app/acme/workspaces/tfe-minimal/runs/run-YjDH5Q3bRMfCteAc

11.  New run :  FAILED! still same commit displayed in dashboard : `d339199`



