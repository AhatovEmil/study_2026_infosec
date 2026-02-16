# Найти все .md файлы (кроме специальных)
MD_FILES = $(wildcard *.md)
MD_FILES := $(filter-out README.md template.md, $(MD_FILES))

# Создать имена для .pdf и .html
PDF_FILES = $(MD_FILES:.md=.pdf)
HTML_FILES = $(MD_FILES:.md=.html)

# Все цели
FILES = $(PDF_FILES) $(HTML_FILES)

# Фильтры и опции
FILTERS = --citeproc
# FILTERS += -F pandoc-crossref

PDF_ENGINE = --pdf-engine=xelatex
PDF_OPTIONS = 
PDF_FORMAT_OPTIONS = -t beamer --slide-level=2
FORMAT_OPTIONS = -V mainfont="Liberation Serif" -V sansfont="Liberation Sans" -V monofont="Liberation Mono" -V geometry:margin=1in

REVEALJS_THEME = beige

# Правило для PDF (Beamer презентация)
%.pdf: %.md
	pandoc "$<" $(FILTERS) $(PDF_ENGINE) $(PDF_OPTIONS) $(PDF_FORMAT_OPTIONS) $(FORMAT_OPTIONS) -o "$@"

# Правило для HTML (Reveal.js презентация)
%.html: %.md
	pandoc "$<" --embed-resources --standalone -t revealjs -V theme=$(REVEALJS_THEME) -o "$@"

# Собрать всё
all: $(FILES)

# Собрать только PDF
pdf: $(PDF_FILES)

# Собрать только HTML
html: $(HTML_FILES)

# Очистка
clean:
	-rm -f $(FILES) *~

cleanall: clean
