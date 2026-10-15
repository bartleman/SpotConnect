# SpotConnect spotraop, AirPlay 2 test build (philippe44/SpotConnect#84).
# Built by .github/workflows/airplay2-build.yml with the staged static binaries as context,
# one per architecture. The binary is fully static; alpine only adds a shell and CA certificates.
#
#   docker run --rm --network host -v $PWD/config:/config ghcr.io/<owner>/spotconnect:airplay2 \
#       -Z -I -x /config/spotraop.xml -D <client_id> -S <client_secret>
#
# Host networking is required: mDNS discovery and the AirPlay RTP/NTP UDP ports do not work behind a bridge.
FROM alpine:3.20
ARG TARGETARCH
RUN apk add --no-cache ca-certificates
COPY spotraop-${TARGETARCH} /usr/local/bin/spotraop
VOLUME /config
WORKDIR /config
ENTRYPOINT ["/usr/local/bin/spotraop"]
CMD ["-Z", "-I", "-x", "/config/spotraop.xml"]
