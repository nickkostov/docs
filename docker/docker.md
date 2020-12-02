```
Преди да се инсталира докер, за всеки случай деинсталирайте 
програмата за да може да се махнат 
всички възможни ненужни пакети.
```
```
sudo yum remove -y docker \
docker-client \
docker-client-latest \
docker-common \
docker-latest \
docker-latest-logrotate \
docker-logrotate \
docker-engine
```

След това инсталирайте docker-ce (docker community edition)
```
sudo yum install -y yum-utils \
device-mapper-persistent-data \
lvm2
```
Сега трябва да се постараем да добавим стабилното хранилище (repository):
```
sudo yum -y install docker-ce
```
Трябва да включим и стартираме демона (сервиза) на докер:
```
sudo systemctl start docker && sudo systemctl enable docker
```
Добавете потребителя в групата на докер за може да ползвате услугата без да ползвате "sudo":
```
sudo usermod -aG docker {yourusername} (може да ползвате променливата за потребител $USER)
```

