# Maintainer: Sizhao LIU <sizhaoliu@talend.com>

pkgname="talend-open-studio-dq"
_altname="Talend Open Studio for Data Quality"
_shortname="TOS_DQ"
_altshortname="top"
pkgver="5.4.1"
_build="r111943"
pkgrel=1
pkgdesc="Open-source data quality software from Talend."
arch=('i686' 'x86_64')
url=("http://www.talend.com")
license=("GPL2")
depends=("gtk2" "glib2")
options=("!strip")

# Choose your prefered site, default value is US.
_hostsite=("http://talend.dreamhosters.com") # US server
#_hostsite=("download-mirror1.talend.com") # Europe server

source=("${_hostsite}/top/release/V${pkgver}/${_shortname}-${_build}-V${pkgver}.zip" 
	"${_shortname// /}.desktop")
md5sums=("030a12dbd7f7552c3ced627dc59433ad"
	"bea0da50b6e281f704de4b3bc735fc02")

build(){
	
    install -dm755 ${pkgdir}/opt ${pkgdir}/usr/bin ${pkgdir}/usr/share/applications || return 1    
    
    # Remove all non-Linux startup scripts   
    cd ${srcdir}/${_shortname}-${_build}-V${pkgver} &&
    rm -rf  *macosx* *solaris* *gtk-ppc* *win* || return 1
  
    cp -Rp ${srcdir}/${_shortname}-${_build}-V${pkgver} ${pkgdir}/opt/${_shortname}-${_build}-V${pkgver} || return 1

    # Link application icon
    ln -s /opt/${_shortname}-${_build}-V${pkgver}/plugins/org.talend.rcp.branding.${_altshortname}_${pkgver}.${_build}/icons/appli_32x32.gif ${pkgdir}/opt/${_shortname}-${_build}-V${pkgver}/icon.gif

    # Link executable based on architecture
    install -m 0755 ${srcdir}/${_shortname// /}.desktop ${pkgdir}/usr/share/applications/ || return 1
    
    ln -s /opt/${_shortname}-${_build}-V${pkgver}/${_shortname// /}-linux-gtk-${CARCH//i6/x} ${pkgdir}/usr/bin/${pkgname} || return 1
    chmod +x ${pkgdir}/opt/${_shortname}-${_build}-V${pkgver}/${_shortname// /}-linux-gtk-${CARCH//i6/x} || return 1      
  }
