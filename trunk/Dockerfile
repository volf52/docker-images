FROM volf52/upx-minimal:4.0.1 as upx-src
FROM volf52/rust-musl-builder:1.65.0-slim-mold as base

ARG VERSION

COPY --from=upx-src /bin/upx /home/volfy/upx

RUN cargo install trunk --version ${VERSION} && \
  /home/volfy/upx --best --lzma -o /home/volfy/trunk /home/volfy/.cargo/bin/trunk

FROM scratch

COPY --from=base /home/volfy/trunk /bin/trunk

CMD [ "/bin/trunk", "--version" ]
