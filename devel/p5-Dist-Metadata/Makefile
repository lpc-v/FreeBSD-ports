PORTNAME=	Dist-Metadata
PORTVERSION=	0.927
CATEGORIES=	devel perl5
MASTER_SITES=	CPAN
PKGNAMEPREFIX=	p5-

MAINTAINER=	perl@FreeBSD.org
COMMENT=	Perl extension for information about a perl module distribution

LICENSE=	ART10 GPLv1+
LICENSE_COMB=	dual
LICENSE_FILE=	${WRKSRC}/LICENSE

BUILD_DEPENDS=	${RUN_DEPENDS}
RUN_DEPENDS=	\
	p5-Archive-Zip>=1.30:archivers/p5-Archive-Zip \
	p5-CPAN-DistnameInfo>=0.12:devel/p5-CPAN-DistnameInfo \
	p5-File-Spec-Native>=1.002:devel/p5-File-Spec-Native \
	p5-Path-Class>=0.24:devel/p5-Path-Class \
	p5-Try-Tiny>=0.09:lang/p5-Try-Tiny
TEST_DEPENDS=	\
	p5-Test-Fatal>0:devel/p5-Test-Fatal \
	p5-Test-MockObject>0:devel/p5-Test-MockObject

USES=		perl5
USE_PERL5=	configure
NO_ARCH=	YES

.include <bsd.port.mk>
