FROM bitnami/oraclelinux-extras:7-r204
LABEL maintainer "Cooby <admin@cooby.io>"

# Install required system packages and dependencies
RUN install_packages bzip2-libs cyrus-sasl-lib glibc keyutils-libs krb5-libs libcom_err libffi libgcc libgcrypt libgpg-error libselinux libstdc++ libxml2 libxslt ncurses-libs nspr nss nss-softokn-freebl nss-util openldap openssl-libs pcre readline sqlite xz-libs zlib
RUN bitnami-pkg install python-3.6.7-20 --checksum 7ab1c97e65af2ce869442c4f9f9abe4bf984d36136186db3eda51d853a8eb8ad
# RUN bitnami-pkg install postgresql-client-10.6.0-20 --checksum 3f1d493904e0c681e17c9135c92d2e51fea7b0161aa4c3c1ca64acf084e58eb1
RUN bitnami-pkg install node-7.10.1-1 --checksum c58b53a2ea5feafe1e0f0ef4b990d9ff55c37089ff5fba12e1938183e8a81a2f
RUN bitnami-pkg unpack odoo-11.0.20181215-0 --checksum 52e001d042b472baed18018be2c4fe4eaacc01f0b09f30e32ce109c76b55add8

COPY rootfs /
ENV COOBY_APP_NAME="odoo-app" \
    COOBY_IMAGE_VERSION="11.0.20181215-ol-7-r5" \
    ODOO_EMAIL="superadmin" \
    ODOO_PASSWORD="bitnami" \
    PATH="/opt/bitnami/python/bin:/opt/bitnami/postgresql/bin:/opt/bitnami/node/bin:$PATH" \
    POSTGRESQL_HOST="postgresql" \
    POSTGRESQL_PASSWORD="" \
    POSTGRESQL_PORT_NUMBER="5432" \
    POSTGRESQL_USER="postgres" \
    SMTP_HOST="" \
    SMTP_PASSWORD="" \
    SMTP_PORT="" \
    SMTP_PROTOCOL="" \
    SMTP_USER=""
#     ingress.enabled=true
#     ingress.hosts[0].name=odoo.cooby.tech
#     ingress.hosts[0].certManager=true
#     ingress.hosts[0].tlsSecret=cloud1-cooby-tech-crt
#     persistence.storageClass=openebs-jiva-default
#     postgresql.persistence.storageClass=openebs-jiva-default


EXPOSE 8069 8071

ENTRYPOINT [ "/app-entrypoint.sh" ]
CMD [ "nami", "start", "--foreground", "odoo-app" ]
