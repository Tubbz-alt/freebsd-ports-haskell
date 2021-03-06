# $FreeBSD$

PORTNAME=	libappindicator
PORTVERSION=	${MAJOR_VER}.${SNAPSHOT_VER:S/.//g}.${PATCH_VER:S/ubuntu//}
CATEGORIES=	devel
MASTER_SITES=	http://archive.ubuntu.com/ubuntu/pool/main/liba/${PORTNAME}/
DISTNAME=	${PORTNAME}_${MAJOR_VER}+${SNAPSHOT_VER}.orig

PATCH_SITES=		${MASTER_SITES}
PATCHFILES=		${PORTNAME}_${MAJOR_VER}+${SNAPSHOT_VER}-${PATCH_VER}.diff.gz
PATCH_DIST_STRIP=	-p1

MAINTAINER=	tagattie@yandex.com
COMMENT=	KSNI App Indicator library

LICENSE=	LGPL21+
LICENSE_FILE=	${WRKSRC}/COPYING

BUILD_DEPENDS=	gnome-autogen.sh:devel/gnome-common \
		gtkdocize:textproc/gtk-doc
LIB_DEPENDS=	libdbus-glib-1.so:devel/dbus-glib \
		libdbusmenu-gtk3.so:devel/libdbusmenu

USES=		autoreconf:build gmake gnome libtool pkgconfig
USE_LDCONFIG=	yes
USE_GNOME=	cairo gdkpixbuf2 gtk30

OPTIONS_DEFINE=		VAPI
OPTIONS_DEFAULT=	VAPI
OPTIONS_SUB=		yes

VAPI_BUILD_DEPENDS=	vala>=0:lang/vala
VAPI_CONFIGURE_ENV_OFF=	ac_cv_path_VALA_API_GEN= \
			ac_cv_path_VALAC=
VAPI_VARS=		EXTRA_PATCHES+=${PATCHDIR}/extra-patch-bindings_vala_examples_Makefile.am

NO_WRKSUBDIR=	yes

GNU_CONFIGURE=	yes
CONFIGURE_ARGS=	--enable-gtk-doc \
		--with-gtk=3
INSTALL_TARGET=	install-strip

MAJOR_VER=	12.10.1
SNAPSHOT_VER=	18.04.20180322.1
PATCH_VER=	0ubuntu5

pre-configure:
	cd ${WRKSRC} && ${SETENV} NOCONFIGURE=yes ${SH} ./autogen.sh

.include <bsd.port.mk>
