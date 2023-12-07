![](https://www.phonexia.com/wp-content/uploads/phonexia-logo-transparent-500px.png)

# Phonexia microservice communication via grpc library

This library contains defined interfaces for all microservices developed by [Phonexia](https://phonexia.com).

To use this library you will first need a running instance of any Phonexia microservice. If you don't yet have any running instance, don't hesitate to [contact our sales department](mailto:info@phonexia.com).

On [this page](https://docs.cloud.phonexia.com/docs/grpc/), you may find a gRPC API reference for all microservices.

## Example

### Health check

You can invoke `health check` method of any microservice like this:

```python
import grpc

from phonexia.grpc.common.health_check_pb2 import HealthCheckRequest
from phonexia.grpc.common.health_check_pb2_grpc import HealthStub


def health_check(stub: HealthStub):
    request = HealthCheckRequest()
    response = stub.Check(request)
    print(response)


def main():
    with grpc.insecure_channel("localhost:8080") as channel:
        stub = HealthStub(channel)
        health_check(stub)


if __name__ == "__main__":
    main()

```

If the microservice is running, it should return: `status: SERVING`.

### Check license

Each microservice has licensed model which is required to run the service. You can fetch information about licensed models like this:

```python
import grpc

from phonexia.grpc.common.licensing_pb2 import LicensingInfoRequest
from phonexia.grpc.common.licensing_pb2_grpc import LicensingStub


def licensing_check(stub: LicensingStub):
    request = LicensingInfoRequest()
    response = stub.Info(request)
    print(response)


def main():
    with grpc.insecure_channel("localhost:8080") as channel:
        stub = LicensingStub(channel)
        licensing_check(stub)


if __name__ == "__main__":
    main()

```

Returned message should contain information about validity until, technology name, model name and it's version.
