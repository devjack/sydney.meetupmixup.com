# MeetupMixup 2017

You probably want [sydney.meetupmixup.com](https://sydney.meetupmixup.com).

This site has a few moving parts:

 - New content/posts are added to `/content`
 - Updates to the theme are best made in the [meetupmixup theme](https://github.com/devjack/sydney.meetupmixup.com-theme)
 - static assets are best placed in `/static`

 Hint: Clone the meetup mixup theme into the local repo but do not commit it:

 ```
 git clone https://github.com/devjack/sydney.meetupmixup.com-theme.git ./themes/mumu-theme
 ```

## Contribution
PR new contribution to master. Approved merges will be auto deployed from master.

## Deployment.
This site it built and deployed using Codeship.

### Tests
#### Setup
```
. golang.sh
go get -v github.com/gohugoio/hugo
git clone https://github.com/devjack/sydney.meetupmixup.com-theme.git ./themes/mumu-theme
rm -rf public/
```

#### Pipeline
```
GIT_HASH=$(git rev-parse --short HEAD) ${GOPATH}/bin/hugo
```

### Deployment
Deployment requires a number of configured environment variables:

 - GO_VERSION = "1.8.1"
 - NETLIFY_SITE (private env var)
 - NETLIFY_TOKEN (private env var)


```
npm install netlify-cli
node node_modules/netlify-cli/bin/cli.js deploy -s ${NETLIFY_SITE} -t ${NETLIFY_TOKEN} -p public/
```
