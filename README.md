# University of Vermont (UVM) Thesis Template

A (relatively) minimal template for typesetting master's theses and doctoral dissertations. **Note:** UVM's Graduate College is aware of this template, but does not maintain it. It is your responsibility to ensure your thesis/dissertation meets the Graduate College's [requirements](https://www.uvm.edu/graduate/academic-resources).

With that said, feature suggestions, bug fixes, and issue discussions are always welcome.

This readme presumes you're familiar with LaTeX. If not, check out [this guide](https://www.overleaf.com/learn/latex/Learn_LaTeX_in_30_minutes). 

## Getting started

Fork or clone this template

```
git clone git@github.com:ajbarrows/uvm-thesis-template.git
cd uvm-thesis-template
```

**It is strongly recommended that you create your own version-controlled template.**

Rename the repository first, if you like.

```
rm .git # remove existing Git folder
git init . # initialize new repository
git add . 
git commit -m "initial commit"
```

Create a new repository on GitHub.

```
git remote add origin git@github.com:YOUR_GITHUB_USER_NAME/{repository name}.git
git push
```

Alternatively, this template should work with Overleaf, but that hasn't been tested.


## Edit `titlepage.tex`

```
\title{Title}
\author{Author}
\defensedate{}
\dissertation                     %% or \thesis
\doctorphilosophy               %% or \masterarts \masterscience
\csds                 %% see note
\gradyear{2026}        %%The year in which the degree will be conferred
\maygrad                           %% \maygrad, \auggrad, \octgrad, or \marchgrad
\advisor{Advisor}
\readerone{ReaderOne}
\chair{Chair}
\readertwo{ReaderTwo}
\dean{Dean}
```

Note: degree program options are found in `uvm-thesis-style.sty`


## Edit content

All thesis/dissertation content goes in `./content`. The template, by default, includes:

```
abstract.tex
acknowledgements.tex
appendix.tex
chapter1.tex
chapter2.tex
chapter3.tex
conclusion.tex
dedication.tex
introduction.tex
```

These are all referenced in `main.tex`. If you add additional `.tex` files, ensure you also add references to them in `main.tex` as

```
\include{content/{my-filename}.tex}
```

## Add references

By default, the template reads [BibTeX](https://www.overleaf.com/learn/latex/Bibliography_management_with_bibtex#Enter_\(\mathrm{Bib\TeX}\)) entries from `bibliography.bib`, which is to say that entries in `bibliography.bib` are accessbible from any files in `./content` using `\cite{}` or similar commands. 

Citation managers like [Zotero](https://www.zotero.org) and the [Better BibTeX Extension](https://retorque.re/zotero-better-bibtex/) are highly recommended. This extension exports all of your references in BibTeX format to a file of your choosing. You can use a [symbolic link](https://en.wikipedia.org/wiki/Symbolic_link) to replace `bibliography.bib` with your Zotero exports without having to manually copy and paste BibTeX references:

```
rm bibliography.bib # first delete this template's bibliography file
ln -s path/to/bibtex-export.bib bibliography.bib
```

## Compile the document

This template is setup to use `pdflatex`. Render the project simply by running

```
pdflatex main.tex
```

### VSCode Integration

You can edit `.tex` files however you like. One popular way is to use an integrated development environment (IDE) like [VSCode](https://code.visualstudio.com). This template includes a VSCode settings file (`./vscode/settings.json`) which presumes you've installed the handy [LaTeX-Workshop Extension](https://github.com/James-Yu/LaTeX-Workshop). Importantly, the default behavior of this extension is to compile a PDF of your project when you save a .tex file. 