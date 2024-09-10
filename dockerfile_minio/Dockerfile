FROM minio/minio:latest

# Use curl to download the MinIO client and make it executable
RUN curl -O https://dl.min.io/client/mc/release/linux-amd64/mc && \
    chmod +x mc && \
    mv mc /usr/local/bin/