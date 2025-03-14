# Created by: Michael Nottebrock <lofi@FreeBSD.org>

PORTNAME=	pinentry
PORTVERSION=	1.2.0
PORTREVISION?=	1
CATEGORIES=	security
MASTER_SITES=	GNUPG/pinentry

MAINTAINER=	jhale@FreeBSD.org
COMMENT?=	Collection of simple PIN or passphrase entry dialogs

LICENSE=	GPLv2+
LICENSE_FILE=	${WRKSRC}/COPYING

USES=		tar:bzip2

.if !defined(PINENTRY_GUI)
INFO=		pinentry
NO_ARCH=	yes
NO_BUILD=	yes
PLIST_FILES=	bin/pinentry

OPTIONS_SINGLE=	FRONTEND
OPTIONS_SINGLE_FRONTEND=	EFL FLTK GNOME GTK2 NCURSES QT5 TTY
OPTIONS_DEFAULT=	NCURSES

FRONTEND_DESC=	Default frontend

TTY_DESC=	Console version
PINENTRY_TTY=	pinentry-tty
TTY_RUN_DEPENDS=	${PINENTRY_TTY}:security/pinentry-tty

NCURSES_DESC=	Curses frontend
PINENTRY_NCURSES=	pinentry-curses
NCURSES_RUN_DEPENDS=	${PINENTRY_NCURSES}:security/pinentry-curses

EFL_DESC=	EFL frontend
PINENTRY_EFL=	pinentry-efl
EFL_RUN_DEPENDS=	${PINENTRY_EFL}:security/pinentry-efl

FLTK_DESC=	FLTK frontend
PINENTRY_FLTK=	pinentry-fltk
FLTK_RUN_DEPENDS=	${PINENTRY_FLTK}:security/pinentry-fltk

GTK2_DESC=	Gtk+ 2 frontend
PINENTRY_GTK2=	pinentry-gtk-2
GTK2_RUN_DEPENDS=	${PINENTRY_GTK2}:security/pinentry-gtk2

QT5_DESC=	Qt 5 frontend
PINENTRY_QT5=	pinentry-qt5
QT5_RUN_DEPENDS=	${PINENTRY_QT5}:security/pinentry-qt5

GNOME_DESC=	GNOME frontend
PINENTRY_GNOME=	pinentry-gnome3
# Due to a dependency loop that exists between security/pinentry-gnome,
# security/gcr, security/gnupg and security/pinentry, the user must install
# pinentry-gnome manually. See pkg-message.gnome for more details.
#GNOME_RUN_DEPENDS=	${PINENTRY_GNOME}:security/pinentry-gnome
GNOME_VARS=		PKGMESSAGE+=${.CURDIR}/pkg-message.gnome

.include <bsd.port.options.mk>

.for gui in ${OPTIONS_SINGLE_FRONTEND}
. if ${PORT_OPTIONS:M${gui}}
PINENTRY_BIN=	${PINENTRY_${gui}}
. endif
.endfor

do-install:
	${LN} -sf ${PINENTRY_BIN} ${STAGEDIR}${PREFIX}/bin/pinentry
	${INSTALL_DATA} ${WRKSRC}/doc/pinentry.info ${STAGEDIR}${PREFIX}/${INFO_PATH}

.else # !defined(PINENTRY_GUI)
PKGNAMESUFFIX=	-${PINENTRY_GUI}
LIB_DEPENDS=	libassuan.so:security/libassuan \
		libgpg-error.so:security/libgpg-error

USES+=		gmake iconv localbase ncurses pkgconfig
GNU_CONFIGURE=	yes
CONFIGURE_ARGS=	--disable-pinentry-emacs
LDFLAGS+=	-Wl,--as-needed

OPTIONS_DEFINE=	LIBSECRET

LIBSECRET_DESC=	Saving the passphrase with libsecret
LIBSECRET_CONFIGURE_ENABLE=	libsecret
LIBSECRET_LIB_DEPENDS=	libsecret-1.so:security/libsecret
LIBSECRET_USES=		gnome
LIBSECRET_USE=		GNOME=glib20

.if ${PINENTRY_GUI} == "gnome"
OPTIONS_SLAVE=	LIBSECRET
LIB_DEPENDS+=	libgcr-base-3.so:security/gcr
PLIST_FILES=	bin/pinentry-gnome3
.else
CONFIGURE_ARGS+=--disable-pinentry-gnome3
.endif

.if ${PINENTRY_GUI} == "qt5"
USES+=		compiler:c++11-lib qt:5
USE_QT=		core gui widgets buildtools_build
PLIST_FILES=	bin/pinentry-qt5
CONFIGURE_ARGS+=--enable-pinentry-qt5 \
		--program-suffix=5
.else
CONFIGURE_ARGS+=--disable-pinentry-qt --disable-pinentry-qt5
.endif

.if ${PINENTRY_GUI} == "gtk2"
USES+=		gnome
USE_GNOME+=	gtk20
PLIST_FILES=	bin/pinentry-gtk-2
.else
CONFIGURE_ARGS+=--disable-pinentry-gtk2
.endif

.if ${PINENTRY_GUI} == "efl"
LIB_DEPENDS+=	libefl.so:devel/efl
PLIST_FILES=	bin/pinentry-efl
.else
CONFIGURE_ARGS+=--disable-pinentry-efl
.endif

.if ${PINENTRY_GUI} == "fltk"
USES+=		compiler:c++11-lib
LIB_DEPENDS+=	libfltk.so:x11-toolkits/fltk
PLIST_FILES=	bin/pinentry-fltk
.else
CONFIGURE_ARGS+=--disable-pinentry-fltk
.endif

.if ${PINENTRY_GUI} == "curses"
PLIST_FILES=	bin/pinentry-curses
.else
CONFIGURE_ARGS+=--disable-pinentry-curses
.endif

.if ${PINENTRY_GUI} == "tty"
PLIST_FILES=	bin/pinentry-tty
CONFIGURE_ARGS+=--enable-pinentry-tty
.else
CONFIGURE_ARGS+=--disable-pinentry-tty
.endif

post-install:
	${RM} ${STAGEDIR}${PREFIX}/bin/pinentry \
		${STAGEDIR}${PREFIX}/share/info/pinentry.info

.endif # !defined(PINENTRY_GUI)

.include <bsd.port.mk>
