.PHONY: build clean test release
OUTPUT = riff
OUTPUT_WINDOWS = $(OUTPUT).exe
GO_SOURCES = $(shell find cmd pkg -type f -name '*.go')

build: $(OUTPUT)

test: build
	go test -v ./...

$(OUTPUT): $(GO_SOURCES)
	go build -o $(OUTPUT) ../cli.go

release: $(GO_SOURCES)
	GOOS=darwin   GOARCH=amd64 go build -o $(OUTPUT) ../cli.go && tar -czf riff-darwin-amd64.tgz $(OUTPUT) && rm -f $(OUTPUT)
	GOOS=linux    GOARCH=amd64 go build -o $(OUTPUT) ../cli.go && tar -czf riff-linux-amd64.tgz $(OUTPUT) && rm -f $(OUTPUT)
	GOOS=windows  GOARCH=amd64 go build -o $(OUTPUT_WINDOWS) ../cli.go && zip -mq riff-windows-amd64.zip $(OUTPUT_WINDOWS)

clean:
	rm -f $(OUTPUT)
	rm -f riff-darwin-amd64.tgz
	rm -f riff-linux-amd64.tgz
	rm -f riff-windows-amd64.zip
