PORTNAME=	containerd
DISTVERSIONPREFIX=v
DISTVERSION=	1.6.6
PORTREVISION=	3
CATEGORIES=	sysutils

MAINTAINER=	decke@FreeBSD.org
COMMENT=	Open and reliable container runtime

LICENSE=	APACHE20
LICENSE_FILE=	${WRKSRC}/LICENSE

BUILD_DEPENDS=	bash:shells/bash

USES=		cpe gmake go:modules,no_targets
USE_GITHUB=	yes
GH_SUBDIR=	src/github.com/containerd/containerd

CPE_VENDOR=	linuxfoundation

USE_RC_SUBR=	containerd

MAKE_ENV=	${GO_ENV} \
		GOFLAGS="${GO_BUILDFLAGS}" \
		VERSION="${DISTVERSION}"

PLIST_FILES=	bin/containerd \
		bin/containerd-shim \
		bin/containerd-stress \
		bin/ctr

do-install:
	@(cd ${WRKSRC} && ${SETENV} DESTDIR="${STAGEDIR}" ${MAKE_CMD} install)

.include <bsd.port.mk>
