build: ## Generate the website from the markdown and configuration files in the directory
	hugo

clean: ## Cleanup the content of the directory 
	rm -rf dist/*

post: ## Create a new blog post whose filename and title come from the environment variables
	sed -i ‘2s/title: .*/title: “$(POST_TITLE)“/’ content/posts/$(POST_NAME).md >/dev/null 2>&1
	