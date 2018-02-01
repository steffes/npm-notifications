# npm-notifications
[![renovate badge](https://img.shields.io/badge/Renovate-enabled-green.svg)](https://renovateapp.com/)
[![Greenkeeper badge](https://img.shields.io/badge/Greenkeeper-disabled-lightgrey.svg)](https://greenkeeper.io/)
[![travis build](https://travis-ci.org/steffes/npm-notifications.svg?branch=master)](https://travis-ci.org/steffes/npm-notifications)
[![dependencies Status](https://david-dm.org/steffes/npm-notifications/status.svg)](https://david-dm.org/steffes/npm-notifications)
[![Dependency Status](https://beta.gemnasium.com/badges/github.com/steffes/npm-notifications.svg)](https://beta.gemnasium.com/projects/github.com/steffes/npm-notifications)
[![Known Vulnerabilities](https://snyk.io/test/github/steffes/npm-notifications/badge.svg)](https://snyk.io/test/github/steffes/npm-notifications)

There are many different options to get notified on npm package updates. Npm mentions using webhooks and hosting a service, like a slackbot, in their blog post [npm web hooks](http://blog.npmjs.org/post/145260155635/introducing-hooks-get-notifications-of-npm). Here are some other ways that I found that worked with various levels of friction in setup.

## 🖌️ [Renovate](https://github.com/apps/renovate)

Best and easiest option in my opinion. Renovate will open a PR after package updates *and* has a ton of awesome config settings. Here I'm checking for updates [every monday](https://renovateapp.com/docs/configuration-reference/configuration-options#schedule) with [automerge](https://renovateapp.com/docs/configuration-reference/configuration-options#automerge) in my `renovate.json`
```js
{
  "extends": [
    "config:base"
  ],
  "automerge": true,
  "major": {
    "automerge": false
  },
  "schedule": "every monday"
}
```
## 🌳 Greenkeeper.io

Use greenkeeper to automatically open a PR after any new package update. Greenkeeper's pull requests are nice because they include a changelog and sometimes links to the commits. Here are the steps to set it up:

- remove `&& exit 1` from the npm test script in `package.json` ([commit 0cbaa3d](https://github.com/steffes/npm-notifications/commit/0cbaa3dd2b80b049fa77f88acab438e690006489))
- `npm install --save ` packages you want updates on
- add travis-ci in repo settings
- commit something to enable travis
- go to [greenkeeper.io](https://greenkeeper.io) and enable it on this repo
- merge greenkeeper's initial commit
- set notifications on your 3rd party github app like [iOctocat](https://ioctocat.com/) or GitHawk for PRs
- Greenkeeper does not have the option to auto merge the greenkeeper PRs after a successful travis build. Use [kkemple/greenkeeper-keeper](https://github.com/kkemple/greenkeeper-keeper) to auto merge but note it requires you hosting the service somewhere. Heres a quick deploy link: [![Deploy](https://www.herokucdn.com/deploy/button.svg)](https://heroku.com/deploy?template=https://github.com/kkemple/greenkeeper-keeper)

## Libraries.io emails and RSS feed

Sign into [libraries.io](https://libraries.io) with github and have it watch your project. Libraries.io will create an RSS feed of the entire dependency tree. That means this project has a feed of 460 packages instead of just the 13 in my package.json. I recommend not watching this project and just manually selecting subscribe for each package you want email notificaitons on or a collective rss feed from.

## [Gemnasium](https://beta.gemnasium.com/sign-in) email or Slack notifications
![gemnasium.png](/img/gemnasium.png)


## [bithound.io](https://bithound.io) Slack or HipChat notifications
![bithound.png](/img/bithound.io.png)

