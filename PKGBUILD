# Maintainer: Sébastien Luttringer

pkgname=archutils-git
pkgver=$(date +%Y.%m.%d)
pkgrel=1
pkgdesc='Seblu Archlinux Utils'
arch=('any')
url='https://github.com/seblu/archutils'
license=('GPL2')
depends=('python' 'bash' 'zsh' 'file' 'grep' 'pyalpm' 'python-pyelftools'
         'python-pygments')
provides=('archutils' 'kernel-reinstall')
replaces=('kernel-reinstall')
conflicts=('archutils' 'kernel-reinstall')

package() {
  cd "$startdir"
  install -dm755 "$pkgdir"/usr/{share/{licenses/$pkgname,libalpm/hooks},bin,lib/munin/plugins}
  # install legal stuff
  install -m644 COPYRIGHT LICENSE "$pkgdir/usr/share/licenses/$pkgname"
  # install binaries
  install -m755 atc aurdown go2chroot addpkg sign getpkg pkgbuild2json \
    tmpmakepkg reinstallpkgs checkservices archlinux-update reexec \
    kernel-reinstall system-upgrade find-deps "$pkgdir/usr/bin"
  # install munin stuff
  install -m755 archlinux-{pacfiles,packages} "$pkgdir/usr/lib/munin/plugins"
  # add shortcut, because i'm lazy
  ln -s checkservices "$pkgdir/usr/bin/cs"
  ln -s system-upgrade "$pkgdir/usr/bin/sup"
  # add hooks
  install -m644 systemd-daemon-reload.hook "$pkgdir/usr/share/libalpm/hooks/10-systemd-daemon-reload.hook"
}

# vim:set ts=2 sw=2 et:
