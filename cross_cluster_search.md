### Setup
1. Start remote elasticsearch by running: `yarn es snapshot -E transport.port=9500 -E http.port=9201 -E path.data=../remote1`
2. Install sample data to remote cluster
    1. Add `elasticsearch.hosts: ["http://localhost:9201"]` to kibana.dev.yml
    2. run `yarn start` to start kibana process
    3. install sample web logs data set on home page
    4. stop kibana process
    5. remove `elasticsearch.hosts` from kibana.dev.yml
3. Start local elasticsearch by running: `yarn es snapshot -E path.data=../local1`
4. Start kibana
5. Add remote cluster under "Stack management -> Remote clusters"
    1. Set **Name** to "remote1"
    2. Set **Seed nodes** to "localhost:9500" 
5. install sample web logs data set
6. Add remote cluster to data view
    1. Edit "Kibana Sample Data Logs" data view
    2. Set **Index pattern** to `kibana_sample_data_logs,remote1:kibana_sample_data_logs`

### Simulate errors
1. Open sample web logs dashboard
2. Add filter with custom DSL
   ```
   {
      "error_query": {
        "indices": [
          {
            "name": "remote1:*",
            "error_type": "exception",
            "message": "remove exception"
          }
        ]
      }
    }
   ```
   ![image](https://github.com/nreese/notes/assets/373691/ee7921ba-8c0d-42e2-b540-354feddb413e)

