# Created by: Sunpoet Po-Chuan Hsieh <sunpoet@FreeBSD.org>

PORTNAME=	grib_api
PORTVERSION=	1.28.0
DISTVERSIONSUFFIX=	-Source
PORTREVISION=	5
CATEGORIES=	science
MASTER_SITES=	https://confluence.ecmwf.int/download/attachments/3473437/ \
		LOCAL/sunpoet

MAINTAINER=	sunpoet@FreeBSD.org
COMMENT=	ECMWF API for WMO FM-92 GRIB messages

LICENSE=	APACHE20
LICENSE_FILE=	${WRKSRC}/LICENSE

LIB_DEPENDS=	libnetcdf.so:science/netcdf \
		libpng.so:graphics/png

CONFLICTS_INSTALL=	eccodes

OPTIONS_SINGLE=	JPEG
OPTIONS_SINGLE_JPEG=	JASPER OPENJPEG
OPTIONS_DEFAULT=OPENJPEG

PORTSCOUT=	site:https://software.ecmwf.int/wiki/display/GRIB/Releases

USES=		libtool pathfix

CONFIGURE_ARGS=	--enable-pthread --with-netcdf=${LOCALBASE} --with-png-support
GNU_CONFIGURE=	yes
INSTALL_TARGET=	install-strip
USE_LDCONFIG=	yes

JASPER_CONFIGURE_ON=	--with-jasper=${LOCALBASE}
JASPER_LIB_DEPENDS=	libjasper.so:graphics/jasper
OPENJPEG_CFLAGS=	-I${LOCALBASE}/include/openjpeg-1.5
OPENJPEG_CONFIGURE_ON=	--with-openjpeg=${LOCALBASE}
OPENJPEG_LIB_DEPENDS=	libopenjpeg.so:graphics/openjpeg15

post-install:
	${INSTALL_SCRIPT} ${WRKSRC}/tools/grib1to2 ${STAGEDIR}${PREFIX}/bin/grib1to2

.include <bsd.port.mk>
