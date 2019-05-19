resume.pdf: resume.ps
	ps2pdf resume.ps

resume.ps: resume.dvi
	dvips resume.dvi

resume.dvi: resume.tex
	latex resume.tex

clean:
	rm  -f resume.aux resume.log resume.dvi texput.log
