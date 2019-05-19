default: resume.pdf

resume-iso8859-1.txt: resume.txt
	iconv -f UTF-8 -t ISO-8859-1 resume.txt >  resume-iso8859-1.txt

resume.ps: resume-iso8859-1.txt
	a2ps -o resume.ps --portrait  --columns=1 --borders=no --lines-per-page=66 --chars-per-line=80 --no-header resume-iso8859-1.txt

resume.pdf: resume.ps
	epstopdf resume.ps
