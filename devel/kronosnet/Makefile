# Created by: David Shane Holden <dpejesh@yahoo.com>

PORTNAME=	kronosnet
PORTVERSION=	1.24
CATEGORIES=	devel
MASTER_SITES=	https://kronosnet.org/releases/

MAINTAINER=	egypcio@FreeBSD.org
COMMENT=	Network abstraction layer designed for high availability

LICENSE=	GPLv2

LIB_DEPENDS=	liblzo2.so:archivers/lzo2 \
		liblz4.so:archivers/liblz4 \
		libnspr4.so:devel/nspr \
		libnss3.so:security/nss \
		libqb.so:devel/libqb \
		libzstd.so:archivers/zstd

USES=		autoreconf gmake localbase libtool pkgconfig ssl
USE_BINUTILS=	yes
USE_GCC=	yes
USE_LDCONFIG=	yes
GNU_CONFIGURE=	yes
LDFLAGS+=	-B${LOCALBASE}/bin

INSTALL_TARGET=	install-strip
TEST_TARGET=	check

OPTIONS_DEFINE=	MANPAGES DOCS
OPTIONS_DEFAULT=MANPAGES
OPTIONS_SUB=	yes

MANPAGES_BUILD_DEPENDS=		doxygen:devel/doxygen
MANPAGES_CONFIGURE_ENABLE=	man

.include <bsd.port.options.mk>

.if ${SSL_DEFAULT} == base
CONFIGURE_ENV=	openssl_CFLAGS="-I/usr/include" openssl_LIBS="-lcrypto"
.endif

.include <bsd.port.mk>
