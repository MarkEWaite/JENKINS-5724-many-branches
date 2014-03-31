Git plugin test repository for many branches
============================================

This repository was created from a script provided as part of the fix
for [JENKINS-5724](https://issues.jenkins-ci.org/browse/JENKINS-5724).
An O(n^2) algorithm was used in the Git plugin filterTipBranches
method.  The fix for [JENKINS-5724](https://issues.jenkins-ci.org/browse/JENKINS-5724)
switched that to a much faster algorithm.
