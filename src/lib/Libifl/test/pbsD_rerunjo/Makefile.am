PROG_ROOT = ../..

AM_CFLAGS = -g -DTEST_FUNCTION -I${PROG_ROOT}/ -I${PROG_ROOT}/${PBS_MACH} --coverage

lib_LTLIBRARIES = libpbsD_rerunjo.la

AM_LDFLAGS = @CHECK_LIBS@ ${lib_LTLIBRARIES}

check_PROGRAMS = test_pbsD_rerunjo

libpbsD_rerunjo_la_SOURCES = scaffolding.c ${PROG_ROOT}/pbsD_rerunjo.c
libpbsD_rerunjo_la_LDFLAGS = @CHECK_LIBS@ -shared -lgcov

test_pbsD_rerunjo_SOURCES = test_pbsD_rerunjo.c

check_SCRIPTS = coverage_run.sh

TESTS = ${check_PROGRAMS} coverage_run.sh

coverage_run.sh:
	echo 'cp -p .libs/pbsD_rerunjo.gc* . >/dev/null 2>&1' > $@
	echo 'RESULTS=($$(gcov pbsD_rerunjo.gcda))' >> $@
	echo 'PARSED_RESULT="TOTALCOV -- $${RESULTS[1]}: Lines($${RESULTS[5]})- $${RESULTS[3]}"' >> $@
	echo 'echo -e "\033[40m\033[1;33m$$PARSED_RESULT\033[0m"' >> $@
	chmod +x $@

CLEANFILES = coverage_run.sh *.gcno *.gcda *.gcov core *.lo
