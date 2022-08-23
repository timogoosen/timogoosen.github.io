### Docker-compose


Some quick easy setups to get things going in docker-compose:



##### For MySQL Mariadb:

Use this, they also have a mysql:8.0 image if you need that.
Volume configuration part is important. It doesn't use the usual /var/lib/mysql directory.


```

  db:
    image: public.ecr.aws/bitnami/mysql:5.7
    ports:
      - 3307:3306
    environment:
      # MYSQL_DATABASE: sas_eurobonus_loyaltfacts
      MYSQL_ROOT_PASSWORD: SomeSupersecretPass
      MYSQL_PASSWORD: SomeSupersecretPass
      MYSQL_USER: sasloyaltfactsdbuser
      MYSQL_ROOT_HOST: '%'
    volumes:
      - /Users/timo/Desktop/docker-volumes:/bitnami/mysql/data
      # Volume configuration see here: https://hub.docker.com/r/bitnami/mysql (ctrl + f for volume)

```



### Get redis going quickly:


Use this, this will set a password on redis also:


```

  cache:
    image: redis:6.2-alpine
    restart: always
    ports:
      - '6379:6379'
    command: redis-server --save 20 1 --loglevel warning --requirepass eYVX7EwVmmxKPCDmwMtyKVge8oLd2t81
    # volumes: 
    #   - cache:/data


```

You can access the redis server via ENV file with:


```
# .env file 
REDIS_HOST=cache
REDIS_PASSWORD=eYVX7EwVmmxKPCDmwMtyKVge8oLd2t81
REDIS_PORT=6379

```

Which you can reference from your other containers like this:


```

    ports:
      - '9000:9000'
    env_file:
    - ./example-service/.env

```