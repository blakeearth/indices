# indices
`indices` is a simple, personal static site generator written in Go. I made it for two reasons:
* I couldn't find any other static-site generators that met my desire for simplicity. With `indices`, I can just drag my Markdown source to the binary and commit, and pages are simple and self-index. (For an example of a site made with `indices`, see [my website](https://blake.earth)).
* I wanted a small project to help me learn Go.

## Usage
> `indices` has no customizability. If you want to make changes to its appearance, for example, you'll need to change the source and build a binary yourself, but this should not be a difficult process.

* `indices` is built like a file system. Imagine that you're writing a site like you would with HTML, but write it with Markdown instead. Other than that, it just adds a self-indexing system.
  * For example, in the root directory of your website, you might have an `index.md` file as a homepage and an `about.md` file for personal details. When you run the binary on your website source, `index.md` will compile to `index.html` and include a navigation section that links to the personal details page (and any other pages in the directory). `about.md` will compile to `about/index.html` and include a note at the bottom of the page that links to the `index.html` of the directory.
  * For a more detailed example, see [my website source](https://github.com/blakeearth/blakeearth.github.io/tree/gh-pages).
* The title of each page is the first line of the `.md` with anything except `a-z`, `A-Z`, ` `, `.` and `-` removed.
* Use `\` at the end of Markdown lines to end the paragraph/force a line break.
* With a binary, just run `indices <website source directory>`. Any files not ending in `.md` will be copied to the final static site.

## Build
1. Make sure you have [Go](https://golang.org/) installed.
2. Then get `blackfriday`, the Markdown processor with `go get gopkg.in/russross/blackfriday.v2`.
3. Then just run `go build` to build a binary.

## Notes
* `indices` uses `blackfriday` and does NOT sanitize input! It will copy over HTML tags, scripts, etc.
* The HTML used to generate the static sites is in `indices.go`. If you want to change the appearance or something else about the sites `indices` generates, start there!
* The code for this repository is sloppy! It's the first program I made with Go (I wanted to learn it), and it could definitely stand some refactoring.
