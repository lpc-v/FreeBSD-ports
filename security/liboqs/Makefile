PORTNAME=	liboqs
DISTVERSION=	0.7.2.20220607
CATEGORIES=	security

MAINTAINER=	yuri@FreeBSD.org
COMMENT=	C library for quantum-resistant cryptography

LICENSE=	MIT
LICENSE_FILE=	${WRKSRC}/LICENSE.txt

BROKEN_i386=	Unknown or unsupported processor: i386
BROKEN_powerpc=	Unknown or unsupported processor: powerpc
BROKEN_aarch64=	use of undeclared identifier 'ID_AA64ISAR0_SHA3_BASE', see https://github.com/open-quantum-safe/liboqs/issues/1223

TEST_DEPENDS=	${PYTHON_PKGNAMEPREFIX}pytest4>0:devel/py-pytest4@${PY_FLAVOR} \
		${PYTHON_PKGNAMEPREFIX}yaml>0:devel/py-yaml@${PY_FLAVOR} \
		bash:shells/bash

USES=		cmake python:test shebangfix ssl
USE_LDCONFIG=	yes

USE_GITHUB=	yes
GH_ACCOUNT=	open-quantum-safe
GH_TAGNAME=	38d3014dc2f74ec0f0c1a9e7e61aa4d2251adcc9

SHEBANG_GLOB=	*.sh

CMAKE_ON=	BUILD_SHARED_LIBS OQS_DIST_BUILD

TEST_TARGET=	run_tests

BINARY_ALIAS=	python3=${PYTHON_CMD}

.include <bsd.port.mk>
