PORTNAME=	jschema-to-python
DISTVERSION=	1.2.3
CATEGORIES=	devel python
MASTER_SITES=	CHEESESHOP
PKGNAMEPREFIX=	${PYTHON_PKGNAMEPREFIX}
DISTNAME=	jschema_to_python-${DISTVERSION}

MAINTAINER=	nork@ninth-nine.com
COMMENT=	Generate Python classes from a JSON schema

LICENSE=	MIT
LICENSE_FILE=	${WRKSRC}/LICENSE

BUILD_DEPENDS=	${PYTHON_PKGNAMEPREFIX}pbr>0:devel/py-pbr@${PY_FLAVOR}
RUN_DEPENDS=	${PYTHON_PKGNAMEPREFIX}attrs>0:devel/py-attrs@${PY_FLAVOR} \
		${PYTHON_PKGNAMEPREFIX}jsonpickle>0:devel/py-jsonpickle@${PY_FLAVOR} \
		${PYTHON_PKGNAMEPREFIX}pbr>0:devel/py-pbr@${PY_FLAVOR}

USES=		dos2unix python:3.6+
USE_PYTHON=	autoplist concurrent distutils

NO_ARCH=	yes

.include <bsd.port.mk>
