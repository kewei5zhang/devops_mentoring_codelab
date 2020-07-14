.PHONY: export
.PHONY: servie
.PHONY: build
.PHONY: debug
.PHONY:

CODELAB_DIR := codelabs
SHA_ID := ${shell git rev-parse HEAD}
GCP_PROJECT_ID := kewei-demo-sandbox

### Export
### claat export all .md files under site/codelabs
export: 
	cd ${CODELAB_DIR}; for i in *.md; do \
		claat export $$i; \
	done

### Serve
serve:
	gulp serve --codelabs-dir=${CODELAB_DIR}

### Build
build:
	docker build -t gcr.io/${GCP_PROJECT_ID}/itmentoring-codelabs:${SHA_ID} \
				 -t gcr.io/${GCP_PROJECT_ID}/itmentoring-codelabs:latest \
				 -f Dockerfile . 

### Run
run:
	docker run -d --name it_mentoring --rm -p 80:3000 gcr.io/${GCP_PROJECT_ID}/itmentoring-codelabs:latest

### Debug
debug: 
	docker run -it gcr.io/${GCP_PROJECT_ID}/itmentoring-codelabs:latest /bin/bash

### Push
push:
	docker push gcr.io/${GCP_PROJECT_ID}/itmentoring-codelabs:${SHA_ID}
	docker push gcr.io/${GCP_PROJECT_ID}/itmentoring-codelabs:latest

### Stop
stop:
	docker stop it_mentoring