PROJECT := doublezhiming
SERVICE := ruby
COMPOSE_FILE := docker-compose.yml
DOCKER_REPO := docker-repos:8123

# Cosmetics
YELLOW := "\e[1;33m"
NC := "\e[0m"

# Shell Functions
INFO := @bash -c '\
  printf $(YELLOW); \
  echo "=> $$1"; \
  printf $(NC)' SOME_VALUE

build:
	${INFO} "Build $(SERVICE)..."
	@ docker-compose -p $(PROJECT) -f $(COMPOSE_FILE) build $(SERVICE)

start:
	${INFO} "Start $(SERVICE)..."
	@ docker-compose -p $(PROJECT) -f $(COMPOSE_FILE) up -d $(SERVICE)

stop:
	${INFO} "Stop $(SERVICE)..."
	@ docker-compose -p $(PROJECT) -f $(COMPOSE_FILE) stop $(SERVICE)

rm:
	${INFO} "Remove $(SERVICE)..."
	@ docker-compose -p $(PROJECT) -f $(COMPOSE_FILE) rm

# make tag TAG=1.0.0
# tag:
# 	${INFO} "Tag $(SERVICE) $(TAG)..."
# 	@ docker tag $(PROJECT)/$(SERVICE):latest $(DOCKER_REPO)/$(PROJECT)/$(SERVICE):$(TAG)

# make login USERNAME=zhiming.zhong
# login:
# 	${INFO} "Login in to docker $(DOCKER_REPO) with $(USERNAME)..."
# 	@ docker login -u $(USERNAME) $(DOCKER_REPO)

# make push TAG=1.0.0
push:
	${INFO} "Publish $(SERVICE) $(TAG)..."
	# @ docker push $(DOCKER_REPO)/$(PROJECT)/$(SERVICE):$(TAG)
	@ docker push $(PROJECT)/$(SERVICE):$(TAG)
