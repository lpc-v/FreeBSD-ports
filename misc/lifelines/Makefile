# Created by: Matt Emmerton <matt@gsicomp.on.ca>

PORTNAME=	lifelines
PORTVERSION=	3.1.1
PORTREVISION=	1
CATEGORIES=	misc
MASTER_SITES=	https://github.com/MarcNo/lifelines/releases/download/${PORTVERSION}/

MAINTAINER=	matt@gsicomp.on.ca
COMMENT=	Advanced genealogical system

LICENSE=	MIT

USES=		autoreconf bison gmake iconv ncurses

GNU_CONFIGURE=	yes
CONFIGURE_ENV=	YACC="bison -y"

CONFLICTS_INSTALL=	atheme-services # bin/dbverify

MAKE_JOBS_UNSAFE=yes

# Lifelines always installs documenatation.  This is contrary to the FreeBSD
# norm which uses --with-docs (aka DOCS) to do so.  We patch the Makefiles
# below in pre-patch.
# Lifelines uses --with-docs to indicate that the full XML docbook toolcahin
# needs to be installed to build the docs.  We use BUILDDOCS for that purpose.

OPTIONS_DEFINE=		BUILDDOCS DOCS NLS
OPTIONS_SUB=		yes
BUILDDOCS_DESC=		Build documentation (requires docbook toolchain)
DOCS_DESC=		Install documentation
NLS_DESC=		Build with NLS support

BUILDDOCS_CONFIGURE_WITH=	docs
BUILDDOCS_BUILD_DEPENDS=	xmlto:textproc/xmlto \
				dblatex:textproc/dblatex

NLS_USES=		gettext
NLS_CONFIGURE_ENABLE=	nls

pre-patch:
	@${REINPLACE_CMD} -e 's,ncursesw/curses.h,curses.h,' \
		${WRKSRC}/src/hdrs/mycurses.h

pre-patch-DOCS-off:
	@${REINPLACE_CMD} -e 's,^doc_DATA.*,doc_DATA = .linesrc lines.cfg,' \
	${WRKSRC}/Makefile.am
	@${REINPLACE_CMD} -e 's,^doc_DATA.*,doc_DATA=,' \
	${WRKSRC}/docs/manual/Makefile.am

.include <bsd.port.mk>
