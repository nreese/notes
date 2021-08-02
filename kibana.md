
@elasticmachine merge upstream

```
// ts type check
rm -rf ./target && rm -rf ./src/core/target
node scripts/type_check --project=x-pack/tsconfig.json
node scripts/type_check --project=tsconfig.json

./node_modules/.bin/tsc -b x-pack/plugins/maps
```

```
node scripts/precommit_hook --fix

node scripts/eslint x-pack/plugins/maps
```

```
// Start maps functional tests
node scripts/functional_tests_server --config x-pack/test/functional/config.js
node scripts/functional_test_runner --config x-pack/test/functional/config.js --debug --grep=""

node scripts/functional_tests_server --config x-pack/test/api_integration/config.ts
node scripts/functional_test_runner --config x-pack/test/api_integration/config.ts --debug --grep=""

// load es-archives
node scripts/es_archiver load x-pack/test/functional/es_archives/monitoring/singlecluster_green_gold --config path/to/your/ftrconfig
```

```
// view doc preview for PR
https://kibana_95883.docs-preview.app.elstc.co/diff
```

```
// build module stats
node scripts/build_kibana_platform_plugins.js --dist --no-examples --profile
npx webpack-bundle-analyzer src/plugins/maps_legacy/target/public/stats.json
```

```
// locate the process hogging the port
lsof -i:5601
```

```
FORCE_DLL_CREATION=true node scripts/kibana --dev
```

```
@elasticmachine run elasticsearch-ci/docs
```

```
yarn start --run-examples
```

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
DELETE test
{}

PUT test
{}

PUT test/_mapping
{
  "properties": {
  "@timestamp": {
    "type": "date"
  },
  "location": {
    "type": "geo_point"
  }
}
}

PUT test/_doc/1
{
    "@timestamp" : "2019-08-22T14:22:08Z",
    "location": "25,25"
}

PUT test/_doc/2
{
    "location": "25,25"
}

GET test/_search

GET /test/_mapping

GET /test/_field_caps?fields=@timestamp
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

```
// run visual regression tests
// from x-pack folder
// set PERCY_TOKEN env to percy key before commands will work

node scripts/functional_tests_server --config test/visual_regression/config.js

yarn run percy exec node ../scripts/functional_test_runner --config test/visual_regression/config.js --grep=""
```

ingest script to create geo_point
```
{
  "script": {
    "lang": "painless",
    "source": "ctx.surface_geo = [ctx.surface_lon, ctx.surface_lat]"
  }
}
```

`xattr -r -d com.apple.quarantine`
