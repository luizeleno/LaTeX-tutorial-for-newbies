# Makefile para compilar automaticamente as aulas
# Deve haver apenas um arquivo .w2b no diretório!!!!!

AULA_W2B := $(wildcard *.w2b)
AULA_TEX := ${AULA_W2B:.w2b=.tex}
AULA_AUX := ${AULA_W2B:.w2b=.aux}
AULA_OUT := ${AULA_W2B:.w2b=.out}
AULA_LOG := ${AULA_W2B:.w2b=.log}
AULA_TOC := ${AULA_W2B:.w2b=.toc}
AULA_SNM := ${AULA_W2B:.w2b=.snm}
AULA_NAV := ${AULA_W2B:.w2b=.nav}
AULA_FLS := ${AULA_W2B:.w2b=.fls}
AULA_FDB := ${AULA_W2B:.w2b=.fdb_latexmk}
AULA_PDF := ${AULA_W2B:.w2b=.pdf}

GPL_SRC := $(wildcard *.gpl)
GPL_PLT := ${GPL_SRC:.gpl=.plt}
GPL_TEX := ${GPL_SRC:.gpl=.tex}

GPT_SRC := $(wildcard *.gnuplot)
GPT_TAB := ${GPT_SRC:.gnuplot=.table}

default: $(AULA_PDF)

$(AULA_TEX): $(AULA_W2B)
	wiki2beamer $? -o $@

$(GPL_TEX): $(GPL_SRC)
	process_gpl $?

gnuplot: $(GPT_SRC)
	gnuplot $?

reprocess:
	latexmk -g -pdf $(AULA_TEX)
	
$(AULA_PDF): $(GPL_TEX) $(GPT_TAB) $(AULA_TEX)
	latexmk -pdf $(AULA_TEX)

clean:
	rm -f $(AULA_TEX) $(AULA_AUX) $(AULA_OUT) $(AULA_LOG) $(AULA_TOC) $(AULA_SNM) $(AULA_NAV) $(AULA_FLS) $(AULA_FDB) $(GPL_PLT) $(GPL_TEX) $(GPT_SRC) $(GPT_TAB)