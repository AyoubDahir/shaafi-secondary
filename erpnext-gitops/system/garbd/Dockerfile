# Minimal garbd (Galera arbitrator) image, reusing the same trusted image family as
# the mariadb-galera Application (apps/mariadb-galera.yaml) rather than pulling in an
# unrelated/unverified third-party garbd image — bitnami's mariadb-galera image
# already ships the wsrep/galera binaries, garbd included.
#
# VERIFY BEFORE BUILDING: confirm the garbd binary's exact path in this image tag
# (it has historically lived at /opt/bitnami/mariadb/bin/garbd) with:
#   docker run --rm --entrypoint find bitnamilegacy/mariadb-galera:11.4.2-debian-12-r0 / -iname 'garbd*'
# and adjust ENTRYPOINT below if the path differs for the tag actually in use.
FROM bitnamilegacy/mariadb-galera:11.4.2-debian-12-r0
USER root
ENTRYPOINT ["/opt/bitnami/mariadb/bin/garbd"]
