# API Docs - v1.0.3

## Sink

### sqs *<a target="_blank" href="https://wso2.github.io/siddhi/documentation/siddhi-4.0/#sink">(Sink)</a>*

<p style="word-wrap: break-word">SQS sink allows users to connect and publish messages to an AWS SQS Queue. It has the ability to only publish Text messages</p>

<span id="syntax" class="md-typeset" style="display: block; font-weight: bold;">Syntax</span>
```
@sink(type="sqs", queue="<STRING>", access.key="<STRING>", secret.key="<STRING>", region="<STRING>", message.group.id="<STRING>", deduplication.id="<STRING>", delay.interval="<INT>", @map(...)))
```

<span id="query-parameters" class="md-typeset" style="display: block; color: rgba(0, 0, 0, 0.54); font-size: 12.8px; font-weight: bold;">QUERY PARAMETERS</span>
<table>
    <tr>
        <th>Name</th>
        <th style="min-width: 20em">Description</th>
        <th>Default Value</th>
        <th>Possible Data Types</th>
        <th>Optional</th>
        <th>Dynamic</th>
    </tr>
    <tr>
        <td style="vertical-align: top">queue</td>
        <td style="vertical-align: top; word-wrap: break-word">Queue url which SQS Sink should connect to</td>
        <td style="vertical-align: top"></td>
        <td style="vertical-align: top">STRING</td>
        <td style="vertical-align: top">No</td>
        <td style="vertical-align: top">No</td>
    </tr>
    <tr>
        <td style="vertical-align: top">access.key</td>
        <td style="vertical-align: top; word-wrap: break-word">Access Key for the Amazon Web Services. (This is a mandatory field and should be provided either in the deployment.yml or in the sink definition itself)</td>
        <td style="vertical-align: top">none</td>
        <td style="vertical-align: top">STRING</td>
        <td style="vertical-align: top">Yes</td>
        <td style="vertical-align: top">No</td>
    </tr>
    <tr>
        <td style="vertical-align: top">secret.key</td>
        <td style="vertical-align: top; word-wrap: break-word">Secret Key of the Amazon User. (This is a mandatory field and should be provided either in the deployment.yml or in the sink definition itself)</td>
        <td style="vertical-align: top">none</td>
        <td style="vertical-align: top">STRING</td>
        <td style="vertical-align: top">Yes</td>
        <td style="vertical-align: top">No</td>
    </tr>
    <tr>
        <td style="vertical-align: top">region</td>
        <td style="vertical-align: top; word-wrap: break-word">Amazon Web Service Region</td>
        <td style="vertical-align: top"></td>
        <td style="vertical-align: top">STRING</td>
        <td style="vertical-align: top">No</td>
        <td style="vertical-align: top">No</td>
    </tr>
    <tr>
        <td style="vertical-align: top">message.group.id</td>
        <td style="vertical-align: top; word-wrap: break-word">ID of the group that the message belong to(only applicable for FIFO Queues)</td>
        <td style="vertical-align: top">null</td>
        <td style="vertical-align: top">STRING</td>
        <td style="vertical-align: top">Yes</td>
        <td style="vertical-align: top">Yes</td>
    </tr>
    <tr>
        <td style="vertical-align: top">deduplication.id</td>
        <td style="vertical-align: top; word-wrap: break-word">ID by which a FIFO queue identifies the duplication in the queue(only applicable for FIFO queues)</td>
        <td style="vertical-align: top">null</td>
        <td style="vertical-align: top">STRING</td>
        <td style="vertical-align: top">Yes</td>
        <td style="vertical-align: top">Yes</td>
    </tr>
    <tr>
        <td style="vertical-align: top">delay.interval</td>
        <td style="vertical-align: top; word-wrap: break-word">Time in seconds for how long the message remain in the queue until it is available for the consumers to consume.</td>
        <td style="vertical-align: top">-1</td>
        <td style="vertical-align: top">INT</td>
        <td style="vertical-align: top">Yes</td>
        <td style="vertical-align: top">No</td>
    </tr>
</table>

<span id="examples" class="md-typeset" style="display: block; font-weight: bold;">Examples</span>
<span id="example-1" class="md-typeset" style="display: block; color: rgba(0, 0, 0, 0.54); font-size: 12.8px; font-weight: bold;">EXAMPLE 1</span>
```
@sink(type='sqs',queue='<queue_url>',access.key='<aws_access_key>',secret.key='<aws_secret_key>',region='<region>',delay.interval='5',deduplication.id='{{deduplicationID}}',message.group.id='charuka',@map(type='xml') )define stream outStream(symbol string, deduplicationID string);
```
<p style="word-wrap: break-word">Following Example shows how to define a SQS sink to publish messages to the service</p>

## Source

### sqs *<a target="_blank" href="https://wso2.github.io/siddhi/documentation/siddhi-4.0/#source">(Source)</a>*

<p style="word-wrap: break-word">SQS source allows users to connect and consume messages from a AWS SQS Queue. It has the ability to receive Text messages</p>

<span id="syntax" class="md-typeset" style="display: block; font-weight: bold;">Syntax</span>
```
@source(type="sqs", queue="<STRING>", access.key="<STRING>", secret.key="<STRING>", region="<STRING>", polling.interval="<INT>", wait.time="<INT>", max.number.of.messages="<INT>", visibility.timeout="<INT>", delete.messages="<BOOL>", delete.retry.interval="<INT>", max.number.of.delete.retry.attempts="<INT>", number.of.parallel.consumers="<INT>", @map(...)))
```

<span id="query-parameters" class="md-typeset" style="display: block; color: rgba(0, 0, 0, 0.54); font-size: 12.8px; font-weight: bold;">QUERY PARAMETERS</span>
<table>
    <tr>
        <th>Name</th>
        <th style="min-width: 20em">Description</th>
        <th>Default Value</th>
        <th>Possible Data Types</th>
        <th>Optional</th>
        <th>Dynamic</th>
    </tr>
    <tr>
        <td style="vertical-align: top">queue</td>
        <td style="vertical-align: top; word-wrap: break-word">Queue name which SQS Source should subscribe to</td>
        <td style="vertical-align: top"></td>
        <td style="vertical-align: top">STRING</td>
        <td style="vertical-align: top">No</td>
        <td style="vertical-align: top">No</td>
    </tr>
    <tr>
        <td style="vertical-align: top">access.key</td>
        <td style="vertical-align: top; word-wrap: break-word">Access Key for the Amazon Web Services. (This is a mandatory field and should be provided either in the deployment.yml or in the source definition itself)</td>
        <td style="vertical-align: top">null</td>
        <td style="vertical-align: top">STRING</td>
        <td style="vertical-align: top">Yes</td>
        <td style="vertical-align: top">No</td>
    </tr>
    <tr>
        <td style="vertical-align: top">secret.key</td>
        <td style="vertical-align: top; word-wrap: break-word">Secret Key of the Amazon User. (This is a mandatory field and should be provided either in the deployment.yml or in the source definition itself)</td>
        <td style="vertical-align: top">null</td>
        <td style="vertical-align: top">STRING</td>
        <td style="vertical-align: top">Yes</td>
        <td style="vertical-align: top">No</td>
    </tr>
    <tr>
        <td style="vertical-align: top">region</td>
        <td style="vertical-align: top; word-wrap: break-word">Amazon Web Service Region</td>
        <td style="vertical-align: top"></td>
        <td style="vertical-align: top">STRING</td>
        <td style="vertical-align: top">No</td>
        <td style="vertical-align: top">No</td>
    </tr>
    <tr>
        <td style="vertical-align: top">polling.interval</td>
        <td style="vertical-align: top; word-wrap: break-word">Interval (in milliseconds) between two message retrieval operations</td>
        <td style="vertical-align: top"></td>
        <td style="vertical-align: top">INT</td>
        <td style="vertical-align: top">No</td>
        <td style="vertical-align: top">No</td>
    </tr>
    <tr>
        <td style="vertical-align: top">wait.time</td>
        <td style="vertical-align: top; word-wrap: break-word">Maximum amount (in seconds) that a polling call will wait for a message to become available in the queue</td>
        <td style="vertical-align: top">-1</td>
        <td style="vertical-align: top">INT</td>
        <td style="vertical-align: top">Yes</td>
        <td style="vertical-align: top">No</td>
    </tr>
    <tr>
        <td style="vertical-align: top">max.number.of.messages</td>
        <td style="vertical-align: top; word-wrap: break-word">Maximum number of messages retrieved from the queue per polling call (Actual maybe smaller than this even if there's more messages in the queue)</td>
        <td style="vertical-align: top">1</td>
        <td style="vertical-align: top">INT</td>
        <td style="vertical-align: top">No</td>
        <td style="vertical-align: top">No</td>
    </tr>
    <tr>
        <td style="vertical-align: top">visibility.timeout</td>
        <td style="vertical-align: top; word-wrap: break-word">The length of time (in seconds) for which a message received from a queue will be invisible to other consumers(only applicable if consumer doesn't purge the received messages from the queue).</td>
        <td style="vertical-align: top">-1</td>
        <td style="vertical-align: top">INT</td>
        <td style="vertical-align: top">Yes</td>
        <td style="vertical-align: top">No</td>
    </tr>
    <tr>
        <td style="vertical-align: top">delete.messages</td>
        <td style="vertical-align: top; word-wrap: break-word">Should the message be deleted from the queue after consuming it.</td>
        <td style="vertical-align: top">delete.messages</td>
        <td style="vertical-align: top">BOOL</td>
        <td style="vertical-align: top">Yes</td>
        <td style="vertical-align: top">No</td>
    </tr>
    <tr>
        <td style="vertical-align: top">delete.retry.interval</td>
        <td style="vertical-align: top; word-wrap: break-word">Time interval (in milliseconds) consumer should retry to delete a message in the case of failure during a message delete operation.</td>
        <td style="vertical-align: top">5000</td>
        <td style="vertical-align: top">INT</td>
        <td style="vertical-align: top">Yes</td>
        <td style="vertical-align: top">No</td>
    </tr>
    <tr>
        <td style="vertical-align: top">max.number.of.delete.retry.attempts</td>
        <td style="vertical-align: top; word-wrap: break-word">Maximum number retry attempts to be performed in case of a failure.</td>
        <td style="vertical-align: top">10</td>
        <td style="vertical-align: top">INT</td>
        <td style="vertical-align: top">Yes</td>
        <td style="vertical-align: top">No</td>
    </tr>
    <tr>
        <td style="vertical-align: top">number.of.parallel.consumers</td>
        <td style="vertical-align: top; word-wrap: break-word">Size of the thread pool that should be used for polling.</td>
        <td style="vertical-align: top">1</td>
        <td style="vertical-align: top">INT</td>
        <td style="vertical-align: top">No</td>
        <td style="vertical-align: top">No</td>
    </tr>
</table>

<span id="examples" class="md-typeset" style="display: block; font-weight: bold;">Examples</span>
<span id="example-1" class="md-typeset" style="display: block; color: rgba(0, 0, 0, 0.54); font-size: 12.8px; font-weight: bold;">EXAMPLE 1</span>
```
@source(type='sqs',queue='<queue url>',access.key='<access_key>',secret.key='<secret_key>',region='us-east-2',polling.interval='5000',max.number.of.messages='10',number.of.parallel.consumers='1',purge.messages='true',wait.time='2',visibility.timeout='30',delete.retry.interval='1000',max.number.of.delete.retry.attempts='10',@map(type='xml',enclosing.element="//events",@attributes(symbol='symbol', message_id='trp:MESSAGE_ID') ))define stream inStream (symbol string, message_id string);
```
<p style="word-wrap: break-word">Following Example shows how to define a SQS source to receive messages from the service</p>

