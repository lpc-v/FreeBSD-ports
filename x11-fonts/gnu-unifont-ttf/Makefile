PORTNAME=	unifont
PORTVERSION=	14.0.04
PORTEPOCH=	1
CATEGORIES=	x11-fonts
MASTER_SITES=	GNU/unifont/unifont-${PORTVERSION}
PKGNAMEPREFIX=	gnu-
PKGNAMESUFFIX=	-ttf
DISTFILES=	${FONTFILES:S|$|-${PORTVERSION}${FONTSUFFIX}|}
EXTRACT_ONLY=	# empty

MAINTAINER=	sunpoet@FreeBSD.org
COMMENT=	GNU Unicode TrueType font

LICENSE=	GPLv2+

USES=		fonts

NO_ARCH=	yes
NO_BUILD=	yes

FONTSDIR=	${PREFIX}/share/fonts/gnu-unifont-ttf
PLIST_FILES=	${FONTFILES:S|^|${FONTSDIR}/|:S|$|${FONTSUFFIX}|}

FONTFILES=	unifont unifont_csur unifont_upper
FONTSUFFIX=	.ttf

do-install:
	${MKDIR} ${STAGEDIR}${FONTSDIR}
.for i in ${FONTFILES}
	${INSTALL_DATA} ${DISTDIR}/${i}-${PORTVERSION}${FONTSUFFIX} ${STAGEDIR}${FONTSDIR}/${i}${FONTSUFFIX}
.endfor

.include <bsd.port.mk>
