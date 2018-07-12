# fess
FESS Docker Container. See more at https://github.com/codelibs/fess
Demo at https://search.n2sm.co.jp

# Before bringing the Container up

On Ubuntu we had to set the `vm.max_map_count` setting to 262144. Run `sysctl -w vm.max_map_count=262144`.

For more information, refer to https://www.elastic.co/guide/en/elasticsearch/reference/current/vm-max-map-count.html

# Usage
docker-compose.yml

```
version: '3'
services:
  fess:
    image: codelibs/fess:12.1
    ports:
      - "8080:8080"
    environment:
      - ES_HTTP_URL=http://elasticsearch:9200
      - ES_TRANSPORT_URL=elasticsearch:9300
      - FESS_DICTIONARY_PATH=/var/lib/elasticsearch/config/

  elasticsearch:
    image: elasticsearch:5.6
    ports:
      - "9200:9200"
    volumes:
      - elasticsearch:/usr/share/elasticsearch/data

volumes:
  elasticsearch:
```

Try it at http://localhost:8080
