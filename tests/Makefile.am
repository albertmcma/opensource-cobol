#
# Makefile opencobol/tests
# Process this file with automake to produce Makefile.in
#
# Copyright (C) 2003,2004,2005,2006,2007 Keisuke Nishida
# Copyright (C) 2008-2011 Roger While
#
# This file is part of OpenCOBOL.
#
# The OpenCOBOL compiler is free software: you can redistribute it
# and/or modify it under the terms of the GNU General Public License
# as published by the Free Software Foundation, either version 2 of the
# License, or (at your option) any later version.
#
# OpenCOBOL is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with OpenCOBOL.  If not, see <http://www.gnu.org/licenses/>.

SUBDIRS = cobol85

if I18N_UTF8
TESTS = $(srcdir)/syntax \
	$(srcdir)/run \
	$(srcdir)/run-O \
	$(srcdir)/data-rep \
	$(srcdir)/data-rep-O \
	$(srcdir)/i18n_utf8 \
	$(srcdir)/jp-compat
else
TESTS = $(srcdir)/syntax \
	$(srcdir)/run \
	$(srcdir)/run-O \
	$(srcdir)/data-rep \
	$(srcdir)/data-rep-O \
	$(srcdir)/i18n_sjis \
	$(srcdir)/jp-compat
endif

syntax_DEPENDENCIES = \
	syntax.at \
	syntax.src/copy.at \
	syntax.src/unmatured-copy.at \
	syntax.src/definition.at \
	syntax.src/expression.at \
	syntax.src/multiply.at \
	syntax.src/redefines.at \
	syntax.src/value.at \
	syntax.src/move.at \
	syntax.src/set.at \
	syntax.src/occurs.at \
	syntax.src/subscripts.at \
	syntax.src/free-1col-aster.at \
	syntax.src/indicator.at \
	syntax.src/assign-external.at \
	syntax.src/error-recovery.at \
	syntax.src/data-records.at

run_DEPENDENCIES = \
	run.at \
	run.src/fundamental.at \
	run.src/accept.at \
	run.src/initialize.at \
	run.src/misc.at \
	run.src/ref-mod.at \
	run.src/subscripts.at \
	run.src/extensions.at \
	run.src/return-code.at \
	run.src/functions.at

data_rep_DEPENDENCIES = \
	data-rep.at \
	data-rep.src/binary.at \
	data-rep.src/display.at \
	data-rep.src/packed.at \
	data-rep.src/pointer.at \
	data-rep.src/numeric-dump.cob \
	data-rep.src/numeric-display.cob

i18n_utf8_DEPENDENCIES = \
	i18n_utf8.at \
	i18n_utf8.src/user-defined-word.at \
	i18n_utf8.src/pic-x.at \
	i18n_utf8.src/pic-n.at \
	i18n_utf8.src/pic-bn.at \
	i18n_utf8.src/program-id.at \
	i18n_utf8.src/error-print.at \
	i18n_utf8.src/stored-char-length.at \
	i18n_utf8.src/warn-mixture-byte.at \
	i18n_utf8.src/limits.at \
	i18n_utf8.src/national.at \
	i18n_utf8.src/mb-space.at

i18n_sjis_DEPENDENCIES = \
	i18n_sjis.at \
	i18n_sjis.src/user-defined-word.at \
	i18n_sjis.src/pic-x.at \
	i18n_sjis.src/pic-n.at \
	i18n_sjis.src/program-id.at \
	i18n_sjis.src/error-print.at \
	i18n_sjis.src/limits.at \
	i18n_sjis.src/national.at \
	i18n_sjis.src/mb-space.at

jp_compat_DEPENDENCIES = \
	jp-compat.at \
	jp-compat.src/split-keys.at \
	jp-compat.src/compat-check.at \
	jp-compat.src/copy-leading-trailing.at \
	jp-compat.src/end-program-wrong.at \
	jp-compat.src/evaluate-also-missing.at \
	jp-compat.src/empty-imperative.at \
	jp-compat.src/spl-registers.at \
	jp-compat.src/special-names.at \
	jp-compat.src/intr-funcs.at \
	jp-compat.src/file-control.at \
	jp-compat.src/file-userfh.at \
	jp-compat.src/copy-joining.at \
	jp-compat.src/assign-devicename.at \
	jp-compat.src/job-date.at \
	jp-compat.src/nibble-c-for-unsigned.at \
	jp-compat.src/upsi-x.at \
	jp-compat.src/cob68-copy.at \
	jp-compat.src/switch-no-mnemonic.at \
	jp-compat.src/data-desc-no-dot.at \
	jp-compat.src/sort-key-is.at \
	jp-compat.src/search-key-in-rhs.at \
	jp-compat.src/verbose-runtime.at \
	jp-compat.src/occurs-param-order.at \
	jp-compat.src/io-control.at \
	jp-compat.src/greater-less-than-equal.at \
	jp-compat.src/file-desc.at \
	jp-compat.src/abort-on-file-error.at \
	jp-compat.src/system-routine.at

EXTRA_DIST = $(srcdir)/package.m4 $(TESTS) \
	$(syntax_DEPENDENCIES) \
	$(run_DEPENDENCIES) \
	$(data_rep_DEPENDENCIES) \
	$(i18n_utf8_DEPENDENCIES) \
	$(i18n_sjis_DEPENDENCIES) \
	$(jp_compat_DEPENDENCIES)


DISTCLEANFILES = atconfig

all: $(TESTS)

clean-local:
	rm -rf *.dir *.log

$(srcdir)/package.m4: $(top_srcdir)/configure.ac
	@echo "creating $(srcdir)/package.m4"
	@{								   \
	  echo '# Signature of the current package.';			   \
	  echo 'm4_define([AT_PACKAGE_NAME],	  [@PACKAGE_NAME@])';	   \
	  echo 'm4_define([AT_PACKAGE_TARNAME],	  [@PACKAGE_TARNAME@])';   \
	  echo 'm4_define([AT_PACKAGE_VERSION],	  [@PACKAGE_VERSION@])';   \
	  echo 'm4_define([AT_PACKAGE_STRING],	  [@PACKAGE_STRING@])';    \
	  echo 'm4_define([AT_PACKAGE_BUGREPORT], [@PACKAGE_BUGREPORT@])'; \
	} > $(srcdir)/package.m4

$(srcdir)/%: $(srcdir)/%.at $(srcdir)/package.m4
	autom4te --language=autotest -I $(srcdir) -I $@.src -o $@ $<
	chmod +x $@

$(srcdir)/syntax: $(syntax_DEPENDENCIES)
$(srcdir)/run: $(run_DEPENDENCIES)
$(srcdir)/data-rep: $(data_rep_DEPENDENCIES)
$(srcdir)/i18n_utf8: $(i18n_utf8_DEPENDENCIES)
$(srcdir)/i18n_sjis: $(i18n_sjis_DEPENDENCIES)
$(srcdir)/jp-compat: $(jp_compat_DEPENDENCIES)
