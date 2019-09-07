# snapd for RHEL 8

## Introduction
I wanted to install Spotify, but there weren't any snapd RPMs for RHEL8. So I said fuck it and built them myself.

## Easy Way
Snort down the rpm files with your favorite client into a directory, and then just run sudo dnf localinstall *.rpm like a normal person.

# Hard Way

> sudo subscription-manager repos --enable=codeready-builder-for-rhel-8-x86_64-rpms 

> sudo dnf install @go-toolset python3-docutils libudev-devel libcap-devel selinux-policy-devel xfsprogs-devel libseccomp-devel glibc-static glib2-devel go-compilers-golang-compiler

> mkdir -p ~/rpmbuild/SOURCES

> wget https://github.com/snapcore/snapd/releases/download/2.41/snapd_2.41.no-vendor.tar.xz

> wget https://github.com/snapcore/snapd/releases/download/2.41/snapd_2.41.only-vendor.tar.xz

> cd ..

> wget https://github.com/snapcore/snapd/archive/2.41.tar.gz -O- | tar -xf

> cd snapd-2.41

> spectool -g ./packaging/fedora/snapd.spec

> rpmbuild -bb ./packaging/fedora/snapd.spec

Then from there grab the RPMs out there, stick them all in a folder, and run sudo dnf localinstall *.rpm. But if you are going this route, you probably already know that...