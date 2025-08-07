FROM golang:1.21-alpine

WORKDIR /app

# Create mount point directory with proper permissions
RUN mkdir -p /data && chmod 777 /data
RUN mkdir -p /.cache/go-build && chmod 777 /.cache/go-build
RUN mkdir -p /go && chmod 777 /go

# Install wget for healthcheck
RUN apk add --no-cache wget

# Copy go mod files
COPY go.mod go.sum ./

# Download dependencies
RUN go mod download

# Copy source code
COPY . .

# Build the application
RUN go build -o main cmd/bugtracker/main.go

# Expose port 8080
EXPOSE 8080

# Run the binary
CMD ["./main"] 