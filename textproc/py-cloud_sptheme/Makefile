# Created by: Horia Racoviceanu <horia@racoviceanu.com>
# $FreeBSD$

PORTNAME=	cloud_sptheme
PORTVERSION=	1.7.1
PORTREVISION=	1
CATEGORIES=	textproc python
MASTER_SITES=	CHEESESHOP
PKGNAMEPREFIX=	${PYTHON_PKGNAMEPREFIX}
DIST_SUBDIR=	python

MAINTAINER=	ports@FreeBSD.org
COMMENT=	Sphinx theme

LICENSE=	BSD3CLAUSE
LICENSE_FILE=	${WRKSRC}/LICENSE

BUILD_DEPENDS=	${PYTHON_PKGNAMEPREFIX}sphinx>=1.3:textproc/py-sphinx
RUN_DEPENDS=	${PYTHON_PKGNAMEPREFIX}sphinx>=1.3:textproc/py-sphinx

USES=		python
USE_PYTHON=	distutils autoplist
PYDISTUTILS_BUILDARGS=	build_sphinx -E
NO_ARCH=	yes

PORTDOCS=	*

DOCSDIR=	${PREFIX}/share/doc/py-${PORTNAME}

OPTIONS_DEFINE=	DOCS

post-install-DOCS-on:
	@${MKDIR} ${STAGEDIR}${DOCSDIR} ${STAGEDIR}${DOCSDIR2}
	${INSTALL_DATA} ${WRKSRC}/README ${WRKSRC}/CHANGES ${STAGEDIR}${DOCSDIR}
	cd ${WRKSRC}/build/sphinx && ${COPYTREE_SHARE} html ${STAGEDIR}${DOCSDIR}

.include <bsd.port.mk>
