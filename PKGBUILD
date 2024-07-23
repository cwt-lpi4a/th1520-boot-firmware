# Maintainer: Chaiwat Suttipongsakul <cwt@bashell.com>

pkgbase=th1520-boot-firmware
pkgname=('th1520-boot-firmware'
         'th1520-vendor-opensbi'
         'th1520-mainline-opensbi')
pkgver=r9.bc5d334
pkgrel=1
url="https://github.com/revyos/th1520-boot-firmware"
arch=(riscv64)
license=('proprietary')
makedepends=(git)
options=('!strip')
source=("git+https://github.com/revyos/th1520-boot-firmware.git")
sha256sums=('SKIP')

pkgver() {
  cd "$srcdir/$pkgbase"
  printf 'r%s.%s' "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

package_th1520-boot-firmware() {
  pkgdesc="TH1520 boot firmware"
  cd "$srcdir/$pkgbase/addons/boot"
  install -Dm644 light_aon_fpga.bin \
    "${pkgdir}/boot/light_aon_fpga.bin"
  install -Dm644 light_c906_audio.bin \
    "${pkgdir}/boot/light_c906_audio.bin"
  install -Dm644 str.bin \
    "${pkgdir}/boot/str.bin"
}

package_th1520-vendor-opensbi() {
  pkgdesc="TH1520 vendor opensbi"
  conflicts=('th1520-mainline-opensbi')
  cd "$srcdir/$pkgbase/opensbi"
  install -Dm644 fw_dynamic.bin.vendor \
    "${pkgdir}/boot/fw_dynamic.bin"
}

package_th1520-mainline-opensbi() {
  pkgdesc="TH1520 mainline opensbi"
  conflicts=('th1520-vendor-opensbi')
  cd "$srcdir/$pkgbase/opensbi"
  install -Dm644 fw_dynamic.bin.mainline \
    "${pkgdir}/boot/fw_dynamic.bin"
}

# vim:set ts=8 sts=2 sw=2 et:
