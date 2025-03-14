# Created by: Sunpoet Po-Chuan Hsieh <sunpoet@FreeBSD.org>

PORTNAME=	libzen
PORTVERSION=	22.06
CATEGORIES=	multimedia
MASTER_SITES=	https://mediaarea.net/download/binary/mediainfo/${PORTVERSION}/ \
		LOCAL/sunpoet
DISTNAME=	MediaInfo_CLI_${PORTVERSION}_GNU_FromSource

MAINTAINER=	sunpoet@FreeBSD.org
COMMENT=	ZenLib used by MediaInfo and its library

LICENSE=	ZLIB
LICENSE_FILE=	${WRKSRC}/../../../License.txt

USES=		compiler:c++11-lang libtool pathfix tar:xz

CONFIGURE_ARGS=	--enable-shared --enable-static
GNU_CONFIGURE=	yes
INSTALL_TARGET=	install-strip
USE_CXXSTD=	c++11
USE_LDCONFIG=	yes

WRKSRC=		${WRKDIR}/MediaInfo_CLI_GNU_FromSource/ZenLib/Project/GNU/Library

post-patch:
	@${REINPLACE_CMD} -e '/^ZenLib_LIBS/ s|$$(pwd)[^ ]*|${LOCALBASE}/lib|' ${WRKSRC}/configure
	@${REINPLACE_CMD} -e 's| -lstdc++||g' ${WRKSRC}/configure ${WRKSRC}/libzen.pc.in

post-install:
	${INSTALL_DATA} ${WRKSRC}/../../../Source/ZenLib/BitStream_Fast.h ${STAGEDIR}${PREFIX}/include/ZenLib/BitStream_Fast.h

.include <bsd.port.mk>
