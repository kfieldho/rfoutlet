#PREFIX is environment variable, but if it is not set, then set default value
ifeq ($(PREFIX),)
    PREFIX := /usr/local
endif

all: send codesend RFSniffer

send: RCSwitch.o send.o
	$(CXX) $(CXXFLAGS) $(LDFLAGS) $+ -o $@ -lwiringPi
	
codesend: RCSwitch.o codesend.o
	$(CXX) $(CXXFLAGS) $(LDFLAGS) $+ -o $@ -lwiringPi
	
RFSniffer: RCSwitch.o RFSniffer.o
	$(CXX) $(CXXFLAGS) $(LDFLAGS) $+ -o $@ -lwiringPi
	
install: codesend RFSniffer
	install -d $(DESTDIR)$(PREFIX)/bin/
	install -m 4755 codesend $(DESTDIR)$(PREFIX)/bin/
	install -m 4755 RFSniffer $(DESTDIR)$(PREFIX)/bin/

clean:
	$(RM) *.o send codesend servo RFSniffer
