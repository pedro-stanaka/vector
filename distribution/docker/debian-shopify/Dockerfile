FROM docker.io/debian:bullseye-slim AS builder

WORKDIR /vector

COPY target/release/vector /usr/bin/vector
RUN mkdir -p /var/lib/vector

RUN apt-get update && apt-get install -y --no-install-recommends ca-certificates tzdata systemd && rm -rf /var/lib/apt/lists/*

COPY --from=builder /usr/bin/vector /usr/bin/vector

# Smoke test
RUN ["vector", "--version"]

ENTRYPOINT ["/usr/bin/vector"]
