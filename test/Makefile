.PHONY: clean-vm clean-vagrant-metadata

all: test

test: test-boot test-compile test-cabal

test-boot:
	vagrant up

test-compile: test-boot
	vagrant ssh -c "cd /vagrant && ghc -o hello Hello.hs && ./hello"

test-cabal: test-boot
	vagrant ssh -c "cabal update && cabal install happy && which happy"

clean-vm:
	-vagrant destroy -f

clean-vagrant-metadata:
	-rm -rf .vagrant

clean: clean-vm clean-vagrant-metadata
