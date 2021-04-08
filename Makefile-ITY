#AUTHOR: Eduard Frlicka
LOGIN=xfrlic00
ZIP_NAME=$(LOGIN)-fit
PDF_FILES=$(patsubst %.tex,%.pdf, $(wildcard *.tex))
ZIP_FILES=*.eps *.sty


.PRECIOUS: %.ps %.dvi

all: $(PDF_FILES)

%.pdf:%.ps Makefile
	@echo 'Compiling $<'
	ps2pdf $<

%.ps:%.dvi Makefile
	@echo 'Compiling $<'
	dvips -t a4 -o $@ $<

%.dvi:%.tex Makefile
	@echo 'Compiling $<'
	latex  $< 
	latex  $< 

recompile: clean all

zip: 
	zip $(ZIP_NAME) *.tex Makefile $(ZIP_FILES)

clean:
	rm -f *.pdf *.log *.out *.dvi *.aux *.ps
	rm -f $(ZIP_NAME).zip