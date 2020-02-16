# Toto PubSub
This library supports consuming and publishing events in Toto.<br/>
Currently supports Google PubSub

## Authenticating to Google
Google pubsub requires a Service Account. In order to setup Service Accounts and authorize them to pubsub follow this [guide](https://github.com/nicolasances/guides/wiki/Guide:-GCP-Cross-project-access-to-PubSub)

## Toto Event Consumer

When including this through `require()`, a new `TotoEventConsumer` instance will be automatically created and it will be possible to consume events from kafka.

Typical usage:

```
from toto_pubsub.consumer import TotoEventConsumer

TotoEventConsumer('<ms name>', ['topic1', 'topic2'], [func1, func2])
```
Where: 
 * `func1` and `func2` are callback functions called for each of the topic (func1 will be called for topic1, etc.)

**NOTE!** that the `event` that is being passed in the callback **has already been parsed and is in JSON format**!

## Toto Event Publisher

Typical usage:

```
from toto_pubsub.publisher import TotoEventPublisher

publisher = TotoEventPublisher(microservice='<ms name>', topics=['<topic name>'])

# Post event
msg = {...};

publisher.publish(topic='<topic name>', event=msg)

```
