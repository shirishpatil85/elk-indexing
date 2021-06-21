# Elastic search APIs

- PUT INDEXNAME {settings, shards}
- POST /INDEXNAME/_doc/id=1,2etc {..}   // _doc type is for json, for update version gets updated, 201 if index created
- POST /_bulk {}                        // bulk upload
- POST /_cat/indices                    // lists indices, status as well yellow, green etc
- POST /_cluster/health
- POST /_nodes/stats

# Kibana

- Create index with pattern logstash* for all log files, add logstash pipleines as well
- Upload csv for analysis - settings, index name, sharding, mapping of fields - text, keyword etc
- Dev tools to query elastic search

# Inverted Index

- pre processing  : stopwords (a, the, an, because), stemming (root words), noise (url, hashtags etc)
- term , freq, multidimensional array occurance [[doc1], [position]]...

# Applications

- Realtime search on documents
- Log analysis or CSV analysis
- ML : NLP pre processing for text classification application e.g. spam emails
