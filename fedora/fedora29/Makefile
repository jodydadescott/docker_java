BUILD_NUMBER := latest
PROJECT_NAME := fedora-jdk8
DOCKER_REGISTRY := jodydadescott
DOCKER_IMAGE_NAME?=$(PROJECT_NAME)
DOCKER_IMAGE_TAG?=$(BUILD_NUMBER)

JDK_URL := http://download.oracle.com/otn-pub/java/jdk/8u191-b12/2787e4a523244c269598db4e85c51e0c/jdk-8u191-linux-x64.tar.gz

build:
	make dockerbuild

clean:
	make dockerclean

dockerbuild:
	make .dockerbuild

.dockerbuild:
	touch .dockerbuild
	mkdir -p cache
	[ -f cache/jdk.tgz ] || curl -L -o cache/jdk.tgz --header "Cookie: oraclelicense=a" $(JDK_URL)
	docker build -t $(DOCKER_REGISTRY)/$(DOCKER_IMAGE_NAME):$(DOCKER_IMAGE_TAG) .

dockerrun:
	make dockerbuild
	docker run -it --entrypoint /bin/bash $(DOCKER_REGISTRY)/$(PROJECT_NAME):$(BUILD_NUMBER)

dockerpush:
	docker push $(DOCKER_REGISTRY)/$(DOCKER_IMAGE_NAME):$(DOCKER_IMAGE_TAG)

dockerclean:
	$(RM) .dockerbuild
	$(RM) -rf cache
