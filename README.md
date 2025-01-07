# matse_thesis
This is a LaTeX template that can be used to write any kind of term paper, bachelor thesis or similar papers.
The template is made for FH-Aachen theses, but can of course be adapted as required.

<!-- -------------------------------------------------------------------------------------------- -->

## License
This project uses the `unlicense` checkout the `LICENSE` file for more info, but it boils down to you being able
to do with this template whatever you want. There might be a copyright on the FH-Aachen document picture, but usage
of that seems to be allowed for a thesis officially done at the FH-Aachen (not legal advice).

<!-- -------------------------------------------------------------------------------------------- -->

## Setup

### Linux

```shell

sudo apt update

# Installs the full LaTeX version, this takes 6gb of space, there are also more minimal installs.
sudo apt install texlive-full  
```

### Windows
// TODO: Add windows setup instructions.

### Pycharm / Jetbrains
The [TeXiFy-IDEA](https://plugins.jetbrains.com/plugin/9473-texify-idea) plugin can be used to add LaTeX support to
your IDE.


The repository already contains three build configurations for PyCharm / Jetbrains IDEs.
- `thesis` <- this is the main build configuration, it will do all steps required.
- `pre_build_thesis` <- this is the first build step and is called by the `thesis` build config
- `thesis_bibliography` <- this builds the bibliography after the pre-build. Is called by `thesis` build config
### VsCode
The [LaTeX Workshop](https://marketplace.visualstudio.com/items?itemName=James-Yu.latex-workshop) extension can be used
to add LaTeX support to VsCode, there are some additional setup steps required, check out the linked extension page 
for more info

<!-- -------------------------------------------------------------------------------------------- -->

## Usage

### Main File
The main file is `src/thesis.tex`, it imports the required packages and does the general LaTeX setup. It also imports
the other files that are required. The only thing that needs to be done here is adding additional sections.

```latex
\chapter{Chapter One}  % <-- chapter name
\subfile{chapters/chapter_one} % <-- chapter path, the .tex ending is not required here
```

Remember to add the chapters in the correct order, you will find the chapters close to the end ~ line 82.

### Chapters
Chapters are placed in the `src/chapters`, each chapter has a separate file.

Some chapters have already been added beside the example chapter.

- A finished confidentiality clause which might be required if the thesis is written for/in a company. There
is no need to change this chapter, the missing info will be filled by the variables in the `src/settings.sty` file.

- A finished statutory declaration with signature lines for you, supervising professor and an additional supervisor,
which is for example applicable when writing it in a company. This section will always be required for
bachelor / master - theses or similar papers. Does not need to be edited, the missing info here will be filled by the
variables in the `src/settings.sty` file.

- Abstract with placeholder text. The abstract will always be required, keep it, 
but fill it with something that makes sense

- Table of contents. This one is automatically generated based on your chapters and subchapters, you will not find
a file for this in the `chapters` directory.

- Example chapter called `chapter_one`, you find some general LaTeX examples her like adding sections / subsections,
adding images or listing stuff.

- Conclusion and Outlook chapter, which you might want to split if they are big enough, but can also be kept as one
if it makes more sense structurally (this was the case for me). This is also just filled with placeholder text
and should be changed.

- References. These are generated as well, more about that in a later section. No file in `chapters` for this.

### Updating Variables
The `src/settings.sty` file contains a bunch of variables like author, supervisor and so on.
These are used within the title page, statutory declaration and other already prepared files.

### References
Add your references / sources to the `src/references.bib` file like this:

```bibtex
@article{1,  % <-- number of the source, required for citation and proper ordering
  author          = {Official Kubernetes Documentation},
  title           = {Service},
  url             = {https://kubernetes.io/docs/concepts/services-networking/service/},
  year            = {2020}
}
```
You can later use these references as citations in you text like this:
```latex
\cite{1}  % Number given is the source number given in the example above
```
The references will be used to automatically generate your references chapter.

### Images
Add your Images to `src/images`, you can include them like this:
```latex
\includegraphics[width=\linewidth]{picture_filename}  % Just the name no path, no file ending
\begin{minipage}{\linewidth}
\captionof{figure}{Caption for your Picture}
\end{minipage}
\\[0.5cm]
Some text that says something about something I guess
```
There is no need for a path to the image files, the `src/thesis.tex` file is set up in a way that images will
be taken from the `src/images` directory automatically.

<!-- -------------------------------------------------------------------------------------------- -->

## .gitignore
The `.gitignore` file is set up to ignore all files generated when building your LaTeX project, this includes the
pdf output. It is also configured to ignore the usual files for JetBrains IDEs like PyCharm and for VsCode.
