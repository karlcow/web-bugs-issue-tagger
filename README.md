# web-bugs issue tagger

A tiny app to listen for GitHub webhook Issues events (ignoring when issues are closed) and add labels.

When an issue is created in the [web-bugs](https://github.com/webcompat/web-bugs), usually via [webcompat.com](http://webcompat.com), the app looks for label metadata in the form of a special HTML comment: `<!-- @browser: firefox -->`, for example. If found, our friend [Neptr](https://github.com/Neptr) will add the label and a comment.

### Environment variables

This repo assumes the following environment variables are set:

`USER_REPO`: in the format of `:user/:repo`

`OAUTH_TOKEN`: see [creating an access token for command line use](https://help.github.com/articles/creating-an-access-token-for-command-line-use)

### Testing locally

You can test things locally using a `payload.json` file:

`python app.py` to start the server.

``` bash
curl -X POST \
     -H 'content-type: application/json' \
     -H 'X-GitHub-Event: issues' \
     -d @payload.json \
     http://127.0.0.1:5000/turkeysandwiches
```

### License

This Source Code Form is subject to the terms of the Mozilla Public
License, v. 2.0. If a copy of the MPL was not distributed with this
file, You can obtain one at http://mozilla.org/MPL/2.0/.
