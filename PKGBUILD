# Maintainer: Sébastien Luttringer

pkgname=archutils-git
pkgver=1
pkgrel=1
pkgdesc='Seblu Archlinux Utils'
arch=('any')
url='https://github.com/seblu/archutils'
license=('GPL2')
depends=('python' 'bash' 'devtools')

pkgver() {
  git log -1 --pretty=format:%h
}

package() {
  cd "$startdir"
  install -dm755 "$pkgdir"/usr/{share/licenses/$pkgname,share/devtools,bin}
  # install legal stuff
  install -m644 COPYRIGHT LICENSE "$pkgdir/usr/share/licenses/$pkgname"
  # install config
  install -m644 pacman-seblu.conf "$pkgdir/usr/share/devtools"
  # install binaries
  install -m755 atc seblu-build seblu-repo-add aurdown seblu-build-commit \
    seblu-update go2chroot seblu-commit	addpkg sign archbuild-dl pkgbuild2json \
    seblu-remove tmpmakepkg seblu-cleanup "$pkgdir/usr/bin"
  # symlink archbuild
  ln -s archbuild $pkgdir/usr/bin/seblu-i686-build
  ln -s archbuild $pkgdir/usr/bin/seblu-x86_64-build
}

# vim:set ts=2 sw=2 et:
