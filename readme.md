# Mosquitto config

## Basic brokers

Run a dummy master mosquitto on port `1883`

```text
mosquitto -v -p 1883
```

Configure a bridge `mosquitto_clinet_broker.conf`

```conf
connection bridge_01
address 127.0.0.1:1883

topic # out 0
topic # in 0

listener 51883
```

Run the bridge on port `51883`

```text
mosquitto -c .\mosquitto_clinet_broker.conf -v
```

## testing with clients

Subscribe to master

```text
mosquitto_sub -u adel -t '/greetings' -p 1883 -h '127.0.0.1'
```

Publish to Bridge

```text
mosquitto_pub -u ilies -t '/greetings' -p 51883 -h '127.0.0.1' -m 'hey'
```