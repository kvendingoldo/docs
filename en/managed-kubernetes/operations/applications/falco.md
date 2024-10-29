# Installing Falco


[The Falco Project](https://falco.org/) is intended to secure the operation of Linux-based operating systems.

The Falco application:
* Parses Linux kernel system calls at runtime.
* Analyzes signals using a configurable set of rules.
* Sends an alert if the rules are violated.

{% note warning %}

To use Falco, install [Kyverno](/marketplace/products/yc/kyverno) or another product that supports writing results to [wg-policy-prototypes](https://github.com/kubernetes-sigs/wg-policy-prototypes/blob/master/policy-report/README.md).

{% endnote %}

## Getting started {#before-you-begin}

{% include [check-sg-prerequsites](../../../_includes/managed-kubernetes/security-groups/check-sg-prerequsites-lvl3.md) %}

{% include [sg-common-warning](../../../_includes/managed-kubernetes/security-groups/sg-common-warning.md) %}

## Installation using {{ marketplace-full-name }} {#marketplace-install}

1. Go to the [folder page]({{ link-console-main }}) and select **{{ ui-key.yacloud.iam.folder.dashboard.label_managed-kubernetes }}**.
1. Click the name of the [{{ managed-k8s-name }} cluster](../../concepts/index.md#kubernetes-cluster) you need and select the ![image](../../../_assets/console-icons/shopping-cart.svg) **{{ ui-key.yacloud.k8s.cluster.switch_marketplace }}** tab.
1. Under **{{ ui-key.yacloud.marketplace-v2.label_available-products }}**, select [Falco](/marketplace/products/yc/falco) and click **{{ ui-key.yacloud.marketplace-v2.button_k8s-product-use }}**.
1. Configure the application:
   * **Namespace**: Select or create a [namespace](../../concepts/index.md#namespace) for Falco.
   * **Application name**: Specify the app name.
1. Click **{{ ui-key.yacloud.k8s.cluster.marketplace.button_install }}**.
1. Wait for the application to change its status to `Deployed`.

## Installation using a Helm chart {#helm-install}

1. {% include [helm-install](../../../_includes/managed-kubernetes/helm-install.md) %}

1. {% include [kubectl-install](../../../_includes/managed-kubernetes/kubectl-install.md) %}

1. To install a [Helm chart](https://helm.sh/docs/topics/charts/) with Falco, run the following command:

   ```bash
   helm pull oci://{{ mkt-k8s-key.yc_falco.helmChart.name }} \
     --version {{ mkt-k8s-key.yc_falco.helmChart.tag }} \
     --untar && \
   helm install \
     --namespace <namespace> \
     --create-namespace \
     falco ./falco
   ```

   {% include [Support OCI](../../../_includes/managed-kubernetes/note-helm-experimental-oci.md) %}

## See also {#see-also}

* [Falco documentation](https://falco.org/docs/)
