lint: ## Bad code
	go install github.com/golangci/golangci-lint/cmd/golangci-lint@latest
	golangci-lint run

build: ## compile source code to a binary
	make lint
	go mod init github.com/fmamah777/awesome-api
	go get github.com/gorilla/mux
	go build

run: ## Run the app in the background and write the logs
	./awesome-api >./awesome.log 2>&1 &

stop: ## stop the app
	pgrep awesome-api | xargs kill

clean: ## delete the binary awesome-api
	rm -rf ./awesome-api | rm -rf awesome.log
	pgrep awesome-api | xargs kill

test: ## test for functionality
	curl http://localhost:9999
	curl http://localhost:9999/health
Silent: ## test for functionality

help: ## Print a list of all the goals with a sentence.
	sed -n '1p;5p;8p;15p;18p;p' Makefile | grep "##" | tr -d "##"
