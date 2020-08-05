# db_maker
 Start up a mysql server Docker image, and create a local users database.

I needed a disposable MySQL server with a database of user information.  Hello, Docker and Fakenamegenerator.com/order.php .  Not affiliated, but I've been a big fan of FNG for a long time.  

These scripts assume you've included ALL fields when creating your CSV file.  They also assume you're getting a CSV file, and not a .sql file, which would have been much smarter.  Might've saved me some time too.

Here's how to go from fresh OS install to running DB pretty quickly.

```
sudo apt-get update && sudo apt-get upgrade  -y
```
```
sudo apt-get install python3-pip docker docker-compose -y
```

```
sudo usermod -a -G docker ubuntu
```
```
sudo pip3 install mysql-connector-python
```
```
docker run -e MYSQL_ROOT_PASSWORD=dingdong --name bert-mysql --network host -d mysql:latest
```
```
sleep 90
```
```
python3 create_db.py
```
```
python3 create_table.py
```
```
python3 db_insert.py
```

If you want to run the MySQL CLI from the docker image:
```
docker exec -it bert-mysql mysql -uroot -p
```




