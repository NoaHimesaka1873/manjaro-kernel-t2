# Maintainer: Bernhard Landauer <bernhard@manjaro.org>
# Maintainer: Philip Müller <philm[at]manjaro[dot]org>
# Arch credits:
# Tobias Powalowski <tpowa@archlinux.org>
# Thomas Baechler <thomas@archlinux.org>

pkgver=5.16.7
pkgrel=1
_basekernel=5.16
_basever=${_basekernel//.}
pkgbase=linux${_basever}
_kernelname=-t2-MANJARO
pkgname=("$pkgbase-t2" "$pkgbase-t2-headers")
arch=('x86_64')
url="https://www.kernel.org/"
license=('GPL2')
makedepends=(bc docbook-xsl libelf pahole git inetutils kmod xmlto cpio perl tar xz)
options=('!strip')
source=("https://github.com/t2linux/kernel/archive/refs/tags/t2-v${pkgver}.tar.gz"
        'config'
        # ARCH Patches
        '0001-ZEN-Add-sysctl-and-CONFIG-to-disallow-unprivileged-CLONE_NEWUSER.patch'
        '0002-Btintel_Fix_bdaddress_comparison_with_garbage_value.patch'
        '0003-Bt_Read_codec_capabilities_only_if_supported.patch'
        # Temp Fixes
        # MANJARO Patches
        '0101-i2c-nuvoton-nc677x-hwmon-driver.patch'
#        '0102-iomap-iomap_bmap-should-accept-unwritten-maps.patch'
#        '0104-revert-xhci-Add-support-for-Renesas-controller-with-memory.patch'
        '0105-quirk-kernel-org-bug-210681-firmware_rome_error.patch'
        # Lenovo + AMD
#        '0201-lenovo-wmi2.patch'
        # Bootsplash
        '0301-revert-garbage-collect-fbdev-scrolling-acceleration.patch'
        '0302-revert-fbcon-remove-now-unusued-softback_lines-cursor-argument.patch'
        '0303-revert-fbcon-remove-no-op-fbcon_set_origin.patch'
        '0304-revert-fbcon-remove-soft-scrollback-code.patch'
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
        8001-brcmfmac-pcie-Declare-missing-firmware-files-in-pcie.patch
        8002-brcmfmac-firmware-Support-having-multiple-alt-paths.patch
        8003-brcmfmac-firmware-Handle-per-board-clm_blob-files.patch
        8004-brcmfmac-pcie-sdio-usb-Get-CLM-blob-via-standard-fir.patch
        8005-brcmfmac-firmware-Support-passing-in-multiple-board_.patch
        8006-brcmfmac-pcie-Read-Apple-OTP-information.patch
        8007-brcmfmac-of-Fetch-Apple-properties.patch
        8008-brcmfmac-pcie-Perform-firmware-selection-for-Apple-p.patch
        8009-brcmfmac-firmware-Allow-platform-to-override-macaddr.patch
        8010-brcmfmac-msgbuf-Increase-RX-ring-sizes-to-1024.patch
        8011-brcmfmac-pcie-Fix-crashes-due-to-early-IRQs.patch
        8012-brcmfmac-pcie-Support-PCIe-core-revisions-64.patch
        8013-brcmfmac-pcie-Add-IDs-properties-for-BCM4378.patch
        8014-ACPI-property-Support-strings-in-Apple-_DSM-props.patch
        8015-brcmfmac-acpi-Add-support-for-fetching-Apple-ACPI-pr.patch
        8016-brcmfmac-pcie-Provide-a-buffer-of-random-bytes-to-th.patch
        8017-brcmfmac-pcie-Add-IDs-properties-for-BCM4355.patch
        8018-brcmfmac-pcie-Add-IDs-properties-for-BCM4377.patch
        8019-brcmfmac-pcie-Perform-correct-BCM4364-firmware-selec.patch
        8020-brcmfmac-chip-Only-disable-D11-cores-handle-an-arbit.patch
        8021-brcmfmac-chip-Handle-1024-unit-sizes-for-TCM-blocks.patch
        8022-brcmfmac-cfg80211-Add-support-for-scan-params-v2.patch
        8023-brcmfmac-feature-Add-support-for-setting-feats-based.patch
        8024-brcmfmac-cfg80211-Add-support-for-PMKID_V3-operation.patch
        8025-brcmfmac-cfg80211-Pass-the-PMK-in-binary-instead-of-.patch
        8026-brcmfmac-pcie-Add-IDs-properties-for-BCM4387.patch
        8027-brcmfmac-pcie-Replace-brcmf_pcie_copy_mem_todev-with.patch
        8028-brcmfmac-pcie-Read-the-console-on-init-and-shutdown.patch
        8029-brcmfmac-pcie-Release-firmwares-in-the-brcmf_pcie_se.patch
        # 8030 only applies to the linux-asahi tree and is only for M1 Macs
        8031-brcmfmac-fwil-Constify-iovar-name-arguments.patch
        8032-brcmfmac-common-Add-support-for-downloading-TxCap-bl.patch
        8033-brcmfmac-pcie-Load-and-provide-TxCap-blobs.patch
        8034-brcmfmac-common-Add-support-for-external-calibration.patch)
sha256sums=('SKIP'
            'cb2d729cc20743014d9e3bd08facb9f5bdd19d9fa89014f415c61b4a6eb78e97'
            '986f8d802f37b72a54256f0ab84da83cb229388d58c0b6750f7c770818a18421'
            'b89188b1bc3516d54965dd36def6a2af3d81379e53ff7e527bbd91f77c6f191b'
            'f0eaa81deb5428c41d2f0b09e79a2860931e4a48a368e965172150a20fa2fa62'
            '7823d7488f42bc4ed7dfae6d1014dbde679d8b862c9a3697a39ba0dae5918978'
            '5e804e1f241ce542f3f0e83d274ede6aa4b0539e510fb9376f8106e8732ce69b'
            '365d4225a7db60bd064ebbc34ce0ae582a0c378ad6c4cec7960a5ae4641a6757'
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
            '862f631ef9f25453ce38d9ed0197e62d85f9f5a0625ed77237e643297fb42f75'
            '2f7899b70d5c55aea3f6385385fea01ce21b48f9441982a94f36c842cceec083'
            '2b126cda3863f49b8d3a6de8fa8cca979d87bd9e66812531be5c02c9e5840d82'
            '70a277c9ad4fba624b3916e397624e557135b269c34eb704ace29aa1a6b8e430'
            '42ae52b93ea0cbd0d1859512b88e0c290e3500b8e52f8de3be7398cb6039d0b4'
            '300d926bac23b81d267e73433d668581ec1e3b12fa76462ba3d0b1cf2728b82d'
            '01f3185e551dd49007b533d4bae37774131820a51715e1f1a391220e055afc66'
            'db55305b8e3c2a8fa0a85aeaad661717ae745d5dabc7735221adb184e89a2d1b'
            '82f679f3736e09ee9ea8a8b53c052e84bb40df8a05f21a2082224184ad3cf162'
            '9907f67d099a2b6243747350a2c057d82c39e822107ca57cbfdc32baf378d2cb'
            'd25cd32de8c74ba8bcb430c21f9d84deae1174594d00ea94e1fd1e2ab70ea5cb'
            '823d35349844605dadf381ae7c6097379a23c72da59e3cf393fcf3e5d466dafd'
            'ed6e84bc03cd6adfc3f8def843f150b71470df6d6a88fc348d5e1b36f133f424'
            '23d9018c90d02389f2ddeb0821e581d354184b3b38d4488fbc0f3363463a0c9e'
            'd2e2b0f0c80fb5b4da36d3a7a87b10c2419255c0e38e0faa1d7478eaab1b9a35'
            'ecef58f944bf61950b3211e88acd104b0006a177e76f59a47b8253aaf5e6acc6'
            '1eb6e14b5504efbad7911aabc801a265e9ba13cb2fd6ce8e029af55bf97cec86'
            'f2b553e11240bb88e5d0ffd7883d808c069ede544e5c578c22975466a5c9d26a'
            'ac4b200dadbb88179bf37dcea280efe25bf42b420a90ab1399c3bd9c7905f592'
            'e12726162b868435081a215f04d921cd8b9307de71738c41090ec93a267725de'
            'bfa3bb8d16b6c26831f9b5e833d46ea2c60854f016540a051f96c418be1a728f'
            'e9df13adedefd0043ea6678c19a9de608aa69fe83929a13213c528052096ed3c'
            'b51a916bb0048d7cb57ed2afc25394ec72664efe2a8c5705b0dcfe62384e34ed'
            '2ec5dddd41327b5018d41b920955182bc3f220f692a32b061d8797c8fee99dbc'
            'a8596e6180a895515cbc1f361edc8fca460f630dd15bbd161037d84717717ba8'
            '55b6981468b489f5bb7c59d5f9a6b479c0d96bb1018efa209ed8506d54de8399'
            '2339acd32f020db66f2a3190910d925a030798e3fd57006a09dda56e5acbf279'
            'f41ab41dd9445dee28699c1af7909723514f9d41d30a5c148d4f99617ed2d46e'
            '0e6cd10376f13873a9226d233161a0dab6b1d3c6a7d66bc3c4e8d3cc0f0397d0'
            '8f9a6d47eaec7d9df9a822a146ab15ca7bee906866545493cac8621570237060'
            'ecede30aa68ea4646d3efb0a7190466ff1784f4e93756a04bb58756536f28035'
            '0bed877897873ae86e512d711b86fa11adc5b8e7fe35139e290e8d0a0133f6a5'
            '23f4a7002632f95abb1ed75a4df0570b7a81e5cf4067a16da7101b16eb582a01')

prepare() {
  cd "kernel-t2-v5.16.7"

  # add upstream patch
  # msg "add upstream patch"
  # patch -p1 -i "../patch-${pkgver}"

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

  msg "don't run depmod on 'make install'"
  # We'll do this ourselves in packaging
  sed -i '2iexit 0' scripts/depmod.sh

  msg "get kernel version"
  make prepare

  msg "rewrite configuration"
  yes "" | make config >/dev/null
}

build() {
  cd "kernel-t2-v5.16.7"

  msg "build"
  make -${MAKEFLAGS} LOCALVERSION= bzImage modules
}

package_linux516-t2() {
  pkgdesc="The ${pkgbase/linux/Linux} kernel and modules"
  depends=('coreutils' 'linux-firmware' 'kmod' 'mkinitcpio>=27')
  optdepends=('crda: to set the correct wireless channels of your country')
  provides=("linux=${pkgver}" VIRTUALBOX-GUEST-MODULES WIREGUARD-MODULE)

  cd "kernel-t2-v5.16.7"

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

package_linux516-t2-headers() {
  pkgdesc="Header files and scripts for building modules for ${pkgbase/linux/Linux} kernel"
  depends=('gawk' 'python' 'libelf' 'pahole')
  provides=("linux-headers=$pkgver")

  cd "kernel-t2-v5.16.7"
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
