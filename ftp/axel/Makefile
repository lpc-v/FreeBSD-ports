# Created by: ijliao

PORTNAME=	axel
PORTVERSION=	2.4
PORTREVISION=	2
CATEGORIES=	ftp
MASTER_SITES=	http://pkgs.fedoraproject.org/repo/pkgs/axel/axel-2.4.tar.gz/a2a762fce0c96781965c8f9786a3d09d/

MAINTAINER=	prudhvi-krishna-bsd@surapaneni.in
COMMENT=	Download accelerator

DEPRECATED=	Last release in 2009 and dead upstream, please consider using www/aria2
EXPIRATION_DATE=2022-06-30


USES=		cpe gmake
HAS_CONFIGURE=	yes
CONFIGURE_ARGS=	--prefix=${PREFIX} --mandir=${MANPREFIX}/man

CPE_VENDOR=	axel_project

OPTIONS_DEFINE=	NLS DEBUG
OPTIONS_SUB=	yes

NLS_USES=	gettext iconv
NLS_CONFIGURE_ON=	--i18n=1
NLS_CONFIGURE_OFF=	--i18n=0
DEBUG_CONFIGURE_ON=--debug=1 --strip=0

post-configure:
	@${REINPLACE_CMD} -e 's|gcc|${CC}|' ${WRKSRC}/Makefile.settings

.include <bsd.port.mk>
