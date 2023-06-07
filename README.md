# FLiP-Py-Enviro-Urban

Apache Pulsar + MQTT + Pimoroni Enviro Urban + Raspberry Pi Pico

https://github.com/pimoroni/enviro/blob/main/documentation/getting-started.md

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

#### Stream of Messages

````

----- got message -----
key:[null], properties:[], content:{value={"pm10": 6, "pressure": 1007.75, "device": "pulsaroutside", "pm2_5": 6, "noise": 1.51, "humidity": 31.81, "timestamp": "2022-10-19 16:03:09", "temperature": 27.08, "pm1": 2}, type=class java.lang.String}
----- got message -----
key:[null], properties:[], content:{value={"pm10": 6, "pressure": 1008.04, "device": "pulsaroutside", "pm2_5": 6, "noise": 1.5, "humidity": 28.44, "timestamp": "2022-10-19 16:06:42", "temperature": 26.79, "pm1": 4}, type=class java.lang.String}
----- got message -----
key:[null], properties:[], content:{value={"pm10": 8, "pressure": 1008.13, "device": "pulsaroutside", "pm2_5": 8, "noise": 1.51, "humidity": 30.99, "timestamp": "2022-10-19 16:07:23", "temperature": 26.65, "pm1": 4}, type=class java.lang.String}
----- got message -----
key:[null], properties:[], content:{value={"pm10": 2, "pressure": 1007.97, "device": "pulsaroutside", "pm2_5": 2, "noise": 1.51, "humidity": 29.38, "timestamp": "2022-10-19 16:12:09", "temperature": 24.26, "pm1": 0}, type=class java.lang.String}
----- got message -----
key:[null], properties:[], content:{value={"pm10": 4, "pressure": 1008.06, "device": "pulsaroutside", "pm2_5": 4, "noise": 1.51, "humidity": 31.33, "timestamp": "2022-10-19 16:17:09", "temperature": 22.89, "pm1": 2}, type=class java.lang.String}
----- got message -----
key:[null], properties:[], content:{value={"pm10": 4, "pressure": 1008.18, "device": "pulsaroutside", "pm2_5": 4, "noise": 1.51, "humidity": 32.55, "timestamp": "2022-10-19 16:22:09", "temperature": 22.12, "pm1": 0}, type=class java.lang.String}
----- got message -----
key:[null], properties:[], content:{value={"pm10": 6, "pressure": 1008.12, "device": "pulsaroutside", "pm2_5": 6, "noise": 1.51, "humidity": 33.72, "timestamp": "2022-10-19 16:23:34", "temperature": 22.14, "pm1": 0}, type=class java.lang.String}
----- got message -----
key:[null], properties:[], content:{value={"pm10": 6, "pressure": 1008.08, "device": "pulsaroutside", "pm2_5": 6, "noise": 1.51, "humidity": 33.9, "timestamp": "2022-10-19 16:24:13", "temperature": 22.55, "pm1": 2}, type=class java.lang.String}
----- got message -----
key:[null], properties:[], content:{value={"pm10": 6, "pressure": 1008.08, "device": "pulsaroutside", "pm2_5": 6, "noise": 1.51, "humidity": 30.0, "timestamp": "2022-10-19 16:29:09", "temperature": 24.45, "pm1": 2}, type=class java.lang.String}
----- got message -----
key:[null], properties:[], content:{value={"pm10": 8, "pressure": 1008.01, "device": "pulsaroutside", "pm2_5": 8, "noise": 1.51, "humidity": 29.53, "timestamp": "2022-10-19 16:34:09", "temperature": 25.14, "pm1": 2}, type=class java.lang.String}
----- got message -----
key:[null], properties:[], content:{value={"pm10": 6, "pressure": 1007.94, "device": "pulsaroutside", "pm2_5": 6, "noise": 1.51, "humidity": 28.44, "timestamp": "2022-10-19 16:39:09", "temperature": 25.56, "pm1": 0}, type=class java.lang.String}
----- got message -----
key:[null], properties:[], content:{value={"pm10": 4, "pressure": 1007.89, "device": "pulsaroutside", "pm2_5": 4, "noise": 1.51, "humidity": 27.83, "timestamp": "2022-10-19 16:44:09", "temperature": 25.78, "pm1": 0}, type=class java.lang.String}
----- got message -----
key:[null], properties:[], content:{value={"pm10": 4, "pressure": 1007.79, "device": "pulsaroutside", "pm2_5": 4, "noise": 1.51, "humidity": 27.46, "timestamp": "2022-10-19 16:49:09", "temperature": 25.89, "pm1": 2}, type=class java.lang.String}
----- got message -----
key:[null], properties:[], content:{value={"pm10": 6, "pressure": 1007.74, "device": "pulsaroutside", "pm2_5": 6, "noise": 1.51, "humidity": 27.26, "timestamp": "2022-10-19 16:54:09", "temperature": 25.96, "pm1": 2}, type=class java.lang.String}
----- got message -----
key:[null], properties:[], content:{value={"pm10": 6, "pressure": 1007.79, "device": "pulsaroutside", "pm2_5": 6, "noise": 1.51, "humidity": 27.15, "timestamp": "2022-10-19 16:59:09", "temperature": 26.05, "pm1": 0}, type=class java.lang.String}
----- got message -----
key:[null], properties:[], content:{value={"pm10": 6, "pressure": 1007.68, "device": "pulsaroutside", "pm2_5": 6, "noise": 1.51, "humidity": 27.11, "timestamp": "2022-10-19 17:04:09", "temperature": 26.1, "pm1": 0}, type=class java.lang.String}
----- got message -----
key:[null], properties:[], content:{value={"pm10": 6, "pressure": 1007.58, "device": "pulsaroutside", "pm2_5": 6, "noise": 1.51, "humidity": 27.12, "timestamp": "2022-10-19 17:09:09", "temperature": 26.13, "pm1": 2}, type=class java.lang.String}
----- got message -----
key:[null], properties:[], content:{value={"pm10": 6, "pressure": 1007.45, "device": "pulsaroutside", "pm2_5": 6, "noise": 1.51, "humidity": 27.15, "timestamp": "2022-10-19 17:14:09", "temperature": 26.21, "pm1": 0}, type=class java.lang.String}
----- got message -----
key:[null], properties:[], content:{value={"pm10": 6, "pressure": 1007.41, "device": "pulsaroutside", "pm2_5": 6, "noise": 1.51, "humidity": 27.26, "timestamp": "2022-10-19 17:19:09", "temperature": 26.35, "pm1": 0}, type=class java.lang.String}
----- got message -----
key:[null], properties:[], content:{value={"pm10": 4, "pressure": 1007.4, "device": "pulsaroutside", "pm2_5": 4, "noise": 1.51, "humidity": 27.32, "timestamp": "2022-10-19 17:24:09", "temperature": 26.47, "pm1": 2}, type=class java.lang.String}
----- got message -----
key:[null], properties:[], content:{value={"pm10": 4, "pressure": 1007.29, "device": "pulsaroutside", "pm2_5": 4, "noise": 1.51, "humidity": 27.29, "timestamp": "2022-10-19 17:29:09", "temperature": 26.54, "pm1": 2}, type=class java.lang.String}
----- got message -----
key:[null], properties:[], content:{value={"pm10": 4, "pressure": 1007.37, "device": "pulsaroutside", "pm2_5": 4, "noise": 1.51, "humidity": 27.17, "timestamp": "2022-10-19 17:34:09", "temperature": 26.59, "pm1": 2}, type=class java.lang.String}
----- got message -----
key:[null], properties:[], content:{value={"pm10": 4, "pressure": 1007.35, "device": "pulsaroutside", "pm2_5": 4, "noise": 1.51, "humidity": 27.64, "timestamp": "2022-10-19 17:39:09", "temperature": 26.13, "pm1": 2}, type=class java.lang.String}
----- got message -----
key:[null], properties:[], content:{value={"pm10": 6, "pressure": 1007.4, "device": "pulsaroutside", "pm2_5": 6, "noise": 1.51, "humidity": 31.81, "timestamp": "2022-10-19 17:44:09", "temperature": 24.19, "pm1": 2}, type=class java.lang.String}
----- got message -----
key:[null], properties:[], content:{value={"pm10": 8, "pressure": 1007.43, "device": "pulsaroutside", "pm2_5": 8, "noise": 1.51, "humidity": 32.48, "timestamp": "2022-10-19 17:49:09", "temperature": 23.58, "pm1": 4}, type=class java.lang.String}
----- got message -----
key:[null], properties:[], content:{value={"pm10": 4, "pressure": 1007.57, "device": "pulsaroutside", "pm2_5": 4, "noise": 1.51, "humidity": 32.6, "timestamp": "2022-10-19 17:54:09", "temperature": 23.29, "pm1": 2}, type=class java.lang.String}
----- got message -----
key:[null], properties:[], content:{value={"pm10": 4, "pressure": 1007.47, "device": "pulsaroutside", "pm2_5": 4, "noise": 1.51, "humidity": 32.63, "timestamp": "2022-10-19 17:59:09", "temperature": 23.01, "pm1": 0}, type=class java.lang.String}
----- got message -----
key:[null], properties:[], content:{value={"pm10": 4, "pressure": 1007.53, "device": "pulsaroutside", "pm2_5": 4, "noise": 1.51, "humidity": 33.0, "timestamp": "2022-10-19 18:04:09", "temperature": 22.74, "pm1": 2}, type=class java.lang.String}

````

![Device](https://github.com/tspannhw/FLiP-Py-Enviro-Urban/raw/main/envirourban.jpg)

![DeviceBack](https://github.com/tspannhw/FLiP-Py-Enviro-Urban/raw/main/envirourbanback.jpg)

#### Sending Data to MQTT -> MoP -> Pulsar

![MQTT](https://raw.githubusercontent.com/tspannhw/FLiP-Py-Enviro-Urban/main/urbanmqtt.png)

#### Pulsar Cluster Settings for MoP

````
messagingProtocols=mqtt,amqp,kafka

# directory
protocolHandlerDirectory=./protocols

# mqtt 3.1.1
mqttListeners=mqtt://127.0.0.1:1883
advertisedAddress=127.0.0.1

````

#### References

* https://shop.pimoroni.com/products/enviro-urban?variant=40056508252243
* https://shop.pimoroni.com/products/weatherproof-cover-for-outdoor-sensors?variant=40047884468307
* https://github.com/pimoroni/enviro/blob/main/documentation/getting-started.md
* https://github.com/pimoroni/enviro/blob/main/documentation/destinations/mqtt.md
* https://github.com/tspannhw/FLiP-Current22-LetsMonitorAllTheThings
* https://github.com/tspannhw/pulsar-adafruit-funhouse

#### Projects

https://github.com/tspannhw/FLiP-Pico-Enviro-MQTT

