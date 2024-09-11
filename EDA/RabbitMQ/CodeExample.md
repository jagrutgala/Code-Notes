# Hello World Example

Lets look at a .Net Implementation of Rabbit MQ. We will need rabbitmq and .Net installed on our system and create 2 Conole Applications. These 2 Console Applications namely `Send` and `Receive` we act as producer and consumer respectively.

> **Preparations**:
> - RabbitMQ
> - .Net
> - 2 Console Applications

## Steps

**Send.cs**
1. Add Nuget package `RabbitMQ.Client`.
1. Import RabbitMQ Client
    ```cs
    using RabbitMQ.Client;
    ```
1. Create connection with the RabbitMQ Server
    ```cs
    var factory = new ConnectionFactory { HostName = "localhost" };
    using var connection = factory.CreateConnection();
    ```
1. Create channel
    ```cs
    using var channel = connection.CreateModel();
    ```
1. Declare Queue
    ```cs
    channel.QueueDeclare(
        queue: "my.routing.key",
        durable: false,
        exclusive: false,
        autoDelete: false,
        arguments: null
    );
    ```
1. Publish message to the `default` exchange
    ```cs
    const string message = "Hello World!";
    var body = Encoding.UTF8.GetBytes(message);

    channel.BasicPublish(
        exchange: string.Empty,
        routingKey: "hello",
        basicProperties: null,
        body: body
    );
    ```

**Receive.cs**
1. Add Nuget package `RabbitMQ.Client`.
1. Import RabbitMQ Client
    ```cs
    using RabbitMQ.Client;
    ```
1. Create connection with the RabbitMQ Server
    ```cs
    var factory = new ConnectionFactory { HostName = "localhost" };
    using var connection = factory.CreateConnection();
    ```
1. Create channel
    ```cs
    using var channel = connection.CreateModel();
    ```
1. Declare Queue
    ```cs
    channel.QueueDeclare(
        queue: "hello",
        durable: false,
        exclusive: false,
        autoDelete: false,
        arguments: null
    );
    ```
1. Bind consume callback
    ```cs
    var consumer = new EventingBasicConsumer(channel);
    consumer.Received += (model, ea) =>
    {
        var body = ea.Body.ToArray();
        var message = Encoding.UTF8.GetString(body);
        Console.WriteLine($" [x] Received {message}");
    };
    ```
1. Consume message from `hello` queue.
    ```cs
    channel.BasicConsume(
        queue: "hello",
        autoAck: true,
        consumer: consumer
    );
    ```

**Run both projects**

```
dotnet run
```


# 