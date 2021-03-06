
```
{
  $schema: https://vega.github.io/schema/vega/v5.json
  config: {
    kibana: {type: "map", latitude: 25, longitude: -40, zoom: 3}
  }
  data: [
    {
      name: table
      url: {
        index: kibana_sample_data_ecommerce
        %context%: true
        // %timefield%: timestamp
        body: {
          size: 0
          aggs: {
            gridSplit: {
              geotile_grid: {field: "geoip.location", precision: 4, size: 10000}
              aggs: {
                gridCentroid: {
                  geo_centroid: {
                    field: "geoip.location"
                  }
                }
              }
            }
          }
        }
      }
      format: {property: "aggregations.gridSplit.buckets"}
      transform: [
        {
          type: geopoint
          projection: projection
          fields: [
            gridCentroid.location.lon
            gridCentroid.location.lat
          ]
        }
      ]
    }
  ]
  scales: [
    {
      name: gridSize
      type: linear
      domain: {data: "table", field: "doc_count"}
      range: [
        500
        1000
      ]
    }
  ]
  marks: [
    {
      name: gridMarker
      type: symbol
      from: {data: "table"}
      encode: {
        update: {
          size: {scale: "gridSize", field: "doc_count"}
          xc: {signal: "datum.x"}
          yc: {signal: "datum.y"}
        }
      }
    }
  ]
}
```
