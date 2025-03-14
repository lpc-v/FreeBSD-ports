# Created by: Xin Li <delphij@FreeBSD.org>

PORTNAME=	lmdb
PORTVERSION=	0.9.29
PORTREVISION=	1
DISTVERSIONPREFIX=	${PORTNAME:tu}_
PORTEPOCH=	1
CATEGORIES=	databases

MAINTAINER=	delphij@FreeBSD.org
COMMENT=	OpenLDAP Lightning Memory-Mapped Database

LICENSE=	OPENLDAP
LICENSE_NAME=	OpenLDAP Public License
LICENSE_FILE=	${WRKSRC}/LICENSE
LICENSE_PERMS=	dist-mirror dist-sell pkg-mirror pkg-sell auto-accept

WRKSRC_SUBDIR=		libraries/liblmdb
MAKE_ARGS+=	CC="${CC}"
MAKE_ARGS+=	prefix="${PREFIX}" INSTALL_PROGRAM="${INSTALL_PROGRAM}"
MAKE_ARGS+=	INSTALL_LIB="${INSTALL_LIB}" INSTALL_DATA="${INSTALL_DATA}" INSTALL_MAN="${INSTALL_MAN}"

USE_LDCONFIG=	yes

USE_GITHUB=	yes
GH_ACCOUNT=	${PORTNAME:tu}

SUB_FILES+=	lmdb.pc
SUB_LIST+=	PORTVERSION=${PORTVERSION}

post-install:
	${LN} -sf liblmdb.so.0 ${STAGEDIR}${PREFIX}/lib/liblmdb.so
	${INSTALL_DATA} ${WRKDIR}/lmdb.pc ${STAGEDIR}${PREFIX}/libdata/pkgconfig

do-test:
	${MKDIR} ${WRKSRC}/testdb
	cd ${WRKSRC} && ./mtest*

.include <bsd.port.mk>
