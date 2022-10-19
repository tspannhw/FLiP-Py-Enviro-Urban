# FLiP-Py-Enviro-Urban

Apache Pulsar + MQTT + Pimoroni Enviro Urban + Raspberry Pi Pico

#### Sensors

* https://github.com/pimoroni/enviro/blob/main/documentation/boards/enviro-urban.md

|Name|Parameter|Unit|Symbol|Example|
|---|---|---|---|---|
|Temperature|`temperature`|celcius|°C|`22.11`|
|Humidity|`humidity`|percent|%|`55.42`|
|Air Pressure|`pressure`|hectopascals|hPa|`997.16`|
|Noise|`noise`|voltage|V|`0.87`|
|PM1|`pm1`|micrograms per cubic metre|µg/m³|`9`|
|PM2.5|`pm2_5`|micrograms per cubic metre|µg/m³|`4`|
|PM10|`pm10`|micrograms per cubic metre|µg/m³|`2`|
|Voltage|`voltage`|volts|V|`4.035`|

Read

````
key:[null], properties:[], content:

value=

{"pm10": 8, "pressure": 1007.79, "device": "pulsaroutside", "pm2_5": 8, "noise": 1.51, "humidity": 29.76, 
"timestamp": "2022-10-19 15:58:09", "temperature": 26.9, "pm1": 4}


type=class java.lang.String}

````


#### Using Command Line Consumer

````

bin/pulsar-client consume
The following option is required: [-s | --subscription-name]
Consume messages from a specified topic
Usage: consume [options] TopicName
  Options:
    -ac, --auto_ack_chunk_q_full
      Auto ack for oldest message on queue is full
      Default: false
    -ekv, --encryption-key-value
      The URI of private key to decrypt payload, for example
      file:///path/to/private.key or data:application/x-pem-file;base64,*****
    --hex
      Display binary messages in hex.
      Default: false
    --hide-content
      Do not write the message to console.
      Default: false
    -mc, --max_chunked_msg
      Max pending chunk messages
      Default: 0
    -n, --num-messages
      Number of messages to consume, 0 means to consume forever.
      Default: 1
    -pm, --pool-messages
      Use the pooled message
      Default: true
    -q, --queue-size
      Consumer receiver queue size.
      Default: 0
    -r, --rate
      Rate (in msg/sec) at which to consume, value 0 means to consume messages
      as fast as possible.
      Default: 0.0
    --regex
      Indicate the topic name is a regex pattern
      Default: false
    -st, --schema-type
      Set a schema type on the consumer, it can be 'bytes' or 'auto_consume'
      Default: bytes
    -m, --subscription-mode
      Subscription mode.
      Default: Durable
      Possible Values: [Durable, NonDurable]
  * -s, --subscription-name
      Subscription name.
    -p, --subscription-position
      Subscription position.
      Default: Latest
      Possible Values: [Latest, Earliest]
    -t, --subscription-type
      Subscription type.
      Default: Exclusive
      Possible Values: [Exclusive, Shared, Failover, Key_Shared]
      
````

#### Consume Messsages

````
bin/pulsar-client consume "persistent://public/default/enviro%2Fpulsaroutside" -s "outside" -n 0


bin/pulsar-client consume "persistent://public/default/enviro%2Fpulsaroutside" -s "outside" -n 0 --subscription-type "Shared" --subscription-position "Earliest" --subscription-mode "Durable" --schema-type "auto_consume"


````

#### Sending Data to MQTT -> MoP -> Pulsar

#### References

* https://shop.pimoroni.com/products/enviro-urban?variant=40056508252243
* https://shop.pimoroni.com/products/weatherproof-cover-for-outdoor-sensors?variant=40047884468307
* https://github.com/pimoroni/enviro/blob/main/documentation/getting-started.md
* https://github.com/pimoroni/enviro/blob/main/documentation/destinations/mqtt.md
* https://github.com/tspannhw/FLiP-Current22-LetsMonitorAllTheThings

#### Projects

https://github.com/tspannhw/FLiP-Pico-Enviro-MQTT

