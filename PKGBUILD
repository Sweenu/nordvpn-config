# Maintainer: Bruno Inec <brunoinec at gmail dot com>
pkgname=nordvpn-config
pkgver=1.0
pkgrel=1
pkgdesc="NordVPN config files (with 'auth-user-pass login.key')"
arch=(x86_64)
url="https://nordvpn.com"
source_x86_64=("https://downloads.nordcdn.com/configs/archives/servers/ovpn.zip")
sha256sums_x86_64=(SKIP)

package(){
    local LISTFILES="ls -d ${srcdir}/ovpn_tcp/* ${srcdir}/ovpn_udp/*"
    ${LISTFILES} | xargs sed -i 's/auth-user-pass/auth-user-pass login.key/'
    while read file; do
        local dest=$(basename ${file} | sed -e 's/.nordvpn.com//' -e 's/ovpn/conf/')
        install -Dm600 "${file}" "${pkgdir}/etc/openvpn/client/${dest}"
    done < <(${LISTFILES})
}
