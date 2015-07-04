---
title: Cloud Processing Engine Client SDK reference

language_tabs:
  - php: PHP

toc_footers:
  - <a href='http://sportarchive.github.io/CloudProcessingEngine/' target="_blank">CPE Project doc</a>

includes:
  - sending
  - listening
  - outputs
  - errors

search: true
---

# Introduction

> A PHP implementation of this SDK is available here:<br>
> <a href="https://github.com/sportarchive/CloudProcessingEngine-PHP-Client-SDK" target="_blank">https://github.com/sportarchive/CloudTranscode-PHP-SDK</a>

Welcome to the Cloud Processing Engine (CPE) Client SDK documentation.

The CPE Client SDK allows you to communicate with the CPE stack through AWS SQS.
You can use it to:

   - Submit Jobs to the stack
   - Listen for jobs output

It is a simple AWS SQS interface. It reads and writes the proper JSON format expected by the CT stack.

# Dependencies

```json
{
	"name": "YOUR CLIENT NAME",
	"queues": {
		  "input": "https://sqs.[region].amazonaws.com/[AWS account]/[sqs-input-queue-name]",
		  "output": "https://sqs.[region].amazonaws.com/[AWS account]/[sqs-output-queue-name]"
	}
}
```

Before integrating the SDK into your application, you must register your application (client) into the CPE stack.

The stack maintains a list of clients in its configuration file.
Each client has the following information:

   - name: The name of the client.
   - queues: The input and output SQS queues dedicated for this client.

Make a copy of the JSON object defining your client and save into your application.

The SDK will use your client definition in order to know the SQS queues to use for reading and writing messages. It expects a raw JSON text.

# Install

> Use Composer to install the PHP SDK<br>
> <a href="https://packagist.org/packages/sportarchive/cloud-processing-engine-php-client-sdk" target="_blank">https://packagist.org/packages/sportarchive/cloud-processing-engine-php-client-sdk</a>

```json
{
    "require":
    {
        "sportarchive/cloud-processing-engine-php-client-sdk": "dev-master"
    }
}
```

Install the SDK in your project using the proper dependency manager for your language.

<aside class="notice">
You can also install it by hand by just copying the file in your project.
</aside>

# Instantiate

> Pass your AWS credentials to the constructor and your client JSON .

```ruby
/* Composer autoload to be at the top of your file */
require __DIR__ . "/../vendor/autoload.php";

$CTComSDK = new SA\CTComSDK($key, $secret, $region, $client_def, $debug);
```

In your application, instantiate the SDK to access its methods.

   - key: AWS Key
   - secret: AWS Secret
   - region: AWS region
   - client_def: String containg JSON client definition (same as in the Stack config file)


