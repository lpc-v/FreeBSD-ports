PORTNAME=	endlessh
PORTVERSION=	1.1
PORTREVISION=	1
CATEGORIES=	net

MAINTAINER=	brnrd@FreeBSD.org
COMMENT=	SSH tarpit

LICENSE=	UNLICENSE
LICENSE_FILE=	${WRKSRC}/UNLICENSE

USE_RC_SUBR=	endlessh

USE_GITHUB=	yes
GH_ACCOUNT=	skeeto

PLIST_FILES=	bin/endlessh \
		man/man1/endlessh.1.gz \
		"@sample ${PREFIX}/etc/endlessh.conf.sample" \
		${PREFIX}/etc/endlessh.newsyslog.conf

SUB_FILES=	pkg-message

post-patch:
	${REINPLACE_CMD} 's|share/man|man|;s|/usr/local|${PREFIX}|' ${WRKSRC}/Makefile
	${REINPLACE_CMD} 's|/etc/endlessh/config|${PREFIX}/etc/endlessh.conf|' \
		${WRKSRC}/endlessh.c ${WRKSRC}/endlessh.1

post-install:
	${INSTALL_DATA} ${FILESDIR}/endlessh.newsyslog.conf \
		${FILESDIR}/endlessh.conf.sample ${STAGEDIR}${PREFIX}/etc/
	${STRIP_CMD} ${STAGEDIR}${PREFIX}/bin/endlessh

.include <bsd.port.mk>
