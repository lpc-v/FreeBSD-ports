PORTNAME=	rset
PORTVERSION=	2.4
CATEGORIES=	sysutils
MASTER_SITES=	https://scriptedconfiguration.org/code/

MAINTAINER=	sunpoet@FreeBSD.org
COMMENT=	Configure systems using using any scripting language

LICENSE=	ISCL
LICENSE_FILE=	${WRKSRC}/LICENSE

HAS_CONFIGURE=	yes
MAKE_ARGS=	MANPREFIX=${PREFIX}/share/man
TEST_TARGET=	TEST

post-install:
	${STRIP_CMD} ${STAGEDIR}${PREFIX}/bin/miniquark ${STAGEDIR}${PREFIX}/bin/rset

.include <bsd.port.mk>
