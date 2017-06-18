# Go Jekyll

When I grow up, I want to be a [Go](https://golang.org) implementation of [Jekyll](https://jekyllrb.com).

## Status
[![Build Status](https://travis-ci.org/osteele/gojekyll.svg?branch=master)](https://travis-ci.org/osteele/gojekyll)
[![Go Report Card](https://goreportcard.com/badge/github.com/osteele/gojekyll)](https://goreportcard.com/report/github.com/osteele/gojekyll)

This project is missing more functionality than it implements. It may accidentally work on tiny or simple sites.

It's currently ~50x faster than Jekyll using an embedded Liquid engine (that isn't very completely); and about 5x faster using an un-optimized connection to the [harttle/shopify-liquid](https://github.com/harttle/shopify-liquid) JavaScript library (documentation TBD) to render Liquid templates.

- [ ] Content
  - [x] Front Matter
  - [ ] Posts
    - [ ] Categories
    - [ ] Tags
    - [ ] Drafts
    - [ ] Future
    - [ ] Related
  - [ ] Creating pages
  - [x] Static Files
  - [x] Variables
  - [ ] Collections -- rendered, but not available as variables
  - [ ] Data Files
  - [ ] Assets
    - [ ] Coffeescript
    - [x] Sass
- [ ] Customization
  - [x] Templates
    - [ ] All Jekyll Liquid filters
    - [ ] All Jekyll Liquid tags
  - [x] Includes
  - [x] Permalinks
  - [ ] Pagination
  - [ ] Themes
  - [x] Layouts
- [x] Server
  - [x] Directory watch
  - [x] Live reload
- [ ] Other
  - [x] LINUX, macOS
  - [ ] Windows -- not tested

## Install

```bash
go install osteele/gojekyll/cmd/gojekyll
```

Sometimes this package benefits from my unmerged improvements to the **acstech/liquid** library. If you want to use [my fork](https://github.com/osteele/liquid) instead:

```bash
cd $(go env GOPATH)/src/github.com/acstech/liquid
git remote add osteele https://github.com/osteele/liquid.git
git pull -f osteele
```

(See articles by [Shlomi Noach](http://code.openark.org/blog/development/forking-golang-repositories-on-github-and-managing-the-import-path) and [Francesc Campoy](http://blog.campoy.cat/2014/03/github-and-go-forking-pull-requests-and.html) for how this works and why it is necessary.)

## Run

```bash
gojekyll --source test build
gojekyll --source test serve
gojekyll --source test render index.md # render a file to stdout
gojekyll --source test render /        # render a URL to stdout
gojekyll --source test data /          # print a path's template variables
```

`--source DIR` is optional.

`build` needn't be run before `server`. The latter serves from memory.

`server` only rebuilds individual changed pages, doesn't rebuild collections, and doesn't detect new pages.

`render` renders a single file, identified by permalink if it starts with `/`, and by pathname (relative to the source directory) if it doesn't.

For develpment, `./scripts/gojekyll` uses `go run` each time it's invoked.

## Credits

For rendering Liquid templates: the [acstech/liquid](https://github.com/acstech/liquid) fork of [karlseguin/liquid](https://github.com/karlseguin/liquid); or, [harttle/shopify-liquid](https://github.com/harttle/shopify-liquid/) via JSON-RPC.

The gopher image in the test directory is from [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Gophercolor.jpg). It is used under the [Creative Commons Attribution-Share Alike 3.0 Unported license](https://creativecommons.org/licenses/by-sa/3.0/deed.en).

## Related

[Hugo](https://gohugo.io) isn't Jekyll-compatible (-), but actually works (+++).

[Jekyll](https://jekyllrb.com), of course.

## License

MIT

## Alternate Naming Possibilities

* "Gekyll". (Hard or soft "g"? See [gif](https://en.wikipedia.org/wiki/GIF#Pronunciation_of_GIF).)
* "Gekko"
