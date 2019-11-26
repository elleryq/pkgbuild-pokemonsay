# Maintainer: Yan-ren Tsai <elleryq@gmail.com>
_pkgname=pokemonsay
pkgname=$_pkgname-git
pkgver=r38.88e82d0
pkgrel=1
pkgdesc="\"pokemonsay\" is like \"cowsay\" but for pokémon. "
arch=('any')
url="https://github.com/possatti/pokemonsay"
license=('MIT')
groups=()
depends=('cowsay')
makedepends=('git')
optdepends=()
provides=()
conflicts=()
replaces=()
backup=()
options=()
changelog=
source=(
  "$pkgname"::"git+https://github.com/possatti/$_pkgname.git"
  pokemonsay
  pokemonthink
)
noextract=()
md5sums=('SKIP'
         '934fac473d6a0c3403cbc96b32a35662'
         '49ef1a92157ecb242243849d4000363f')

pkgver() {
    cd "$pkgname"
    (
        set -o pipefail
        git describe --long | sed -r 's/([^-]*-g)/r\1/;s/-/./g' ||
        printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
    )
}

build() {
  rm -rf "$pkgname/.git"
}

package() {
  install_path="$pkgdir/usr/share/pokemonsay"
  bin_path="$pkgdir/usr/bin"
  pokemonsay_bin="pokemonsay"
  pokemonthink_bin="pokemonthink"

  mkdir -p "$install_path"
  mkdir -p "$install_path/cows/"
  mkdir -p "$bin_path"

  # Copy the cows and the main script to the install path.
  cp $pkgname/cows/*.cow $install_path/cows/
  cp $pkgname/pokemonsay.sh $install_path/
  cp $pkgname/pokemonthink.sh $install_path/

  install -Dm755 pokemonsay "$bin_path/pokemonsay"
  install -Dm755 pokemonthink "$bin_path/pokemonthink"
}
