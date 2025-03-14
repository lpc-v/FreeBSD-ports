# Created by: Nicola Vitale <nivit@email.it>

PORTNAME=	morla
PORTVERSION=	0.16.1
PORTREVISION=	12
CATEGORIES=	editors textproc
MASTER_SITES=	http://www.morlardf.net/src/ \
		http://nivi.interfree.it/distfiles/${PORTNAME}/${PORTVERSION}/

MAINTAINER=	nivit@FreeBSD.org
COMMENT=	RDF editor

LIB_DEPENDS=	libnxml.so:textproc/libnxml \
		librdf.so:textproc/redland \
		libraptor2.so:textproc/raptor2 \
		libcurl.so:ftp/curl
BUILD_DEPENDS=	dot:graphics/graphviz
RUN_DEPENDS=	dot:graphics/graphviz

OPTIONS_DEFINE=	XULRUNNER
XULRUNNER_DESC=	Xulrunner as JavaScript engine

GNU_CONFIGURE=	yes
CPPFLAGS+=	-I${LOCALBASE}/include
LDFLAGS+=	-L${LOCALBASE}/lib
CONFIGURE_ARGS=	--with-gconf=none --with-gtkhtml=none
USES=		gettext gnome libtool pkgconfig
USE_GNOME=	libxslt gtk20
USE_LDCONFIG=	${PREFIX}/lib/${PORTNAME}

DESKTOP_ENTRIES="morla" \
		"Edit RDF documents" \
		"${DATADIR}/icons/128_color.png" \
		"morla" \
		"WebDevelopment;" \
		true

XULRUNNER_BROKEN=	www/libxul is gone, consider using lang/spidermonkey*
XULRUNNER_CONFIGURE_ON=	--with-javascript=xulrunner
XULRUNNER_CONFIGURE_OFF=	--with-javascript=none

post-patch:
	@${REINPLACE_CMD} -e 's|-D.*_DISABLE_DEPRECATED||g' \
		${WRKSRC}/configure

.include <bsd.port.mk>
