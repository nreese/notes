1) Run the following commands in Dev tools => Console 
```
    PUT local1
    {}

    PUT local1/_mapping
    {
      "properties": {
        "value": {
          "type": "keyword"
        }
      }
    }

    PUT local1/_doc/1
    {
        "value" : "foo1"
    }

    PUT local2
    {}

    PUT local2/_mapping
    {
      "properties": {
        "value": {
          "type": "keyword"
        }
      }
    }

    PUT local2/_doc/1
    {
        "value" : "foo2"
    }
```
2) Create `local*` data view
3) Open discover, add filter pill with custom DSL
```
{
  "error_query": {
    "indices": [
      {
        "error_type": "exception",
        "message": "local shard failure message 123",
        "name": "local2",
        "shard_ids": [
          0
        ]
      }
    ]
  }
}
```
