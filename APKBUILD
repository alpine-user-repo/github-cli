pkgname=github-cli-git
repository="https://github.com/cli/cli.git"
builddir="${srcdir}/cli"
pkgver="_git"
pkgrel=0
pkgdesc="The GitHub CLI tool"
arch='x86_64'
url="https://github.com/cli/cli"
license='MIT'
depends='git'
makedepends='git go'
provides='github-cli'
conflicts='github-cli'
source=""

# Build flags
export CGO_CPPFLAGS="${CPPFLAGS}"
export CGO_CFLAGS="${CFLAGS}"
export CGO_CXXFLAGS="${CXXFLAGS}"
export CGO_LDFLAGS="${LDFLAGS}"
export GOFLAGS="-buildmode=pie -ldflags=-linkmode=external -trimpath -mod=readonly -modcacherw"

prepare() { 
    default_prepare
    cd "$srcdir"
    git clone --depth=1 "${repository}"
}

build() {
  cd "${builddir}"
  go build "./cmd/gh"
}

package() {
  cd "${builddir}"

  install -Dm755 "gh" -t "$pkgdir/usr/bin"
}
