PORTNAME=	libretro-virtualjaguar
PORTVERSION=	0.20220304
CATEGORIES=	games

MAINTAINER=	dmenelkir@gmail.com
COMMENT=	Port of Virtual Jaguar to Libretro

LICENSE=	GPLv3

USES=		compiler:c++11-lib gmake
USE_LDCONFIG=	yes

USE_GITHUB=	yes
GH_ACCOUNT=	libretro
GH_PROJECT=	virtualjaguar-libretro
GH_TAGNAME=	263c979

PLIST_FILES=	lib/libretro/virtualjaguar_libretro.so

do-install:
	${MKDIR} ${STAGEDIR}/${PREFIX}/lib/libretro;
	${INSTALL_LIB} ${WRKSRC}/virtualjaguar_libretro.so ${STAGEDIR}/${PREFIX}/lib/libretro;

.include <bsd.port.mk>
