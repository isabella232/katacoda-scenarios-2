In the previous scenarios we've defined the static configuration. However this has made it difficult to reload the configuration when changes are required. To solve this, the static configuration can be defined as **Dynamic Configuration**. With Dynamic Configuration, when changes are made, Envoy will automatically reload the changes and apply them to the configuration and traffic routing.

Envoy supports different parts of the configuration as dynamic. The APIs available are:

* **EDS**: The Endpoint Discovery Service (EDS) API provides a way Envoy can discover members of an upstream cluster. This allows you to dynamically add and remove servers handling the traffic.

* **CDS**: The cluster discovery service (CDS) API layers on a mechanism by which Envoy can discover upstream clusters used during routing. 

* **RDS**: The route discovery service (RDS) API layers on a mechanism by which Envoy can discover the entire route configuration for an HTTP connection manager filter at runtime.

* **LDS**: The listener discovery service (LDS) layers on a mechanism by which Envoy can discover entire listeners at runtime. 

* **SDS**: The secret discovery service (SDS) layers on a mechanism by which Envoy can discover cryptographic secrets (certificate plus private key, TLS session ticket keys) for its listeners, as well as the configuration of peer certificate validation logic (trusted root certs, revocations, etc).

The value for configuration can come from the filesystem, REST-JSON or gRPC endpoints.

More information can be found in the [Envoy documentation overview](https://www.envoyproxy.io/docs/envoy/latest/intro/arch_overview/dynamic_configuration)

In the next steps, we'll change our configuration to use **EDS** allowing nodes to be dynamically added based with data coming from the filesystem.