# Minimal Image for tini

[SRC](https://github.com/krallin/tini)

## Usage

```dockerfile
# ... other build steps

FROM volf52/tini:0.19.0 as tini-src

# Use the binary in other stages
FROM base as prod

COPY --from=tini-src /bin/tini /bin/tini

ENTRYPOINT ["/bin/tini", "--", "/app"]
```
