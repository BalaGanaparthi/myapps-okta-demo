FROM golang:latest

# Define current working directory
WORKDIR /infra

# Download modules to local cache so we can skip re-
# downloading on consecutive docker build commands
# COPY go.mod .
# COPY go.sum .
# RUN go mod download

# Add sources
COPY . .

# RUN go build -o out/auth0-go-web-app .

# Expose port 3000 for our web app binary
EXPOSE 8080

# CMD ["/01-Login/out/auth0-go-web-app"]

CMD ["go", "run", "main.go"]
