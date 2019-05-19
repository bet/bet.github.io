default: resume.pdf resume.ps

resume-big.pdf: resume.tex
	latexmk -pdf resume.tex
	mv resume.pdf resume-big.pdf

resume.pdf: resume-big.pdf
	gs -dBATCH -dNOPAUSE -q -sDEVICE=pdfwrite -sOutputFile=resume.pdf resume-big.pdf
	
resume.ps: resume.dvi
	dvips resume.dvi

resume.dvi: resume.tex
	latex resume.tex

clean:
	rm  -f resume.aux resume.log resume.dvi texput.log resume-big.pdf resume.fdb_latexmk resume.fls
