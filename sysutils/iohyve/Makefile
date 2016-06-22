# $FreeBSD$

PORTNAME=	iohyve
PORTVERSION=	0.7.6
CATEGORIES=	sysutils

MAINTAINER=	lme@FreeBSD.org
COMMENT=	bhyve manager utilizing ZFS and other FreeBSD tools

LICENSE=	BSD2CLAUSE
LICENSE_FILE=	${WRKSRC}/LICENSE

USE_GITHUB=	yes
GH_ACCOUNT=	pr1ntf

NO_BUILD=	yes
NO_ARCH=	yes

post-patch:
	@${REINPLACE_CMD} -e "s|/usr/local/lib/iohyve|${PREFIX}/lib/iohyve|g" ${WRKSRC}/iohyve

pre-install:
	@${MKDIR} ${PREFIX}/lib/iohyve                                                          

do-install:
	${INSTALL_SCRIPT} ${WRKSRC}/rc.d/iohyve ${PREFIX}/etc/rc.d                              
	${INSTALL_SCRIPT} ${WRKSRC}/iohyve ${PREFIX}/sbin                                       
	(cd ${WRKSRC}/lib/ && ${COPYTREE_SHARE} . ${PREFIX}/lib/iohyve)                         
	${INSTALL_MAN} ${WRKSRC}/iohyve.8 ${PREFIX}/man/man8

.include <bsd.port.mk>
