ALL = placeholder.pdf
all: $(ALL)

%.pdf: %.tex
	pdflatex $<

%.pdf: %.py
	python $<

clean:
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
	@rm -f *.pgftex *.pgf
	@rm -f *.fdb_latexmk
	@rm -f *.synctex.gz
	@rm -f doc_data.txt

distclean: clean
	@rm -f $(ALL)

.PHONY: all clean distclean
