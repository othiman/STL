LATEX = latex
BIBTEX = bibtex
PDFLATEX = pdflatex
GS = /usr/bin/gs
#DVI2PS = /usr/bin/dvips
DVI2PS = dvips
PS2PDF = ps2pdf

.SUFFIXES: .dvi .tex .ps .pdf

TRGSRC = stl2018man.tex
DVI = $(subst .tex,.dvi,$(TRGSRC))
PS  = $(subst .dvi,.ps,$(DVI))
PDF  = $(subst .ps,.pdf,$(PS))
#DOCS = ${DVI} ${PS} ${PDF}
DOCS = ${PDF}
PARTS = $(TRGSRC) intro.tex g711.tex g711iplc.tex g726.tex g727.tex g728.tex g722.tex rpe.tex rate.tex eid.tex mnru.tex sv56.tex reverb.tex truncate.tex freqresp.tex stereoop.tex basop.tex utl.tex

.tex.dvi: .bib
	$(LATEX) $<; $(BIBTEX) $*; $(LATEX) $<; $(LATEX) $<

.dvi.ps:
	$(DVI2PS) -D600 -Z -o $@ $<
	$(DVI2PS) -D600 -tletter -Z -o $@ $<

#.ps.pdf:
#	$(GS) -dBATCH -dNOPAUSE -sDEVICE=pdfwrite -sOutputFile=$@ $<
#.ps.pdf:
#	$(PS2PDF) -sPAPERSIZE=a4 -dSAFER -dBATCH -dNOPAUSE -sDEVICE=pdfwrite -sOutputFile=$@ -c save pop -f $<

.tex.pdf:
	$(PDFLATEX) $<; $(BIBTEX) $*; $(PDFLATEX) $<; $(PDFLATEX) $<

all: ${DOCS}

clean: 
	\rm -f ${DOCS} *.aux *.log *.out *.toc

$(DVI): $(PARTS)
$(PDF): $(PARTS)

