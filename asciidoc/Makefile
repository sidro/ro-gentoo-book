# Makefile pentru generarea manualului Gentoo in format PDF, HTML5 și epub
#
# Thanks to Oliver Burtchen (oliver-burtchen) for the options for a2x
# to correctly handle chars with diacritical marks
# https://bugs.launchpad.net/ubuntu/+source/asciidoc/+bug/1073247
#
# Versiunile programelor folosite:
# asciidoc 8.6.8
# Asciidoctor 0.1.3
# LaTeX cu pachetul unicode
# dblatex-0.3
# DocBook xsl-stylesheets-1.78.1

SRC_FILE=gentoo-robook
CSS_FILE=custom.css

all: clean html pdf epub

html:
	@echo -n "Generez HTML..."
	@asciidoctor -b html5 -a stylesheet=${CSS_FILE} ${SRC_FILE}.adoc
	@echo "gata"

pdf:
	@echo -n "Generez PDF..."
	@asciidoctor -b docbook ${SRC_FILE}.adoc
	@a2x -a encoding=utf-8 -a lang=ro --dblatex-opts='-P latex.encoding=utf8 -P latex.unicode.use=1 -P latex.output.revhistory=0' -f pdf --stylesheet "docbook-xsl.css $CSS_FILE" ${SRC_FILE}.xml
	@echo "gata"

epub:
	@echo -n "Generez epub..."
	@a2x -f epub -d book -a docinfo ${SRC_FILE}.adoc
	@echo "gata"

clean:
	@rm -f *.pdf *.xml *.html *.epub
