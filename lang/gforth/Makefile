# Created by: Cyrille Lefevre <clefevre@citeweb.net>

PORTNAME=	gforth
PORTVERSION=	0.7.3
PORTREVISION=	14
CATEGORIES=	lang
MASTER_SITES=	http://www.complang.tuwien.ac.at/forth/gforth/ \
		GNU

MAINTAINER=	danfe@FreeBSD.org
COMMENT=	Fast and portable Forth system

LICENSE=	GPLv3+
LICENSE_FILE=	${WRKSRC}/COPYING

LIB_DEPENDS=	libavcall.so:devel/libffcall \
		libffi.so:devel/libffi \
		libltdl.so:devel/libltdl

USES=		gmake libtool:build localbase makeinfo
USE_GCC=	yes
USE_LDCONFIG=	${PREFIX}/lib/gforth/${PORTVERSION}/libcc-named

GNU_CONFIGURE=	yes
CONFIGURE_ENV=	GFORTHHIST=${WRKSRC}
MAKE_ENV=	GFORTHHIST=${WRKSRC}
ALL_TARGET=	kernel/version.fs more info
MAKE_JOBS_UNSAFE=yes

STRIP=		#none

PLIST_SUB=	PORTVERSION=${PORTVERSION} \
		WORDSIZE=${WORDSIZE} BYTEORDER=${BYTEORDER}

PORTDOCS=	AUTHORS BUGS Benchres COPYING COPYING.DOC \
		INSTALL INSTALL.BINDIST NEWS README \
		NEWS.vmgen README.vmgen ToDo

INFO=		gforth vmgen

OPTIONS_DEFINE=	DOCS

.include <bsd.port.pre.mk>

.if ${ARCH} == i386 || ${ARCH} == powerpc || ${ARCH} == armv6 || ${ARCH} == armv7
WORDSIZE=32
.else
WORDSIZE=64
.endif

.if ${ARCH} == powerpc || ${ARCH} == powerpc64 || ${ARCH} == sparc64
BYTEORDER=b
.else
BYTEORDER=l
.endif

post-patch:
	${REINPLACE_CMD} 's:@CC@:& -I${LOCALBASE}/include -L${LOCALBASE}/lib:' \
		 ${WRKSRC}/envos.fs.in
	${REINPLACE_CMD} '/ checkone/d' ${WRKSRC}/Makefile.in

post-install: install-doc remove-empty-files remove-empty-dirs

install-doc:
.if ${PORT_OPTIONS:MDOCS}
	@${MKDIR} ${STAGEDIR}${DOCSDIR}
. for filename in ${PORTDOCS}
	${INSTALL_DATA} ${WRKSRC}/${filename} ${STAGEDIR}${DOCSDIR}
. endfor
.endif

# Remove unused file
remove-empty-files:
	@${RM} ${STAGEDIR}${DATADIR}/site-forth/siteinit.fs

# Remove unused directories
remove-empty-dirs:
	@${FIND} -d ${STAGEDIR}${DATADIR}/${PORTVERSION}/arch/ -type d -empty -delete

.include <bsd.port.post.mk>
