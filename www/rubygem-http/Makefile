# Created by: Sunpoet Po-Chuan Hsieh <sunpoet@FreeBSD.org>

PORTNAME=	http
PORTVERSION=	5.1.0
CATEGORIES=	www rubygems
MASTER_SITES=	RG

MAINTAINER=	sunpoet@FreeBSD.org
COMMENT=	Simple Ruby DSL for making HTTP requests

LICENSE=	MIT
LICENSE_FILE=	${WRKSRC}/LICENSE.txt

RUN_DEPENDS=	rubygem-addressable>=2.8<3:www/rubygem-addressable \
		rubygem-http-cookie>=1.0<2:www/rubygem-http-cookie \
		rubygem-http-form_data>=2.2<3:www/rubygem-http-form_data \
		rubygem-llhttp-ffi>=0.4.0<0.5:www/rubygem-llhttp-ffi

USES=		gem
USE_RUBY=	yes

NO_ARCH=	yes

.include <bsd.port.mk>
