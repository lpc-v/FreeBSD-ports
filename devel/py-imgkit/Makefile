# Created by: Dan Langille <dvl@FreeBSD.org>

PORTNAME=	imgkit
PORTVERSION=	1.2.2
CATEGORIES=	devel python
MASTER_SITES=	CHEESESHOP
PKGNAMEPREFIX=	${PYTHON_PKGNAMEPREFIX}

MAINTAINER=	dvl@FreeBSD.org
COMMENT=	Python wrapper to convert html to image

LICENSE=	MIT

USES=		python:3.6+
USE_PYTHON=	distutils autoplist

RUN_DEPENDS+=	wkhtmltopdf>0:converters/wkhtmltopdf

.include <bsd.port.mk>
