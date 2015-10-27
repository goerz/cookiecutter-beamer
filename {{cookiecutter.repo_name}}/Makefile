PDFLATEXOPTS = -file-line-error -interaction=nonstopmode -halt-on-error -synctex=1
TEXFILE_ROOT = {{cookiecutter.texfile_root}}

all: $(TEXFILE_ROOT).pdf

$(TEXFILE_ROOT).pdf: $(TEXFILE_ROOT).tex $(wildcard images/*.py images/*.tex images/*.pdf images/*.png images/*.jpg)
	$(MAKE) -C images all
	@latexmk -pdf -pdflatex="pdflatex $(PDFLATEXOPTS)" -silent $(TEXFILE_ROOT).tex

pdflatex:
	@echo "Compiling Main File ..."
	pdflatex $(PDFLATEXOPTS) $(TEXFILE_ROOT)
	pdflatex $(PDFLATEXOPTS) $(TEXFILE_ROOT)
	@echo "Done"

update:
	pdflatex $(PDFLATEXOPTS) $(TEXFILE_ROOT)

clean:
	@echo "Cleaning up files from LaTeX compilation ..."
	$(MAKE) -C images clean
	@rm -f *.aux
	@rm -f *.log
	@rm -f *.toc
	@rm -f *.bbl
	@rm -f *.blg
	@rm -f *.out
	@rm -f *.bak
	@rm -f *.ilg
	@rm -f *.snm
	@rm -f *.nav
	@rm -f *.fls
	@rm -f *.table
	@rm -f *.gnuplot
	@rm -f *.fdb_latexmk
	@rm -f *.synctex.gz
	@echo "Done"

distclean: clean
	$(MAKE) -C images distclean
	@rm -f $(TEXFILE_ROOT).pdf

.PHONY: all pdflatex update clean distclean
