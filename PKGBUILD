# Maintainer: Augusto Hack <hack.augusto@gmail.com>
pkgname=tinyarch
pkgver=1
pkgrel=1
pkgdesc="Script to generate the smallest iso for unattended install"
arch=('x86_64')
license=('GPL')
depends=('zsh' 'pacman' 'systemd')
backup=('etc/mkinitcpio-tinyarch.conf' 'usr/share/tinyarch/tinyarch.cfg')
source=('mkinitcpio-tinyarch.conf' 'tinyarch.cfg' 'tinyarch_script' 'tinyarch_initcpio' 'tinyarch_qemu' 'init')
# makepkg -g
md5sums=('fcc948818001d3b88846473db356c7b9'
         '2680e02e7350ef3f60bed559fa096c50'
         '34f3bb0935464a4b7db4256aa3e32467'
         '3db96b75d2d15749f109804b0ea6c3dd'
         '83480b9ec59b6cbc863e1773611b1ff9'
         '92176cb816cdea64626ffed83c515944')

package() {
    install -D -m755 "$srcdir/tinyarch_script" "$pkgdir/usr/bin/tinyarch"
    install -D -m755 "$srcdir/init" "$pkgdir/usr/share/tinyarch/init"

    install -D -m644 "$srcdir/mkinitcpio-tinyarch.conf" "$pkgdir/etc/mkinitcpio-tinyarch.conf"
    install -D -m644 "$srcdir/tinyarch.cfg" "$pkgdir/usr/share/tinyarch/tinyarch.cfg"

    install -D -m644 "$srcdir/tinyarch_initcpio" "$pkgdir/usr/lib/initcpio/install/tinyarch"
    install -D -m644 "$srcdir/tinyarch_qemu" "$pkgdir/usr/lib/initcpio/install/tinyarch_qemu"
}
