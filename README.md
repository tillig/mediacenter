# My Media Center

This repo houses documentation, diagrams, and info on my media center setup. I had been blogging this information, but given the rate with which it changes, I switched to [a repository rendered with ReadTheDocs](http://illigmediacenter.readthedocs.io/) so I could more easily keep things up to date.

**[Read the docs!](http://illigmediacenter.readthedocs.io/)**

## Build

The documentation is built using Sphinx and ReStructuredText.

```powershell
cd docs
make html
```

Diagrams are built using [my PlantUML watcher](https://github.com/tillig/plantuml-in-azdo-wiki) via Node.js.

```powershell
npm install
npm run watch
```

## References

* [ReStructured Text Quickstart](http://docutils.sourceforge.net/docs/user/rst/quickstart.html)
* [ReStructured Text Quick Reference](http://docutils.sourceforge.net/docs/user/rst/quickref.html)
* [ReStructured Text Cheat Sheet](http://docutils.sourceforge.net/docs/user/rst/cheatsheet.txt)
* [Sphinx ReStructured Text](http://sphinx-doc.org/rest.html)
* [Sphinx Markup](http://sphinx-doc.org/markup/index.html)
