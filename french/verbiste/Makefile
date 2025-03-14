# Created by: Dan Phillips <dan-ports@dp.id.au>

PORTNAME=	verbiste
PORTVERSION=	0.1.47
PORTREVISION=	2
CATEGORIES=	french education textproc
MASTER_SITES=	http://sarrazip.com/dev/

MAINTAINER=	dereckson@gmail.com
COMMENT=	French verb conjugator/deconjugator

LICENSE=	GPLv2

USES=		gnome pathfix pkgconfig iconv:wchar_t libtool shebangfix
USE_GNOME=	libxml2
USE_LDCONFIG=	yes

GNU_CONFIGURE=	yes
INSTALL_TARGET=	install-strip
SHEBANG_FILES=	${WRKSRC}/examples/*.pl

CPPFLAGS+=	-I${LOCALBASE}/include
LDFLAGS+=	-L${LOCALBASE}/lib

TEST_TARGET=	check

OPTIONS_DEFINE=	GTK2 DOCS EXAMPLES

CONFIGURE_ARGS=	--without-gnome-app --without-gnome-applet

.include <bsd.port.options.mk>

.if ${PORT_OPTIONS:MGTK2}
USE_GNOME+=	cairo gdkpixbuf2 gtk20
LIB_DEPENDS+=	libfontconfig.so:x11-fonts/fontconfig \
		libfreetype.so:print/freetype2
PLIST_SUB+=	HASGTK=""
.else
CONFIGURE_ARGS+=--without-gtk-app
PLIST_SUB+=	HASGTK="@comment "
.endif

.if ${PORT_OPTIONS:MGTK2}
USES+=		gettext
PLIST_SUB+=	HASGUI=""
.else
PLIST_SUB+=	HASGUI="@comment "
.endif

post-install:
	${MKDIR} ${STAGEDIR}${EXAMPLESDIR}
.for f in README *.java *.c
	${INSTALL_DATA} ${WRKSRC}/examples/${f} ${STAGEDIR}${EXAMPLESDIR}
.endfor
	${INSTALL_SCRIPT} ${WRKSRC}/examples/*.pl ${STAGEDIR}${EXAMPLESDIR}

.include <bsd.port.mk>
