### Commands
To run a local version of the site:
```
hugo server -v -D --disableFastRender --minify
```
We use minify locally to make local builds more similar to production.

### Hugo tricks
`{{- "" -}}` removes whitespace caused by newlines in html.
