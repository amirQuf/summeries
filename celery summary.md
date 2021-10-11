# celery summary



## [What’s a Task Queue?](https://docs.celeryproject.org/en/stable/getting-started/introduction.html#id2)¶

Task queues are used as a mechanism to distribute work across threads or machines.

A task queue’s input is a unit of work called a task. Dedicated worker processes constantly monitor task queues for new work to perform.

Celery communicates via messages, usually using a broker to mediate between clients and workers. To initiate a task the client adds a message to the queue, the broker then delivers that message to a worker.

A Celery system can consist of multiple workers and brokers, giving way to high availability and horizontal scaling.

Celery is written in Python, but the protocol can be implemented in any language. In addition to Python there’s [node-celery](https://github.com/mher/node-celery) and [node-celery-ts](https://github.com/IBM/node-celery-ts) for Node.js, and a [PHP client](https://github.com/gjedeer/celery-php).

Language interoperability can also be achieved exposing an HTTP endpoint and having a task that requests it (webhooks).

Celery is ...

- **Fast**

- **Highly Available**

- **simple**

- **felxiable**

  

  

**example:**

```python
from celery import Celery

app = Celery('hello', broker='amqp://guest@localhost//')

@app.task
def hello():
    return 'hello world'
```

it support..

- **Brokers**
- **result store**
- **concurrency**
- **serialization**

## Features

- **Monitoring**
- **Scheduling**
- **Work-flows**
- **Resource Leak Protection**
- **Time & Rate Limits**
- **User Components**



### Installation

```shell
$ pip install -U Celery
```

### Bundles

```shell
$ pip install "celery[librabbitmq]"

$ pip install "celery[librabbitmq,redis,auth,msgpack]"
```

#### Serializers

- `celery[auth]`

  for using the `auth` security serializer.

- `celery[msgpack]`

  for using the msgpack serializer.

- `celery[yaml]`

  for using the yaml serializer.

#### Concurrency

- `celery[eventlet]`

  for using the [eventlet](https://pypi.python.org/pypi/eventlet/) pool.

- `celery[gevent]`

  for using the [gevent](https://pypi.python.org/pypi/gevent/) pool.

#### Transports and Backends

- `celery[librabbitmq]`

  for using the librabbitmq C library.

- `celery[redis]`

  for using Redis as a message transport or as a result backend.

- `celery[sqs]`

  for using Amazon SQS as a message transport (*experimental*).

- `celery[tblib]`

  for using the [`task_remote_tracebacks`](https://docs.celeryproject.org/en/stable/userguide/configuration.html#std-setting-task_remote_tracebacks) feature.

- `celery[memcache]`

  for using Memcached as a result backend (using [pylibmc](https://pypi.python.org/pypi/pylibmc/))

- `celery[pymemcache]`

  for using Memcached as a result backend (pure-Python implementation).

- `celery[cassandra]`

  for using Apache Cassandra as a result backend with DataStax driver.

- `celery[couchbase]`

  for using Couchbase as a result backend.

- `celery[arangodb]`

  for using ArangoDB as a result backend.

- `celery[elasticsearch]`

  for using Elasticsearch as a result backend.

- `celery[riak]`

  for using Riak as a result backend.

- `celery[dynamodb]`

  for using AWS DynamoDB as a result backend.

- `celery[zookeeper]`

  for using Zookeeper as a message transport.

- `celery[sqlalchemy]`

  for using SQLAlchemy as a result backend (*supported*).

- `celery[pyro]`

  for using the Pyro4 message transport (*experimental*).

- `celery[slmq]`

  for using the SoftLayer Message Queue transport (*experimental*).

- `celery[consul]`

  for using the Consul.io Key/Value store as a message transport or result backend (*experimental*).

- `celery[django]`

  specifies the lowest version possible for Django support.You should probably not use this in your requirements, it’s here for informational purposes only.

  
