# go-simple-bank
video lectures by techschool
# git test access token

1. Install golang
sudo apt install golang-go

1. Install docker
https://docs.docker.com/engine/install/ubuntu/

2. Install migrate (golang-migrate)
https://github.com/golang-migrate/migrate/tree/master/cmd/migrate

3. Create postgres12 image
sudo make postgres

4. Create db simple-bank
sudo make createdb

5. Migrate table schemas
sudo make migrateup

#####################
# Build docker image #
sudo docker build -t simplebank:latest .

# Prepare our custom network bank-network to connect our containers to
sudo docker network create bank-network
sudo docker network connect bank-network postgres12   #or use --network bank-network on creating container

# Run docker image, use container name postgres12 instead of ip, we can do it because we use the same network
sudo docker run --name simplebank --network bank-network -p 8080:8080 -e GIN_MODE=release -e DB_SOURCE="postgresql://root:password@postgres12:5432/simple_bank?sslmode=disable" simplebank:latest

# Check if the both containers are connected to our custom network
sudo docker inspect bank-network

sudo docker compose up
sudo docker compose down