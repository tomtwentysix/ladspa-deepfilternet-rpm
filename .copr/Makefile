# Called by COPR as: make -f .copr/Makefile srpm outdir=<dir> spec=<spec>
top := $(abspath $(dir $(lastword $(MAKEFILE_LIST)))/..)
version := $(shell sed -n 's/^Version:[[:space:]]*//p' $(top)/ladspa-deepfilternet.spec)

srpm:
	command -v curl || dnf -y install curl
	curl -fsSL -o $(outdir)/DeepFilterNet-$(version).tar.gz \
		https://github.com/Rikorose/DeepFilterNet/archive/v$(version)/DeepFilterNet-$(version).tar.gz
	rpmbuild -bs --define "_sourcedir $(outdir)" --define "_srcrpmdir $(outdir)" $(top)/ladspa-deepfilternet.spec
