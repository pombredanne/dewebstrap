# Copyright (c) Paul Tagliamonte <paultag@debian.org>, 2012 under the terms
# and conditions of the Expat license, a copy of which should be given to you
# with the source of this application.

#CSSC ?= recess
#CSFLAGS ?= --compile --compress

CSSC ?= lessc
CSFLAGS ?= -x

DIST ?= dist

all: lecture

lecture:
	@echo "make [static|flask|clean]"

clean:
	rm -rf $(DIST)

build: clean
	mkdir $(DIST) -p
	mkdir $(DIST)/static/css -p
	mkdir $(DIST)/static/imgs -p
	$(CSSC) $(CSFLAGS) less/dewebstrap.less > $(DIST)/static/css/dewebstrap.css
	cp templates $(DIST) -r
	cp imgs/* $(DIST)/static/imgs
	/usr/lib/dewebstrap/getcopyright > $(DIST)/templates/footer.html

static: build
	cd $(DIST) && /usr/lib/dewebstrap/static-build index.html > index.html
	# cd $(DIST) && /usr/lib/dewebstrap/static-build about.html > about.html
	rm -rf $(DIST)/templates

flask: build
	cp code/app.py $(DIST)
