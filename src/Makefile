ROOT=$(shell pwd)
PLATFORM=$(shell $(ROOT)/systype.sh)
include $(ROOT)/Make.defines.$(PLATFORM)


# director config
BIN=$(ROOT)/../workspace
ENGINE=$(ROOT)/engine
INJECTOR=$(ROOT)/injector
TOOLS=$(ROOT)/tools

DIRS=$(ENGINE) $(INJECTOR) $(TOOLS)


MAKE_DIR=make -C

SUBDIRS=$(DIRS)

.PHONY:all $(SUBDIRS)

all: $(SUBDIRS)

$(SUBDIRS):
		$(MAKE_DIR) $@

#all	:
#	for i in $(DIRS); do \
#		(cd $$i && echo "making $$i" && $(MAKE) ) || exit 1; \
#	done

clean:
	for i in $(DIRS); do \
		(cd $$i && echo "cleaning $$i" && $(MAKE) clean) || exit 1; \
	done

install :
#	for i in $(DIRS); do \
#		(cd $$i && echo "install $$i" && $(MAKE) install) || exit 1; \
#	done
	cp $(INJECTOR)/memInjector $(BIN)/memInjector
	cp $(ENGINE)/memoryEngine.ko $(BIN)/memoryEngine.ko

github:
	make clean
	cd $(ROOT)/.. 
	git add -A
	git commit -m $(GITHUB_COMMIT)
	git push origin master

insmod:
	cd $(ENGINE)&& make insmod

reinsmod:
	cd $(ENGINE)&& make reinsmod
