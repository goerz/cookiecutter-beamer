PDFLATEXOPTS = -file-line-error -interaction=nonstopmode -halt-on-error -synctex=1

all: {{ cookiecutter.prefix }}.pdf

{{ cookiecutter.prefix }}.pdf: {{ cookiecutter.prefix }}.tex $(wildcard images/*.py images/*.tex images/*.pdf images/*.png images/*.jpg)
	$(MAKE) -C images all
	@latexmk -pdf -pdflatex="pdflatex $(PDFLATEXOPTS)" -silent {{ cookiecutter.prefix }}.tex

pdflatex:
	@echo "Compiling Main File ..."
	pdflatex $(PDFLATEXOPTS) {{ cookiecutter.prefix }}
	pdflatex $(PDFLATEXOPTS) {{ cookiecutter.prefix }}
	@echo "Done"

update:
	pdflatex $(PDFLATEXOPTS) {{ cookiecutter.prefix }}

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
	@rm -f {{ cookiecutter.prefix }}.pdf

.PHONY: all pdflatex update clean distclean
