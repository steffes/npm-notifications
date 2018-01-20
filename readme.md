# npm-notifications
[![Greenkeeper badge](https://badges.greenkeeper.io/steffes/npm-notifications.svg)](https://greenkeeper.io/)
![travis build](https://travis-ci.org/steffes/npm-notifications.svg?branch=master)
[![dependencies Status](https://david-dm.org/steffes/npm-notifications/status.svg)](https://david-dm.org/steffes/npm-notifications)


Using greenkeeper to get notifications on package updates. This is easier than creating a slack bot or any of the other ways that npm mentions in their blog post [npm web hooks](http://blog.npmjs.org/post/145260155635/introducing-hooks-get-notifications-of-npm)

- remove `&& exit 1` from the npm test script ([commit 0cbaa3d](https://github.com/steffes/npm-notifications/commit/0cbaa3dd2b80b049fa77f88acab438e690006489))
- `npm install --save ` packages you want updates on
- add travis-ci in repo settings
- commit something to enable travis
- go to [greenkeeper.io](https://greenkeeper.io) and enable it on this repo
- merge greenkeeper's initial commit
- set notifications on your 3rd party github app like iOctocat or GitHawk for PRs
