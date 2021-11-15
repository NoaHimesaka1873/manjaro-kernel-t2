# Maintainer: Bernhard Landauer <bernhard@manjaro.org>
# Maintainer: Philip Müller <philm[at]manjaro[dot]org>
# Arch credits:
# Tobias Powalowski <tpowa@archlinux.org>
# Thomas Baechler <thomas@archlinux.org>

pkgbase=linux516
pkgname=('linux515' 'linux515-headers')
_kernelname=-MANJARO
_basekernel=5.16
_basever=516
_rc=rc1
_commit=fa55b7dcdc43c1aa1ba12bca9d2dd4318c2a0dbf
pkgver=5.16rc1.211115.gfa55b7d
pkgrel=1
arch=('x86_64')
url="https://www.kernel.org/"
license=('GPL2')
makedepends=('bc'
    'docbook-xsl'
    'libelf'
    'pahole'
    'git'
    'inetutils'
    'kmod'
    'xmlto'
    'cpio'
    'perl'
    'tar'
    'xz')
options=('!strip')
source=("https://codeload.github.com/torvalds/linux/zip/$_commit"
        #"https://www.kernel.org/pub/linux/kernel/v5.x/linux-${_basekernel}.tar.xz"
        #"https://www.kernel.org/pub/linux/kernel/v5.x/patch-${pkgver}.xz"
        'config'
        # ARCH Patches
        '0001-ZEN-Add-sysctl-and-CONFIG-to-disallow-unprivileged-CLONE_NEWUSER.patch'
        '0002-HID-quirks-Add-Apple-Magic-Trackpad-2-to-hid_have_special_driver-list.patch'
        # Temp Fixes
        # MANJARO Patches
        '0101-i2c-nuvoton-nc677x-hwmon-driver.patch'
##        '0102-iomap-iomap_bmap-should-accept-unwritten-maps.patch'
##        '0103-futex.patch'
#        '0104-revert-xhci-Add-support-for-Renesas-controller-with-memory.patch'
        '0105-quirk-kernel-org-bug-210681-firmware_rome_error.patch'
        # Lenovo + AMD
#        '0201-lenovo-wmi2.patch'
        # other patches
        # Bootsplash
#        '0301-revert-fbcon-remove-now-unusued-softback_lines-cursor-argument.patch'        
#        '0302-revert-fbcon-remove-no-op-fbcon_set_origin.patch'
#        '0303-revert-fbcon-remove-soft-scrollback-code.patch'
#        '0401-bootsplash.patch'
#        '0402-bootsplash.patch'
#        '0403-bootsplash.patch'
#        '0404-bootsplash.patch'
#        '0405-bootsplash.patch'
#        '0406-bootsplash.patch'
#        '0407-bootsplash.patch'
#        '0408-bootsplash.patch'
#        '0409-bootsplash.patch'
#        '0410-bootsplash.patch'
#        '0411-bootsplash.patch'
#        '0412-bootsplash.patch'
#        '0413-bootsplash.gitpatch'
        )
sha256sums=('cc38ca61b94b5663bf5964ed82e7d9eb5090c4a3b03ae6d86d235671bec47470'
            '4891b6e754ee1bd7e0f6faa62de9d092ed056d03165d96cba9917de82f26b75e'
            '986f8d802f37b72a54256f0ab84da83cb229388d58c0b6750f7c770818a18421'
            'df5843818f1571841e1a8bdbe38d7f853d841f38de46d6a6a5765de089495578'
            '7823d7488f42bc4ed7dfae6d1014dbde679d8b862c9a3697a39ba0dae5918978'
            '5e804e1f241ce542f3f0e83d274ede6aa4b0539e510fb9376f8106e8732ce69b')

pkgver() {
  printf %s%s.%s.g%s "$_basekernel" "$_rc" "$(date +%y%m%d)" "${_commit:0:7}"
}

prepare() {
  cd linux-$_commit
#  cd "linux-${_basekernel}"

  # add upstream patch
#  msg "add upstream patch"
#  patch -p1 -i "../patch-${pkgver}"

  local src
  for src in "${source[@]}"; do
      src="${src%%::*}"
      src="${src##*/}"
      [[ $src = *.patch ]] || continue
      msg2 "Applying patch: $src..."
      patch -Np1 < "../$src"
  done

#  msg2 "0513-bootsplash"
#  git apply -p1 < "../0413-bootsplash.gitpatch"

  msg2 "add config"
  cat "../config" > ./.config

  if [ "${_kernelname}" != "" ]; then
    sed -i "s|CONFIG_LOCALVERSION=.*|CONFIG_LOCALVERSION=\"${_kernelname}\"|g" ./.config
    sed -i "s|CONFIG_LOCALVERSION_AUTO=.*|CONFIG_LOCALVERSION_AUTO=n|" ./.config
  fi

  msg "set extraversion to pkgrel"
  sed -ri "s|^(EXTRAVERSION =).*|\1 -${pkgrel}|" Makefile

  # set patchlevel to 14
  #sed -ri "s|^(PATCHLEVEL =).*|\1 14|" Makefile

  msg "don't run depmod on 'make install'"
  # We'll do this ourselves in packaging
  sed -i '2iexit 0' scripts/depmod.sh

  msg "get kernel version"
  make prepare

  msg "rewrite configuration"
  yes "" | make config >/dev/null
}

build() {
  cd linux-$_commit
#  cd "linux-${_basekernel}"

  msg "build"
  make ${MAKEFLAGS} LOCALVERSION= bzImage modules
}

package_linux515() {
  pkgdesc="The ${pkgbase/linux/Linux} kernel and modules"
  depends=('coreutils' 'linux-firmware' 'kmod' 'mkinitcpio>=27')
  optdepends=('crda: to set the correct wireless channels of your country')
  provides=("linux=${pkgver}" VIRTUALBOX-GUEST-MODULES WIREGUARD-MODULE)

  cd linux-$_commit
#  cd "linux-${_basekernel}"

  # get kernel version
  _kernver="$(make LOCALVERSION= kernelrelease)"

  mkdir -p "${pkgdir}"/{boot,usr/lib/modules}
  make LOCALVERSION= INSTALL_MOD_PATH="${pkgdir}/usr" INSTALL_MOD_STRIP=1 modules_install

  # systemd expects to find the kernel here to allow hibernation
  # https://github.com/systemd/systemd/commit/edda44605f06a41fb86b7ab8128dcf99161d2344
  cp arch/x86/boot/bzImage "${pkgdir}/usr/lib/modules/${_kernver}/vmlinuz"

  # Used by mkinitcpio to name the kernel
  echo "${pkgbase}" | install -Dm644 /dev/stdin "${pkgdir}/usr/lib/modules/${_kernver}/pkgbase"
  echo "${_basekernel}-${CARCH}" | install -Dm644 /dev/stdin "${pkgdir}/usr/lib/modules/${_kernver}/kernelbase"

  # add kernel version
  echo "${pkgver}-${pkgrel}-MANJARO x64" > "${pkgdir}/boot/${pkgbase}-${CARCH}.kver"

  # make room for external modules
  local _extramodules="extramodules-${_basekernel}${_kernelname:--MANJARO}"
  ln -s "../${_extramodules}" "${pkgdir}/usr/lib/modules/${_kernver}/extramodules"

  # add real version for building modules and running depmod from hook
  echo "${_kernver}" |
    install -Dm644 /dev/stdin "${pkgdir}/usr/lib/modules/${_extramodules}/version"

  # remove build and source links
  rm "${pkgdir}"/usr/lib/modules/${_kernver}/{source,build}

  # now we call depmod...
  depmod -b "${pkgdir}/usr" -F System.map "${_kernver}"
}

package_linux515-headers() {
  pkgdesc="Header files and scripts for building modules for ${pkgbase/linux/Linux} kernel"
  depends=('gawk' 'python' 'libelf' 'pahole')
  provides=("linux-headers=$pkgver")

  cd linux-$_commit
#  cd "linux-${_basekernel}"
  local _builddir="${pkgdir}/usr/lib/modules/${_kernver}/build"

  install -Dt "${_builddir}" -m644 Makefile .config Module.symvers
  install -Dt "${_builddir}/kernel" -m644 kernel/Makefile
  install -Dt "${_builddir}" -m644 vmlinux  

  mkdir "${_builddir}/.tmp_versions"

  cp -t "${_builddir}" -a include scripts

  install -Dt "${_builddir}/arch/x86" -m644 "arch/x86/Makefile"
  install -Dt "${_builddir}/arch/x86/kernel" -m644 "arch/x86/kernel/asm-offsets.s"

  cp -t "${_builddir}/arch/x86" -a "arch/x86/include"

  install -Dt "${_builddir}/drivers/md" -m644 drivers/md/*.h
  install -Dt "${_builddir}/net/mac80211" -m644 net/mac80211/*.h

  # https://bugs.archlinux.org/task/13146
  install -Dt "${_builddir}/drivers/media/i2c" -m644 drivers/media/i2c/msp3400-driver.h

  # https://bugs.archlinux.org/task/20402
  install -Dt "${_builddir}/drivers/media/usb/dvb-usb" -m644 drivers/media/usb/dvb-usb/*.h
  install -Dt "${_builddir}/drivers/media/dvb-frontends" -m644 drivers/media/dvb-frontends/*.h
  install -Dt "${_builddir}/drivers/media/tuners" -m644 drivers/media/tuners/*.h

  # https://bugs.archlinux.org/task/71392
  install -Dt "${_builddir}/drivers/iio/common/hid-sensors" -m644 drivers/iio/common/hid-sensors/*.h

  # add xfs and shmem for aufs building
  mkdir -p "${_builddir}"/{fs/xfs,mm}

  # copy in Kconfig files
  find . -name Kconfig\* -exec install -Dm644 {} "${_builddir}/{}" \;

  # add objtool for external module building and enabled VALIDATION_STACK option
  install -Dt "${_builddir}/tools/objtool" tools/objtool/objtool

  # remove unneeded architectures
  local _arch
  for _arch in "${_builddir}"/arch/*/; do
    [[ ${_arch} == */x86/ ]] && continue
    rm -r "${_arch}"
  done

  # remove documentation files
  rm -r "${_builddir}/Documentation"

  # strip scripts directory
  local file
  while read -rd '' file; do
    case "$(file -bi "$file")" in
      application/x-sharedlib\;*)      # Libraries (.so)
        strip $STRIP_SHARED "$file" ;;
      application/x-archive\;*)        # Libraries (.a)
        strip $STRIP_STATIC "$file" ;;
      application/x-executable\;*)     # Binaries
        strip $STRIP_BINARIES "$file" ;;
      application/x-pie-executable\;*) # Relocatable binaries
        strip $STRIP_SHARED "$file" ;;
    esac
  done < <(find "${_builddir}" -type f -perm -u+x ! -name vmlinux -print0 2>/dev/null)
  strip $STRIP_STATIC "${_builddir}/vmlinux"
  
  # remove unwanted files
  find ${_builddir} -name '*.orig' -delete
}
