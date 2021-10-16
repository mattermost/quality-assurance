# Submission
### Links to PRs & Issues

PR: https://github.com/mattermost/mattermost-server/pull/18451
JIRA: https://mattermost.atlassian.net/browse/MM-36862
Issue: https://github.com/mattermost/quality-assurance/issues/22

### Description of Issue

Summary

When deleting a reply in a thread we should also delete the participant
from the participants array. This should happen if they have no other
replies in that thread.

### Tests Ran

Test 1:
1) Reply to someones root post 
2) Open this thread on the RHS
3) Delete your reply (you should not have any other replies on this thread)
Result: On the main channel view, user avatar is removed from the root post footer and reply count is updated.
This should also apply to the avatars in the row of the Threads list.

Test 2:
1) Reply to someones root post 
2) Reply angain to someones root post 
3) Open this thread on the RHS
4) Delete one reply
Result: On the main channel view, user avatar is still there from the root post footer, reply count is updated.
The avatars in the row of the Threads list is still there too.

Test 3:
1) Reply to someones root post 
2) Delete the root post
Result: Root post and threads are deleted.
