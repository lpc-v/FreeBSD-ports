PORTNAME=	fossil
PORTVERSION=	2.18
DISTVERSIONPREFIX=	src-
PORTREVISION=	0
PORTEPOCH=	2
CATEGORIES=	devel www
MASTER_SITES=	https://fossil-scm.org/home/tarball/version-${PORTVERSION}/

MAINTAINER=	gahr@FreeBSD.org
COMMENT=	DSCM with built-in wiki, http interface and server, tickets database

LICENSE=	BSD2CLAUSE
LICENSE_FILE=	${WRKSRC}/COPYRIGHT-BSD2.txt

USES=		cpe ssl

WRKSRC=		${WRKDIR}/${PORTNAME}-src-${PORTVERSION}

CPE_VENDOR=	fossil-scm
HAS_CONFIGURE=	yes
CONFIGURE_ARGS=	--prefix=${PREFIX} --with-openssl=${OPENSSLBASE}
USE_RC_SUBR=	fossil
MAKE_JOBS_UNSAFE=yes
MAKE_ENV=	TCLSH=${TCLSH}

PLIST_FILES=	bin/fossil man/man1/fossil.1.gz

OPTIONS_DEFINE=	JSON FUSE STATIC TH1HOOKS TCL
OPTIONS_DEFAULT=JSON
JSON_DESC=	JSON API support
FUSE_DESC=	Enable fossil fusefs command
TH1HOOKS_DESC=	Enable TH1 command and web page hooks
TCL_DESC=	Enable Tcl integration

JSON_CONFIGURE_ON=	--json
STATIC_CONFIGURE_ON=	--static
STATIC_LDFLAGS=		-pthread
FUSE_CONFIGURE_OFF=	--disable-fusefs
TH1HOOKS_CONFIGURE_ON=	--with-th1-hooks
TCL_CONFIGURE_ON=	--with-tcl-stubs --with-tcl=${TCL_LIBDIR}
TCL_USES=		tcl
TCL_CFLAGS=		-DTCL_LIBRARY_NAME=\\\"libtcl${TCL_SHLIB_VER}.so\\\" \
			-DTCL_MINOR_OFFSET=7
FUSE_LIB_DEPENDS=	libfuse.so:sysutils/fusefs-libs
FUSE_USES=		localbase:ldflags

post-patch-FUSE-on:
	@${REINPLACE_CMD} -e 's/define-append LIBS -lfuse/& -pthread/' ${WRKSRC}/auto.def

post-install:
	@${STRIP_CMD} ${STAGEDIR}${PREFIX}/bin/fossil
	${INSTALL_MAN} ${WRKSRC}/fossil.1 ${STAGEDIR}${MANPREFIX}/man/man1

.include <bsd.port.mk>
