# go-simple-bank
video lectures by techschool

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