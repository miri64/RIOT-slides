FILENAME        := 2016-riot-panorama
PANDOC          := pandoc
PANDOC_FLAGS    := -t beamer -S -s --latex-engine=xelatex --filter="./pandoc-svg"
PDF             := $(FILENAME).pdf
SRC             := $(FILENAME).md
DEPS            := beamerthemeRIOT.sty header-config.tex graphics/Logo.pdf

.PHONY : all clean

all : $(PDF)

$(PDF): $(SRC) $(DEPS)
	@pandoc $(foreach H,$(filter header-%.tex,$^),-H $(H))\
	        $(foreach A,$(filter before-%.tex,$^),-B $(B))\
	        $(foreach A,$(filter after-%.tex,$^),-A $(A))\
	        -o $@ $(PANDOC_FLAGS) $<

graphics/%.pdf: graphics/%.svg
	@inkscape --export-pdf=$@ $<

clean:
	@rm -f $(PDF)
	@rm -f $(patsubst %.psvg,%,$(wildcard graphics/*.psvg))
	@rm -f $(wildcard graphics/*.psvg)
	@rm -f graphics/Logo.pdf
