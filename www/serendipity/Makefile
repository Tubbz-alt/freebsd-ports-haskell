# Created by: babak@farrokhi.net
# $FreeBSD$

PORTNAME=	serendipity
PORTVERSION=	2.1.4
PORTREVISION=	1
CATEGORIES=	www
MASTER_SITES=	SF/php-blog/${PORTNAME}/${PORTVERSION}

MAINTAINER=	joneum@FreeBSD.org
COMMENT=	PHP based weblog software

LICENSE=	BSD3CLAUSE
LICENSE_FILE=	${WRKSRC}/docs/LICENSE

WRKSRC=		${WRKDIR}/${PORTNAME}
NO_BUILD=	YES
SERENDIPITY?=	www/${PORTNAME}
PLIST_SUB+=	WWWOWN="${WWWOWN}" WWWGRP="${WWWGRP}"
USE_PHP=	session pcre gd openssl mbstring iconv zlib xml
SUB_FILES=	pkg-message
USES=		cpe php tar:bzip2
CPE_VENDOR=	s9y

OPTIONS_DEFINE=	MYSQL PGSQL SQLITE MAGICK
OPTIONS_DEFAULT=	MYSQL MAGICK

MYSQL_USE=	PHP=mysqli
PGSQL_USE=	PHP=pgsql
SQLITE_USE=	PHP=sqlite3
MAGICK_RUN_DEPENDS+=	convert:graphics/ImageMagick6

do-install:
	@-${MKDIR} ${STAGEDIR}${PREFIX}/${SERENDIPITY}
	@${CHMOD} 755 ${STAGEDIR}${PREFIX}/${SERENDIPITY}
	@(cd ${WRKSRC} && ${CP} -R * ${STAGEDIR}${PREFIX}/${SERENDIPITY}/ )

.include <bsd.port.mk>
