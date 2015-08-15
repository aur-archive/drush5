# Original Maintainer: Josh 'jheretic' King <josh at chambana dot net>

pkgname=drush5
pkgrealname=drush
pkgver=5.8
pkgrel=1
pkgdesc="The Drupal command-line shell"
arch=('any')
url="http://drupal.org/project/drush/"
license=('GPL')
depends=('php' 'bash')
install=${pkgname}.install
conflicts=('drush')
replaces=('drush')
provides=('drush')
source=(http://ftp.drupal.org/files/projects/$pkgrealname-7.x-$pkgver.tar.gz \
http://download.pear.php.net/package/Console_Table-1.1.3.tgz)

build() {
  cd ${srcdir}/${pkgrealname}
  install -d ${pkgdir}/usr/lib/${pkgrealname}/commands
  cp -rf ${srcdir}/${pkgrealname}/commands/* ${pkgdir}/usr/lib/${pkgrealname}/commands/
  install -d ${pkgdir}/usr/lib/${pkgrealname}/includes
  cp -rf ${srcdir}/${pkgrealname}/includes/* ${pkgdir}/usr/lib/${pkgrealname}/includes/
  install -d ${pkgdir}/usr/share/doc/${pkgrealname}/examples
  cp -rf ${srcdir}/${pkgrealname}/examples/* ${pkgdir}/usr/share/doc/${pkgrealname}/examples/
  #Install Console_Table library so Drush doesn't have to
  cp -rf ${srcdir}/Console_Table-1.1.3/Table.php ${pkgdir}/usr/lib/${pkgrealname}/includes/table.inc
  chmod -x ${pkgdir}/usr/lib/${pkgrealname}/includes/table.inc
  install -Dm755 ./drush.php ${pkgdir}/usr/lib/drush/drush.php || return 1
  install -Dm755 ./drush ${pkgdir}/usr/lib/drush/drush || return 1
  install -Dm644 ./drush.info ${pkgdir}/usr/lib/drush/drush.info || return 1
  install -Dm644 ./docs/drush.api.php ${pkgdir}/usr/lib/drush/drush.api.php || return 1
  install -Dm644 ./README.txt ${pkgdir}/usr/share/doc/drush/README.txt || return 1
  install -Dm644 ./LICENSE.txt ${pkgdir}/usr/share/doc/drush/LICENSE.txt || return 1
  install -Dm644 ./drush_logo-black.png ${pkgdir}/usr/share/doc/drush/drush_logo-black.png || return 1
  install -Dm644 ./examples/example.drushrc.php ${pkgdir}/etc/drush/example.drushrc.php || return 1
  install -Dm644 ./examples/example.aliases.drushrc.php ${pkgdir}/etc/drush/example.aliases.drushrc.php || return 1
  install -Dm644 ./examples/example.drush.ini ${pkgdir}/etc/drush/example.drush.ini || return 1
  mkdir -p ${pkgdir}/usr/bin
  ln -s /usr/lib/drush/drush ${pkgdir}/usr/bin/drush
  #Make directory for eventual packaged drush extensions
  mkdir -p ${pkgdir}/usr/share/drush/commands
}
md5sums=('1ec16e87b73c94739faa98a00a8c3538'
         '34b5f34db1ab0c4daedf2862958af257')
