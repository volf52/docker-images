FROM volf52/tars:0.1.1 as tars
FROM volf52/upx-minimal:4.0.1 as upx-src
FROM alpine:3.16.2 as fetch

WORKDIR /bench

ARG VERSION

COPY --from=tars /bin/tars .
COPY --from=upx-src /bin/upx .

RUN apk add curl && \
  curl -sSL "https://github.com/ducaale/xh/releases/download/v${VERSION}/xh-v${VERSION}-x86_64-unknown-linux-musl.tar.gz" -o xh.tar.gz && \
  /bench/tars ./xh.tar.gz && mv xh-v${VERSION}-x86_64-unknown-linux-musl/xh ./xh && \
  /bench/upx --best --lzma -o xh_min ./xh

FROM scratch

COPY --from=fetch /bench/xh_min /bin/xh

CMD ["xh", "--version"]
