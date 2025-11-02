FROM golang:1.24

# Install necessary dependencies
RUN apt update && apt install -y \
    wget \
    dos2unix \
    && apt clean

# Set Go environment and PATH
ENV GOPATH=/root/go
ENV PATH="$GOPATH/bin:/go/bin:$PATH"

# Install MailHog
RUN go install github.com/mailhog/MailHog@latest \
    && cp /root/go/bin/MailHog /usr/local/bin/MailHog

# Copy auth setup script
COPY commands/setup_mailhog_auth.sh /commands/setup_mailhog_auth.sh

# Convert line endings and make executable
RUN dos2unix /commands/setup_mailhog_auth.sh && chmod +x /commands/setup_mailhog_auth.sh
