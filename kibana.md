
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

```
// Query for saved objects
GET .kibana/_search
{
 "query": {
   "match": {
     "type": "index-pattern"
   }
 }
}
```

// run tslint on file
`yarn tslint relative/path/to/file`

```
// preserve ES data in folder
yarn es snapshot -E path.data=../data
```


```
// fix localization
node scripts/i18n_check.js --fix
```

```
yarn es snapshot -E "xpack.security.enabled=false"
```

```
node scripts/update_prs 38366
```

```
// auto correct prettier
node_modules/.bin/eslint --cache '{src,src-docs,src-framer}/**/*.{ts,tsx,js}' --fix

// this is faster
yarn lint-fix
```
