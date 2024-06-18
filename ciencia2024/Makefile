.PHONY: main clean FORCE

main: poster.pdf

poster.pdf: FORCE
	latexmk poster.tex -pdflatex='lualatex -interaction nonstopmode' -pdf -pvc -view=pdf -f -jobname=./build/poster

clean:
	latexmk -pdf -C
