# cookiecutter-beamer #

A [cookiecutter][] template for LaTeX ([Beamer][]) slides

[cookiecutter]: https://github.com/audreyr/cookiecutter
[Beamer]: https://bitbucket.org/rivanvx/beamer/wiki/Home

## Usage ##

First, make sure to have `cookiecutter` installed:

    pip install cookiecutter

Then, create a new project with

    git clone https://github.com/goerz/cookiecutter-beamer.git
    cookiecutter cookiecutter-beamer/

or

    cookiecutter gh:goerz/cookiecutter-beamer

## Variables ##


* `author_name`: The author's full name, will show up on the title slide, in the footer, and in the PDF metadata
* `author_affiliation`: The author's affiliation, will show up on the title slide and in the footer
* `location`: Location where the talk is presented, will show up on the title slide
* `location_word`: single-word shorthand for the location, to be used in the default `repo_name`
* `year`: Year in which talk is presented (integer)
* `month`: Month in which talk is presented (integer)
* `day`: Day on which talk is presented (integer)
* `date`: Date as it appears on the title slide
* `texfile_root`: The name of the main tex file, without extension
* `title`: The full title of the Talk, as it appears on the title slide
* `title_short`: A shortened version of the title, as it appears in the footer
* `title_word`: A single-word shorthand for the title, to be used in the default `repo_name`
* `subject`: Subject of the talk, will show up in the PDF metadata
* `repo_name`: Name of folder in which to set up the talk. By default, set up as `{year}-{month}-{day}_{location_word}_{title_word}`


## Structure and Features ##

### Makefile generation of slides and figures ###

The generated folder will have the following structure:

    .
    ├── Makefile            # Main makefile
    ├── images              # Folder for included image files
    │   ├── Makefile        # Makefile for generating images from tikz or python
    │   ├── colors.tex      # Definition of nice color palette
    │   ├── matplotlibrc    # Settings for matplotlib
    │   └── placeholder.tex # An example tikz image
    ├── mymacros.sty        # Definition of macros and loading packages
    ├── slides.tex          # Main tex files (assuming texfile_root = slides)
    └── theme_settings.tex  # theme-related settings, included from slides.tex

Compilation of the talk and the figures is set up via a Makefile. Simply running `make` should compile the talk into a pdf file. In addition, images may be generated automatically: The `images` folder may contain not just jpg, pdf, and png files for direct inclusion, but also scripts or (TikZ) tex files that can be converted to images. This conversion happens through the instructions in `images/Makefile`. The file `images/placeholder.tex` is an example for a tikz-generated figure.

### `texpos` ###

In `theme_settings.tex`, the [`texpos` package][textpos] is loaded and initialize in order to facilitate absolute positioning on a slide. On a coordinate system with its origin in the top left corner, a block of width 3 cm may be placed with its top left corner at the coordinates (4 cm, 2 cm) with the code

    \begin{textblock}{3}(4,2)
      \dots
    \end{textblock}

The total canvas is 12.8 cm by 9.6 cm.

[textpos]: https://www.ctan.org/pkg/textpos)
