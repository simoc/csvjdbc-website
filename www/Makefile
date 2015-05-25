# Generates HTML pages from Markdown source files using discount
# program ( http://www.pell.portland.or.us/~orc/Code/discount/ )
#
HTML = index.html doc.html develop.html

%.html: %.md
	cat header.html > $@
	markdown $< >> $@
	cat footer.html >> $@

all: $(HTML)

clean:
	rm $(HTML)

