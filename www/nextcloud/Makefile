# $FreeBSD$

PORTNAME=	nextcloud
PORTVERSION=	10.0.1
PORTREVISION=	1
CATEGORIES=	www
MASTER_SITES=	https://download.nextcloud.com/server/releases/

MAINTAINER=	loic.blot@unix-experience.fr
COMMENT=	Personal cloud which runs on your own server

LICENSE=	AGPLv3
LICENSE_FILE=	${WRKSRC}/COPYING-AGPL

USES=		cpe php:web tar:bzip2 ssl
USE_PHP=	bz2 ctype curl dom fileinfo filter gd hash iconv json \
		mbstring pdo posix session simplexml xml xmlreader xmlwriter \
		xsl wddx zip zlib

NEXTCLOUD_USERNAME?=	${WWWOWN}
NEXTCLOUD_GROUPNAME?=	${WWWGRP}

WRKSRC=		${WRKDIR}/${PORTNAME}
NO_BUILD=	yes
NO_ARCH=	yes
SUB_FILES=	pkg-message
PLIST_SUB=	NEXTCLOUD_USERNAME=${NEXTCLOUD_USERNAME} \
		NEXTCLOUD_GROUPNAME=${NEXTCLOUD_GROUPNAME}

OPTIONS_DEFINE=	EXIF LDAP SMB SSL
OPTIONS_MULTI=	DB
OPTIONS_MULTI_DB=	MYSQL PGSQL SQLITE
OPTIONS_DEFAULT=	EXIF LDAP MYSQL SMB SSL

EXIF_DESC=	Image rotation support

EXIF_USE=	PHP=exif
LDAP_USE=	PHP=ldap
MYSQL_USES=	mysql
MYSQL_USE=	PHP=pdo_mysql
PGSQL_USES=	pgsql
PGSQL_USE=	PHP=pdo_pgsql,pgsql
SQLITE_USE=	PHP=pdo_sqlite,sqlite3
SMB_RUN_DEPENDS=	pecl-smbclient>=0.8.0:net/pecl-smbclient
SSL_USE=	PHP=openssl

.include <bsd.port.options.mk>

.if ${OPSYS} == FreeBSD && ${OSVERSION} < 1002000
WITH_OPENSSL_PORT=	yes
.endif

do-install:
	@${MKDIR} -m 0755 ${STAGEDIR}${WWWDIR}
	@cd ${WRKSRC} && ${COPYTREE_SHARE} . ${STAGEDIR}${WWWDIR}
	@${MKDIR} ${STAGEDIR}${WWWDIR}/data

.include <bsd.port.mk>
