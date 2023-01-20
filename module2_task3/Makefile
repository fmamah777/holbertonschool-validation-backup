.SILENT:
help: ## Must be implemented and print a list of all the goals with a sentence.
	sed -n '2p;5p;14p;18p;22p;25p;29p;33p' Makefile | grep "##" | tr -d "##"

lint: ## Checks to see if the code is written in compliance with the linter.
	golangci-lint run; \
	if [ $? -eq 0 ]; then \
		exit 0; \
	else \
		exit 1; \
		echo golangci-lint run; \
	fi

build: ## Compiles the source code of the application to a binary named awesome-api.
	go mod init github.com/cbmarie255/awesome-api
	go build

run: ## Runs the application in background by executing the binary awesome-api, and write logs into a file named awesome.log.
	chmod u+x awesome-api
	./awesome-api >./awesome.log 2>&1 &

stop: ## Stops the application.
	pgrep awesome-api | xargs kill

clean: ## Delete the binary awesome-api and the log file awesome-api.log.
	-rm -r awesome-api
	-pgrep awesome-api | xargs kill
	-rm -f awesome-api
	-rm -f coverage-units.out
	-rm -f coverage-integrations.out

test: ## Tests application's server to ensure that it behaves as expected.
	curl http://localhost:9999
	curl http://localhost:9999/health

unit-tests: ## Unit-testing code for the HelloHandler method.
	go test -v -short -coverprofile=coverage-units.out

integration-tests: ## Run the integration tests and write the coverage report
	go test -coverprofile=coverage-integrations.out -run ^Test_server$ -covermode=atomic -short $(INTEGRATION_TEST_FILES)