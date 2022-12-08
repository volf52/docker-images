FROM volf52/tars:0.1.1 as tars-src
FROM volf52/upx-minimal:4.0.1 as upx-src
FROM radial/busyboxplus:curl as downloader

WORKDIR /bench
ARG VERSION

COPY --from=tars-src /bin/tars ./tars
COPY --from=upx-src /bin/upx ./upx

RUN curl -sSL "https://github.com/LukeMathWalker/cargo-chef/releases/download/v${VERSION}/cargo-chef-x86_64-unknown-linux-musl.tar.gz" -o ./cargo-chef.tar.gz && ./tars cargo-chef.tar.gz && ./upx --best --lzma -o cargo-chef-min cargo-chef

FROM scratch

COPY --from=downloader /bench/cargo-chef-min /bin/cargo-chef

CMD [ "/bin/cargo-chef", "--version" ]
