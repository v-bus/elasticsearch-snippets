#delete indexes by wildcard
DELETE /catalog*

#list all indexes
GET /_search?size=100

#create index with analyzer
PUT /catalog
{
  "settings": {
    "index":{
      "number_of_shards": 5,
      "number_of_replicas": 2
    }
    , "analysis": {
      "analyzer": {
        "std": {
          "type": "standard",
          "stopwords": "_russian_"
        }
      }
    }
  },
  "mappings": {
    "properties": {
      "my_text": {
        "type": "text",
        "analyzer": "std"
      }
    }
  }
}
