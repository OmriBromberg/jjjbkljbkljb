logstash-input-elasticsearch_dynamic_aggregator
====================

Apache Kafka input for Logstash. This input will consume messages from a Kafka topic using the high level consumer API exposed by Kafka. 

For more information about Kafka, refer to this [documentation](http://kafka.apache.org/documentation.html) 

Information about high level consumer API can be found [here](http://kafka.apache.org/documentation.html#highlevelconsumerapi)

Logstash Configuration
====================

See https://github.com/OmriBromberg/elasticsearch-datemath for details about the elasticsearch-datemath library.

| Setting       | Input Type    | Required | Default |
| ------------- | ------------- | -------- | ------- |
| [`start_time`](#start_time)    | string, datemath expression        | No       |  now-1d |
| [`end_time`](#end_time)      | string, datemath expression |   No    |  now    [This is the link text](#headin)|
| [`datetime_format`](#datetime_format)| string, valid java 8 time format     |    No   | yyyy.MM.dd|
| [`index_format`](#index_format)   | string, valid java 8 time format        | No       |  yyyy.Mm.dd |
| [`retries`](#retries)      | number, n >= 0      |   No    |  0    |
| [`threads`](#threads) | number, n > 0     |    No   | 1|
| [`schedule`](#schedule)    | hash, valid rufus-scheduler type `{in|at|every|cron => x}`       | Yes       |   |


    input {
        elasticsearch_dynamic_aggregator {
            start_time => ... # string (optional), default: 'now-1d', Datemath expression.
            end_time => ... # string (optional), default: 'now', Datemath expression.
            datetime_format => ... # string (optional), default: 'yyyy.MM.dd', Pattern of the datetime in the datemath expressions (start_time, end_time).
            index_format => ... # string (optional), default: 'yyyy.MM.dd', Pattern of the formatted indices.
            retries => ... # number (optional), default: 0, Specifies the number of retires each query will do in case of a failure.
            threads => ... # number (optional), default: 1, Specifies the number of simultaneous threads used to query.
        }
    }
##### `start_time`
- Value type is string
- default value is `"now-1d"`

The datemath expression used to determine the start datetime of the formatted indices

##### `end_time`
- Value type is string
- default value is `"now"`

The datemath expression used to determine the end datetime of the formatted indices

##### `datetime_format`
- Value type is string
- default value is `"yyyy.MM.dd"`

The datetime format used for the start and end datemath expressions

##### `index_format`
- Value type is string
- default value is `"yyyy.MM.dd"`

The datetime format for the formatted indices

##### `retries`
- Value type is number
- default value is `0`

The number of retries used if the query fails

##### `threads`
- Value type is number
- default value is `1`

The number of simultaneous threads used to query

##### `schedule`
- Value type is hash
- There is no default value for this setting.

The setting used to configure the scheduler type. valid rufus-scheduler type `{in|at|every|cron => x}`

The default codec is json 
[create an anchor](#Dependencies)

Dependencies
====================

* elasticsearch-datemath version 0.4.1
* elasticsearch logstash input
