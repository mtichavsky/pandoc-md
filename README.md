## About

This script converts .md files to .html files through utility called *[pandoc](https://pandoc.org/)* **(which has to be installed on the machine).** It lets you specify an array of directories or files in arguments, so you don't have to convert them manually one by one. Script also checks for existing html files and if they are up to date (based on modification date difference between .md and .html) they don't get recompiled to prevent unnecessary writes.

Also contains a bonus: there's a section on converting markdown to PDF (not part of the script), which I use extensively for school projects.

## Usage:

```bash
    pandoc-md [options] [paths]
```

- `-h` show help

SWITCH OPTIONS (one of these is mandatory)

- `-d` convert specified directories
- `-i` convert specified files
- `-t` convert this (local) folder

OPTIONAL OPTIONS

- `-s` choose stylesheet to be linked to the resulting `.html` files
- `-f` force option - skips the check if files are up to date
- `-r` recursively convert folders (convert files in the working directory and in all containing directories)

If you keep using the same style file for the most of your html files, you can set an environment variable `PANDOC_MD_STYLE` to contain a path to that script. The path in `PANDOC_MD_STYLE` will be used by default (that is when you don't use `-s` option).


## LaTeX

Unrelated to this script, more like a note to self, this is how I convert .md files to PDF:

```sh
# pandoc and LaTeX needs to be installed 
pandoc README.md --pdf-engine=xelatex --metadata-file pandoc-metadata.yml \
  -s -o readme.pdf
```

Note that it references one more file, `pandoc-metadata.yml`, which I created specificaly for styling my document.
Example contents of this file:

```yml
--
# https://pandoc.org/MANUAL.html#variables-for-latex
# A list of LaTeX packages I install on Fedora:
#   - texlive-latex
#   - texlive-babel-czech
#   - texlive-collection-latexrecommended
#   - texlive-adjustbox
author:
- Milan Tichavský
geometry:
  - top=30mm
  - left=20mm
  - right=20mm
  - bottom=30mm
mainfont: "DejaVu Sans"
colorlinks: true
linkcolor: blue
urlcolor: blue
filecolor: magenta
citecolor: green
links-as-notes: true
urlstyle: tt
```

Of course, you can ignore this option if you're happy with the default style.

