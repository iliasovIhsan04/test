im syimyk frontend dev


now i change this is file.


559

First, got "your branch is ahead of origin/master by 3 commits" then my app has reverted to an earlier time with earlier changes.

How can I get what I spent the last 11 hours doing back?

git


reset HEAD@{1}. – 
Amber
 CommentedApr 11, 2012 at 3:21
19
Only if the codes are staged (using git add), they are kept in git and can be found back easily using commands like git fsck --lost-found. – 
Landys
 CommentedFeb 13, 2017 at 12:29
10
Accidentally dropped a commit I should have kept when rebasing. This totally saved me from redo-ing a couple hours worth of work. – 
josephting
 CommentedJan 10, 2019 at 6:30
3
Do lost commits get auto-deleted after a certain period of time? – 
TheTechRobo
 CommentedSep 4, 2020 at 23:47
4
@TheTechRobo36414519 git-gc eventually cleans up old reflog entries, and once nothing references a commit its objects will eventually be cleaned up too. The conditions under which the reflog is cleaned up can be set via git-gc's config options git-scm.com/docs/git-gc#Documentation/git-gc.txt-gcreflogExpire (at the time of this comment, the default expiry for reflog entries is 90 days for commits which are reachable, and 30 days for commits which are unreachable from curr



Before answering, let's add some background, explaining what this HEAD is.

First of all what is HEAD?
HEAD is simply a reference to the current commit (latest) on the current branch.
There can only be a single HEAD at any given time (excluding git worktree).

The content of HEAD is stored inside .git/HEAD and it contains the 40 bytes SHA-1 of the current commit.
wefwefwef
