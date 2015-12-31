(JENKINS-32258](https://issues.jenkins-ci.org/browse/JENKINS-32258) too many calls to rev-parse when pruning stale remote tracking branches

Git plugin 2.4.1 introduced a regression in the prune stale remote
tracking branches behavior.  Previously there was a single call to
rev-parse the HEAD revision, but with git plugin 2.4.1, there is a
call to rev-parse every branch name in the repository.  The bug report
describes a repository with 17000+ branches and how that bug causes a
delay of more than 5 minutes completing the build.

I confirmed the bug exists in git plugin 2.4.1 by creating a job which
builds the master branch and uses the text finder plugin to mark the
build unstable if `git.*rev-parse.*branch-[0-9][0-9]` is visible in the
build log.  Then I created 100 branches in the repository named branch-00
to branch-99.`
