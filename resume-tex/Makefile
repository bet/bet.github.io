resume.dvi: resume.tex
	latex resume.tex

resume.ps: resume.dvi
	dvips resume.dvi

	pdftops resume.pdf

resume.pdf: resume.tex
	pdflatex resume.tex

clean:
	rm resume.aux resume.log
