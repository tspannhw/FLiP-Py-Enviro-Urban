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

Similar to 

````
{
  "nickname": "outside-pulsar", 
  "model": "urban",
  "uid": "e6614c775b8c4035", 
  "timestamp": "2022-09-04T10:40:24Z", 
  "readings": {
    "temperature": 27.57, 
    "humidity": 49.33, 
    "pressure": 996.22, 
    "noise": 0.41, 
    "pm1": 0.0, 
    "pm2_5": 0.0, 
    "pm10": 0.0, 
    "voltage": 4.954
  }
}
````

#### Sending Data to MQTT -> MoP -> Pulsar

#### References

* https://shop.pimoroni.com/products/enviro-urban?variant=40056508252243
* https://shop.pimoroni.com/products/weatherproof-cover-for-outdoor-sensors?variant=40047884468307
* https://github.com/pimoroni/enviro/blob/main/documentation/getting-started.md
* https://github.com/pimoroni/enviro/blob/main/documentation/destinations/mqtt.md

#### Projects

https://github.com/tspannhw/FLiP-Pico-Enviro-MQTT

