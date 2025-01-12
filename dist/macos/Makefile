.PHONY: all app clean mrproper

all: app

app: ../../build/iaito.app radare2-unpkg
	mkdir disk
	cp -a ../../build/iaito.app disk/
	scripts/embed-radare2.sh radare2-unpkg disk/iaito.app
	cd disk && macdeployqt iaito.app -dmg -verbose=2
	mv disk/*.dmg .

radare2-unpkg: radare2.pkg
	pkgutil --expand-full $< $@

radare2.pkg:
	echo "Download first radare2.pkg from https://github.com/radareorg/radare2/releases"
	@false

../../build/iaito.app:
	echo "Building iaito..."
	$(MAKE) -C ../.. QMAKE_FLAGS=IAITO_BUNDLE_R2_APPBUNDLE=true

clean:
	rm -rf disk radare2-unpkg

mrproper: clean
	rm -f radare2.pkg
