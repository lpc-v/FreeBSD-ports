PORTNAME=	ddgr
PORTVERSION=	2.0
DISTVERSIONPREFIX=	v
CATEGORIES=	www

MAINTAINER=	amdmi3@FreeBSD.org
COMMENT=	DuckDuckGo from the terminal

LICENSE=	GPLv3+
LICENSE_FILE=	${WRKSRC}/LICENSE

USE_GITHUB=	yes
GH_ACCOUNT=	jarun

USES=		python:3.6+ shebangfix
SHEBANG_FILES=	${PORTNAME}
NO_ARCH=	yes
NO_BUILD=	yes

PORTDOCS=	README.md CHANGELOG
PLIST_FILES=	bin/ddgr \
		share/man/man1/ddgr.1.gz

OPTIONS_DEFINE=	BASH ZSH FISH DOCS
OPTIONS_DEFAULT=BASH ZSH FISH

BASH_PLIST_FILES=	etc/bash_completion.d/ddgr-completion.bash
ZSH_PLIST_FILES=	share/zsh/site-functions/_ddgr
FISH_PLIST_FILES=	share/fish/completions/ddgr.fish

do-install:
	${INSTALL_SCRIPT} ${WRKSRC}/ddgr ${STAGEDIR}${PREFIX}/bin
	${INSTALL_MAN} ${WRKSRC}/ddgr.1 ${STAGEDIR}${MANPREFIX}/share/man/man1

do-install-DOCS-on:
	@${MKDIR} ${STAGEDIR}${DOCSDIR}
	cd ${WRKSRC} && ${INSTALL_DATA} ${PORTDOCS} ${STAGEDIR}${DOCSDIR}/

do-install-BASH-on:
	@${MKDIR} ${STAGEDIR}${PREFIX}/etc/bash_completion.d/
	${INSTALL_DATA} ${WRKSRC}/auto-completion/bash/ddgr-completion.bash \
		${STAGEDIR}${PREFIX}/etc/bash_completion.d/

do-install-ZSH-on:
	@${MKDIR} ${STAGEDIR}${PREFIX}/share/zsh/site-functions/
	${INSTALL_DATA} ${WRKSRC}/auto-completion/zsh/_ddgr \
		${STAGEDIR}${PREFIX}/share/zsh/site-functions/

do-install-FISH-on:
	@${MKDIR} ${STAGEDIR}${PREFIX}/share/fish/completions/
	${INSTALL_DATA} ${WRKSRC}/auto-completion/fish/ddgr.fish \
		${STAGEDIR}${PREFIX}/share/fish/completions/

do-test:
	cd ${WRKSRC} && ./ddgr --help >/dev/null 2>&1

.include <bsd.port.mk>
