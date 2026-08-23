# Minimal garbd (Galera arbitrator) image.
#
# CORRECTED 2026-08-23: the previous approach (FROM bitnamilegacy/mariadb-galera,
# ENTRYPOINT at /opt/bitnami/mariadb/bin/garbd) was wrong — that image family does NOT
# ship a garbd binary at all, only libgalera_smm.so (confirmed by inspecting
# bitnamilegacy/mariadb-galera:12.0.2-debian-12-r0, the tag actually deployed by
# apps/mariadb-galera.yaml). It would have failed even if built.
#
# Debian 12's own official repo ships `galera-arbitrator-4` at 26.4.23-0+deb12u1 — an
# EXACT version match to the libgalera_smm.so bundled in
# bitnamilegacy/mariadb-galera:12.0.2-debian-12-r0 (also 26.4.23). This is an official
# Debian package, not a third-party image, so it satisfies the original goal of this
# file (avoid an unrelated/unverified third-party garbd image) while actually working.
# Confirmed by installing it in a throwaway debian:12-slim container: binary lands at
# /usr/bin/garbd, `garbd --version` reports `4.23.r`.
#
# If the mariadb-galera image tag in apps/mariadb-galera.yaml is ever upgraded, check
# that Debian 12's galera-arbitrator-4 version still matches the new tag's bundled
# libgalera_smm.so version before rebuilding this image.
FROM debian:12-slim
RUN apt-get update \
 && apt-get install -y --no-install-recommends galera-arbitrator-4 \
 && rm -rf /var/lib/apt/lists/*
ENTRYPOINT ["/usr/bin/garbd"]
