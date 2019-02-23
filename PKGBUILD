pkgname=adapta-noah-theme
pkgver=3.95.0.11.r8.d668e581
pkgrel=1
pkgdesc='An adaptive Gtk+ theme based on Material Design Guidelines'
arch=('any')
url='https://github.com/Strum355/adapta-gtk-theme'
license=('GPL2')
depends=('gtk-engine-murrine' 'gtk3')
makedepends=('git' 'gnome-shell' 'inkscape' 'libxml2' 'parallel' 'sassc')
optdepends=('gnome-shell: The GNOME Shell'
            'gnome-flashback: The GNOME flashback shell'
            'budgie-desktop: The Budgie desktop'
            'cinnamon: The Cinnamon desktop'
            'xfdesktop: The Xfce desktop')
provides=('adapta-noah-theme')
conflicts=('adapta-noah-theme')
source=()
#'git+https://github.com/Strum355/adapta-gtk-theme.git'
sha256sums=('SKIP')

pkgver() {
  cd ..

  git describe --tags | sed 's/-/.r/; s/-g/./'
}

build() {
  cd ..
  
  ./autogen.sh \
    --prefix=/usr \
    --disable-gnome \
    --disable-flashback \
    --disable-xfce \
    --disable-mate \
    --disable-openbox \
    --disable-plank \
    --enable-parallel \
    --with-selection_color='#3C87D8' \
    --with-accent_color='#9FC782' \
    --with-suggestion_color='#71AB5C' \
    --with-destruction_color='#E0685C'
  make
}

package() {
  cd ..

  make DESTDIR="${pkgdir}" install

  install -dm 755 "${pkgdir}"/usr/share/plank/themes
  ln -s /usr/share/themes/Adapta/plank "${pkgdir}"/usr/share/plank/themes/Adapta-Noah
}