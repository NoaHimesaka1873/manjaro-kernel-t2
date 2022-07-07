# Maintainer: Noa Himesaka <himesaka@noa.codes>
# Manjaro maintainers:
# Maintainer: Bernhard Landauer <bernhard@manjaro.org>
# Maintainer: Philip Müller <philm[at]manjaro[dot]org>
# Archlinux maintainers:
# Tobias Powalowski <tpowa@archlinux.org>
# Thomas Baechler <thomas@archlinux.org>

pkgver=5.18.7
pkgrel=1
_basekernel=5.18
_basever=${_basekernel//.}
_kernelname=-T2-OTOTSUKU
pkgbase=linux${_basever}-t2
pkgname=("$pkgbase" "$pkgbase-headers")
arch=('x86_64')
url="https://www.kernel.org/"
license=('GPL2')
makedepends=(bc docbook-xsl libelf pahole git inetutils kmod xmlto cpio perl tar xz)
options=('!strip')
source=("https://www.kernel.org/pub/linux/kernel/v5.x/linux-${_basekernel}.tar.xz"
        "https://www.kernel.org/pub/linux/kernel/v5.x/patch-${pkgver}.xz"
        'config'
        # Bootsplash
        '0301-revert-fbcon-remove-now-unusued-softback_lines-cursor-argument.patch'
        '0302-revert-fbcon-remove-no-op-fbcon_set_origin.patch'
        '0303-revert-fbcon-remove-soft-scrollback-code.patch'
        '0401-bootsplash.patch'
        '0402-bootsplash.patch'
        '0403-bootsplash.patch'
        '0404-bootsplash.patch'
        '0405-bootsplash.patch'
        '0406-bootsplash.patch'
        '0407-bootsplash.patch'
        '0408-bootsplash.patch'
        '0409-bootsplash.patch'
        '0410-bootsplash.patch'
        '0411-bootsplash.patch'
        '0412-bootsplash.patch'
        '0413-bootsplash.gitpatch'
  # apple-bce, apple-ibridge
  apple-bce::git+https://github.com/t2linux/apple-bce-drv#commit=f93c6566f98b3c95677de8010f7445fa19f75091
  apple-ibridge::git+https://github.com/Redecorating/apple-ib-drv#commit=467df9b11cb55456f0365f40dd11c9e666623bf3

  1001-Put-apple-bce-and-apple-ibridge-in-drivers-staging.patch
  1002-add-modalias-to-apple-bce.patch

  # Fix some acpi errors
  2001-fix-acpica-for-zero-arguments-acpi-calls.patch

  # Apple SMC ACPI support
  3001-applesmc-convert-static-structures-to-drvdata.patch
  3002-applesmc-make-io-port-base-addr-dynamic.patch
  3003-applesmc-switch-to-acpi_device-from-platform.patch
  3004-applesmc-key-interface-wrappers.patch
  3005-applesmc-basic-mmio-interface-implementation.patch
  3006-applesmc-fan-support-on-T2-Macs.patch
  3007-applesmc-Add-iMacPro-to-applesmc_whitelist.patch

  # T2 USB Touchpad support
  4001-Input-bcm5974-Add-support-for-the-T2-Macs.patch

  # make hid not touch tb to avoid `vhci: [00] URB failed: 3`
  5001-Fix-for-touchbar.patch

  # Hack for i915 overscan issues
  7001-drm-i915-fbdev-Discard-BIOS-framebuffers-exceeding-h.patch

  # Broadcom WIFI device support
  # https://github.com/AsahiLinux/linux/commits/bits/080-wifi
  8001-asahilinux-wifi-patchset.patch

)
sha256sums=('51f3f1684a896e797182a0907299cc1f0ff5e5b51dd9a55478ae63a409855cee'
	    'SKIP'
            '523ffb848dd39df0fb93f668e1985b514a23ae31b1892c415753b83651979c04'
            '2b11905b63b05b25807dd64757c779da74dd4c37e36d3f7a46485b1ee5a9d326'
            '94a8538251ad148f1025cc3de446ce64f73dc32b01815426fb159c722e8fa5bc'
            '1f18c5c10a3c63e41ecd05ad34cd9f6653ba96e9f1049ce2b7bb6da2578ae710'
            '59202940d4f12bad23c194a530edc900e066866c9945e39748484a6545af96de'
            'e096b127a5208f56d368d2cb938933454d7200d70c86b763aa22c38e0ddb8717'
            '8c1c880f2caa9c7ae43281a35410203887ea8eae750fe8d360d0c8bf80fcc6e0'
            '1144d51e5eb980fceeec16004f3645ed04a60fac9e0c7cf88a15c5c1e7a4b89e'
            'dd4b69def2efacf4a6c442202ad5cb93d492c03886d7c61de87696e5a83e2846'
            '028b07f0c954f70ca37237b62e04103e81f7c658bb8bd65d7d3c2ace301297dc'
            'a0c548c5703d25ae34b57931f1162de8b18937e676e5791a0f039922090881e7'
            '8dbb5ab3cb99e48d97d4e2f2e3df5d0de66f3721b4f7fd94a708089f53245c77'
            'a7aefeacf22c600fafd9e040a985a913643095db7272c296b77a0a651c6a140a'
            'e9f22cbb542591087d2d66dc6dc912b1434330ba3cd13d2df741d869a2c31e89'
            '27471eee564ca3149dd271b0817719b5565a9594dc4d884fe3dc51a5f03832bc'
            '60e295601e4fb33d9bf65f198c54c7eb07c0d1e91e2ad1e0dd6cd6e142cb266d'
            '035ea4b2a7621054f4560471f45336b981538a40172d8f17285910d4e0e0b3ef'
            'SKIP'
            'SKIP'
            'b7c987889d92a48d638d5258842b10f6c856e57f29ad23475aa507c7b4ad5710'
            'a3a43feaffccbcd119f4a1b4e1299ef07ae36ef9bffc17767bf10e447fa02a2a'
            '45b911e592dd6c717e77ec4d8cbf844860bb7c29ace7a7170e7bf59c12e91bb4'
            'cfd23a06797ac86575044428a393dd7f10f06eff7648d0b78aedad82cbe41279'
            '8d8401a99a9dfbc41aa2dc5b6a409a19860b1b918465e19de4a4ff18de075ea3'
            '08d165106fe35b68a7b48f216566951a5db0baac19098c015bcc81c5fcba678d'
            '62f6d63815d4843ca893ca76b84a9d32590a50358ca0962017ccd75a40884ba8'
            '2827dab6eeb2d2a08034938024f902846b5813e967a0ea253dc1ea88315da383'
            '398dec7d54c6122ae2263cd5a6d52353800a1a60fd85e52427c372ea9974a625'
            'd4ca5a01da5468a1d2957b8eb4a819e1b867a3bcd1cd47389d7c9ac9154b5430'
            'b1f19084e9a9843dd8c457c55a8ea8319428428657d5363d35df64fb865a4eae'
            '92e6f4173074ac902c3fc397ea39a5ff6d5eb8645539645c0cd61b3d05ac83ca'
            '9ede98eceb69e9c93e25fdb2c567466963bdd2f81c0ecb9fb9e5107f6142ff26'
            'f307d149ac9a48bbfd5ea678ff80457e31ae6f788ec8915f19f128d0bd966d65')

prepare() {
  cd "linux-${_basekernel}"

  # add upstream patch
  #msg "add upstream patch"
  #patch -p1 -i "../patch-${pkgver}"

  for i in apple-bce apple-ibridge; do
    echo "Copying $i in to drivers/staging..."
	# no need to copy .git/
	mkdir drivers/staging/$i
    cp -r $srcdir/$i/* drivers/staging/$i/
  done

  local src
  for src in "${source[@]}"; do
      src="${src%%::*}"
      src="${src##*/}"
      [[ $src = *.patch ]] || continue
      msg2 "Applying patch: $src..."
      patch -Np1 < "../$src"
  done

  msg2 "0513-bootsplash"
  git apply -p1 < "../0413-bootsplash.gitpatch"

  msg2 "add config"
  cp ../config .config
	make olddefconfig
	diff -u ../config .config || :

  if [ "${_kernelname}" != "" ]; then
    sed -i "s|CONFIG_LOCALVERSION=.*|CONFIG_LOCALVERSION=\"${_kernelname}\"|g" ./.config
    sed -i "s|CONFIG_LOCALVERSION_AUTO=.*|CONFIG_LOCALVERSION_AUTO=n|" ./.config
  fi

  msg "set extraversion to pkgrel"
  sed -ri "s|^(EXTRAVERSION =).*|\1 -${pkgrel}|" Makefile

  msg "don't run depmod on 'make install'"
  # We'll do this ourselves in packaging
  sed -i '2iexit 0' scripts/depmod.sh

  msg "get kernel version"
  make prepare

  msg "rewrite configuration"
  yes "" | make config >/dev/null
}

build() {
  cd "linux-${_basekernel}"

  msg "build"
  make LOCALVERSION= bzImage modules
}

package_linux518-t2() {
  pkgdesc="The ${pkgbase/linux/Linux} kernel and modules for Macs with Apple T2 security chip"
  depends=('coreutils' 'linux-firmware' 'kmod' 'mkinitcpio>=27')
  optdepends=('wireless-regdb: to set the correct wireless channels of your country')
  replaces=('linux57-mbp' 'linux56-mbp' 'linux516-t2' 'linux517-t2')
  conflicts=('apple-bce-dkms-git' 'apple-bce-git' 'apple-ibridge-dkms-git' 'apple-ibridge-git')
  provides=("linux=${pkgver}" VIRTUALBOX-GUEST-MODULES WIREGUARD-MODULE)

  cd "linux-${_basekernel}"

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

package_linux518-t2-headers() {
  pkgdesc="Header files and scripts for building modules for ${pkgbase/linux/Linux} kernel for Macs with Apple T2 security chip"
  depends=('gawk' 'python' 'libelf' 'pahole')
  replaces=('linux57-mbp-headers' 'linux56-mbp-headers' 'linux516-t2-headers' 'linux517-t2-headers')
  provides=("linux-headers=$pkgver")

  cd "linux-${_basekernel}"
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

  # https://forum.manjaro.org/t/90629/39
  install -Dt "${_builddir}/tools/bpf/resolve_btfids" tools/bpf/resolve_btfids/resolve_btfids

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
