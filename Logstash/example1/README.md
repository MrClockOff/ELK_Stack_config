# Logstash example 1:

## Parsing nested objects into separate documets.

The example input json:

```json
{
    "id": "1234",
    "title": "Session 1",
    "items" : [
        {
            "id" : "0987",
            "title" : "Item 1"
        },
        {
            "id" : "75758",
            "title" : "Item 2"
        },
        {
            "id" : "5646",
            "title" : "Item 3"
        }
    ],
    "values" : [
        {
            "key" : "key5445",
            "value" : "value1"
        },
        {
            "key" : "kkEy00",
            "value" : "value1456"
        }
    ]
}
```

the output in logstash:

```ruby
{
    "@timestamp" => 2018-02-26T09:21:50.842Z,
     "@metadata" => {
        "type" => "root"
    },
      "@version" => "1",
            "id" => "1234",
         "title" => "Session 1"
}
{
    "@timestamp" => 2018-02-26T09:21:50.842Z,
     "@metadata" => {
        "type" => "values"
    },
      "@version" => "1",
         "value" => "value1",
           "key" => "key5445"
}
{
    "@timestamp" => 2018-02-26T09:21:50.842Z,
     "@metadata" => {
        "type" => "values"
    },
      "@version" => "1",
         "value" => "value1456",
           "key" => "kkEy00"
}
{
    "@timestamp" => 2018-02-26T09:21:50.842Z,
     "@metadata" => {
        "type" => "items"
    },
      "@version" => "1",
            "id" => "0987",
         "title" => "Item 1"
}
{
    "@timestamp" => 2018-02-26T09:21:50.842Z,
     "@metadata" => {
        "type" => "items"
    },
      "@version" => "1",
            "id" => "75758",
         "title" => "Item 2"
}
{
    "@timestamp" => 2018-02-26T09:21:50.842Z,
     "@metadata" => {
        "type" => "items"
    },
      "@version" => "1",
            "id" => "5646",
         "title" => "Item 3"
}
```
