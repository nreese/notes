
```shell
// run API functional tests
./node_modules/.bin/grunt test:api
```

```shell
// unpack functional test archives
gunzip -k data.json.gz 
```

```shell
// pack functional test archives
gzip data.json
```

```shell
// build docs
docs/build_docs.pl --doc ./kibana/docs/index.asciidoc --resource=./kibana/x-pack/docs/ --chunk 1 --open
```
