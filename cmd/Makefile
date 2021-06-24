BUILD_NAME:=twdl
BUILD_VERSION:=1.0
SOURCE:=*.go
LDFLAGS:=-ldflags "-X main.Version=${BUILD_VERSION}"

all: build install

test: 
	go test

build: test
	go build -o ${BUILD_NAME} ${SOURCE}

build_linux: test
	CGO_ENABLED=0 GOOS=linux GOARCH=amd64 go build -o ${BUILD_NAME} ${SOURCE}

build_win: test
	CGO_ENABLED=0 GOOS=windows GOARCH=amd64 go build -o ${BUILD_NAME} ${SOURCE}

build_macos: test
	CGO_ENABLED=0 GOOS=darwin GOARCH=amd64 go build -o ${BUILD_NAME} ${SOURCE}

install: build
	go install
#release: build build_win build_macos
	
clean:
	go clean
	rm ${BUILD_NAME}

.PHONY: all test build build_linux build_win install clean
