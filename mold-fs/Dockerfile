FROM radial/busyboxplus:curl as downloader

ARG VERSION

RUN curl -sSL "https://github.com/rui314/mold/releases/download/v${VERSION}/mold-${VERSION}-x86_64-linux.tar.gz" -o /mold-${VERSION}.tar.gz

FROM scratch

ARG VERSION

# docker create --name dummy volf52/mold-fs:latest ; docker cp dummy /mold-${VERSION}.tar.gz .
COPY --from=downloader /bin/ls /bin/ls
COPY --from=downloader /mold-${VERSION}.tar.gz /mold-${VERSION}.tar.gz

CMD ["/bin/ls", "/"]
