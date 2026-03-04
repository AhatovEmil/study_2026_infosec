### Cross references
## Use pandoc-xnos (https://github.com/tomduck/pandoc-xnos)
## Local pandoc-xnos
# FILTERS += --filter pandoc/filters/pandoc_fignos.py --filter pandoc/filters/pandoc_eqnos.py --filter pandoc/filters/pandoc_tablenos.py --filter pandoc/filters/pandoc_secnos.py
## System-wide pandoc-xnos
# FILTERS += --filter pandoc-fignos --filter pandoc-eqnos --filter pandoc-tablenos --filter pandoc-secnos
## Use pandoc-crossref (https://github.com/lierdakil/pandoc-crossref)
FILTERS += --filter /usr/local/bin/pandoc-crossref
###
PDF_ENGINE += --pdf-engine=xelatex --pdf-engine-opt=--shell-escape
OPTIONS += --number-sections
BIB_OPTIONS = --citeproc
# Добавляем параметры для шрифтов
FORMAT_OPTIONS = -V mainfont="Liberation Serif" -V sansfont="Liberation Sans" -V monofont="Liberation Mono" -V geometry:margin=1in

# Найти все .md файлы (кроме README.md и шаблонов)
MD_FILES = $(wildcard *.md)
MD_FILES := $(filter-out README.md template.md, $(MD_FILES))

# Создать имена для .docx и .pdf
DOCX_FILES = $(MD_FILES:.md=.docx)
PDF_FILES = $(MD_FILES:.md=.pdf)

# Все цели
FILES = $(DOCX_FILES) $(PDF_FILES)

%.docx: %.md
	-pandoc "$<" $(FILTERS) $(OPTIONS) $(BIB_OPTIONS) -o "$@"

%.pdf: %.md
	-pandoc "$<" $(FILTERS) $(PDF_ENGINE) $(PDF_OPTIONS) $(BIB_OPTIONS) $(FORMAT_OPTIONS) $(OPTIONS) -o "$@"

all: $(FILES)

clean:
	-rm -f $(FILES) *~

cleanall: clean
