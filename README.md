## How to start the demo app:

```
(cd code/base && composer install) && \
sudo docker-compose up
```

Then open http://localhost:8080/

## Things I've tried:

Reset opcache:

```
curl http://localhost:8080/?reset=1
```

Simulate a deployment:

```
(cd code && ts=$(date +%s) && rsync -a base/ $ts/ && rm -rf $ts/var/cache && mkdir $ts/var/cache && chmod 777 $ts/var/cache && rm -f current && ln -s $ts current && curl http://localhost:8080/?reset=1)
```

Stress the server while doing any of the above:

```
ab -n 10000 -c 100 http://localhost:8080/en/blog/
```
