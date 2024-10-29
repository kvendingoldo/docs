# Fields and annotations of the Service resource

The `Service` resource defines the [{{ k8s }} service](../../../managed-kubernetes/concepts/index.md#service). Services in {{ network-load-balancer-name }} for {{ managed-k8s-name }} are load balancers for incoming traffic.

`Service` is a standard {{ k8s }} resource. This reference describes the resource's fields and annotations supported by {{ network-load-balancer-name }} for {{ managed-k8s-name }}. For a complete reference for the resource, please see the [{{ k8s }} documentation](https://kubernetes.io/docs/reference/kubernetes-api/service-resources/service-v1/).

## Service {#service}

```yaml
apiVersion: v1
kind: Service
metadata: <ObjectMeta>
spec: <ServiceSpec>
```

#|
|| **Field**     | **Value or type**   | **Description**                   ||
|| `apiVersion` | `v1` | **Required**
Kubernetes API version          ||
|| `kind`       | `Service`              | Resource type                    ||
|| `metadata`   | `ObjectMeta`           | **Required**
[Resource metadata](#metadata) ||
|| `spec`       | `ServiceSpec`          | **Required**
[Resource specification](#servicespec)   ||
|#

{% cut "Example" %}

```yaml
apiVersion: v1
kind: Service
metadata:
  name: nlb-demo-1
spec:
  selector:
    app: app-demo-1
  type: LoadBalancer
  ports:
    - port: 80
      name: plaintext
      targetPort: 8080
```

{% endcut %}

## ObjectMeta {#metadata}

```yaml
name: <string>
annotations:
  yandex.cloud/load-balancer-type: <string>
  yandex.cloud/subnet-id: <string>
  yandex.cloud/load-balancer-healthcheck-healthy-threshold: <string>
  yandex.cloud/load-balancer-healthcheck-interval: <string>
  yandex.cloud/load-balancer-healthcheck-timeout: <string>
  yandex.cloud/load-balancer-healthcheck-unhealthy-threshold: <string>
```

#|
|| **Field**      | **Value or type** | **Description** ||
|| `name`        | `string`             | **Required**
[Resource name](https://kubernetes.io/docs/concepts/overview/working-with-objects/names/#names)

Does not match the load balancer name in {{ network-load-balancer-name }} ||
|| `annotations` | `map[string]string`  | [Resource annotations](#annotations) ||
|#

### Annotations (metadata.annotations) {#annotations}

Annotations are collections of `key:value` pairs used for assigning metadata to objects. Annotation values are always of the `string` data type. See more on annotations in [the Kubernetes documentation](https://kubernetes.io/docs/concepts/overview/working-with-objects/annotations/).

You can provide the following annotations for the `ObjectMeta` object:

* **yandex.cloud/load-balancer-type**

   [Load balancer type](../../../network-load-balancer/concepts/nlb-types.md) (by default, with an external IP address).

   For a load balancer with an internal IP address, the value is `internal`.

* **yandex.cloud/subnet-id**

   ID of the subnet in which you need to allocate an IP address for the internal network load balancer.

* **yandex.cloud/load-balancer-healthcheck-healthy-threshold**

   Number of consecutive successful [checks](../../../network-load-balancer/concepts/health-check.md) to consider a node available.

   The minimum value is `2`, the maximum is `10`.

* **yandex.cloud/load-balancer-healthcheck-interval**

   [Health check](../../../network-load-balancer/concepts/health-check.md) interval in seconds.

   The minimum value is `2s`, the maximum is `300s`.

* **yandex.cloud/load-balancer-healthcheck-timeout**

   Timeout for [health checks](../../../network-load-balancer/concepts/health-check.md) in seconds. A node is considered unavailable if it has not responded within the specified time.

   The minimum value is `1s`, the maximum is `60s`.

* **yandex.cloud/load-balancer-healthcheck-unhealthy-threshold**

   Number of consecutive failed [checks](../../../network-load-balancer/concepts/health-check.md) to consider a node unavailable.

   The minimum value is `2`, the maximum is `10`.

## ServiceSpec {#servicespec}

```yaml
type: LoadBalancer
ports:
  - <ServicePort>
  - ...
loadBalancerIP: <string>
externalTrafficPolicy: <string>
```

#|
|| **Field** | **Value or type** | **Description** ||
|| `type`   | `LoadBalancer` | **Required**
Service type.

{% note warning %}

The {{ k8s }} services used as network load balancers must be of the `LoadBalancer` type. For more details on this type, please see the [{{ k8s }} documentation](https://kubernetes.io/docs/concepts/services-networking/service/#loadbalancer).

{% endnote %}
||

|| `ports`    | `[]ServicePort`      | **Required**
[List of ports the service is available on](#ports).
||

|| `loadBalancerIP` | `string` | When using an [external load balancer](../../../network-load-balancer/concepts/nlb-types.md), you can specify a static [public IP address](../../../vpc/concepts/address.md#public-addresses) in this field. You need to [reserve such an address in advance](../../../vpc/operations/get-static-ip.md). When reserving a public IP address, you can enable [DDoS protection](../../../vpc/ddos-protection/index.md).


If you do not specify a static IP address, the network load balancer will get a dynamic IP address ||
|| `externalTrafficPolicy` | `string` | [Traffic management policy]({{ k8s-api-link }}#servicespec-v1-core):

* `Cluster`: Traffic goes to any of the {{ k8s }} cluster nodes. If the required pods are not on the node, [kube-proxy](https://kubernetes.io/docs/reference/command-line-tools-reference/kube-proxy) forwards traffic to another node. Default value.
* `Local`: Traffic goes directly to the nodes where the application containers are running. In which case:

   * User request IP is saved.
   * Less horizontal traffic is exchanged between VMs.
||
|#

### ServicePort {#ports}

```yaml
port: <int32>
name: <string>
targetPort: <int32>
```

#|
|| **Field** | **Value or type** | **Description** ||
|| `port`    | `int32`      | **Required**
Port of the network load balancer to handle user requests.
||

|| `targetPort`    | `int32`      | **Required**
Container port the application is available on.
||

|| `name` | `string` | Port name within the service.
||
|#
