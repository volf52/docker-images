FROM volf52/upx-minimal:4.0.1 as upx-src
FROM volf52/rust-musl-builder:1.65.0-slim-mold as build

WORKDIR /home/volfy/bench

COPY --from=upx-src /bin/upx .

RUN cargo install tree-sitter-cli && ./upx --best --lzma -o tree-sitter /home/volfy/.cargo/bin/tree-sitter

FROM scratch

COPY --from=build /home/volfy/bench/tree-sitter /bin/tree-sitter

CMD [ "/bin/tree-sitter", "--version" ]
