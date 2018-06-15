SOURCE=s1kd-newddn.c
OUTPUT=s1kd-newddn

CFLAGS=-Wall -Werror -pedantic-errors -O3 -I ../common `pkg-config --cflags libxml-2.0 libxslt`
LDFLAGS=`pkg-config --libs libxml-2.0 libxslt`

PREFIX=/usr/local
INSTALL_PREFIX=$(PREFIX)/bin

all: $(OUTPUT)
	$(MAKE) -C doc

templates.h: templates/ddn.xml ../common/42to*.xsl
	xxd -i templates/ddn.xml > templates.h
	xxd -i ../common/42to20.xsl >> templates.h
	xxd -i ../common/42to21.xsl >> templates.h
	xxd -i ../common/42to22.xsl >> templates.h
	xxd -i ../common/42to23.xsl >> templates.h
	xxd -i ../common/42to30.xsl >> templates.h
	xxd -i ../common/42to40.xsl >> templates.h
	xxd -i ../common/42to41.xsl >> templates.h

$(OUTPUT): $(SOURCE) templates.h
	$(CC) $(CFLAGS) -o $(OUTPUT) $(SOURCE) $(LDFLAGS)

clean:
	rm -f $(OUTPUT) templates.h
	$(MAKE) -C doc clean

install:
	cp $(OUTPUT) $(INSTALL_PREFIX)/
	$(MAKE) -C doc install