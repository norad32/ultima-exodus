# directories
DIRS = common cfg tlk binpatch
PACKAGE_DIRS = cfg binpatch

%: FORCE
	# operate on local, dos, winnt and linux targets
	for i in ${DIRS}; do \
		if [ -d "$$i" ]; then \
			TARGET=local make -C $$i $@ || exit 1; \
			TARGET=dos make -C $$i $@ || exit 1; \
			TARGET=winnt make -C $$i $@ || exit 1; \
			TARGET=linux make -C $$i $@ || exit 1; \
		fi \
	done || exit 1

package%: FORCE
	# package only dos/win/linux targets
	for i in ${PACKAGE_DIRS}; do \
		if [ -d "$$i" ]; then \
			TARGET=dos make -C $$i $@ || exit 1; \
			TARGET=winnt make -C $$i $@ || exit 1; \
			TARGET=linux make -C $$i $@ || exit 1; \
		fi \
	done || exit 1

gen_config%: FORCE
	# run local target to generate config file
	TARGET=local make -C cfg $@ || exit 1

Makefile: ;
FORCE: ;