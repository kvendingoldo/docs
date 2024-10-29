# {{ yq-full-name }} overview

{{ yq-full-name }} is a data service that can run federated queries against [{{ objstorage-full-name }}](../../storage/concepts/index.md) object storage, [{{ mch-name }}](https://yandex.cloud/en/services/managed-clickhouse), [{{ mgp-name }}](https://yandex.cloud/en/services/managed-greenplum), [{{ mmy-name }}](https://yandex.cloud/en/services/managed-mysql), [{{ mpg-name }}](https://yandex.cloud/en/services/managed-postgresql), and [{{ ydb-name }}](https://yandex.cloud/en/services/ydb) managed databases, and [{{ yds-full-name }}](../../data-streams/concepts/index.md) real-time streams. {{ yq-full-name }} uses YQL – a unified SQL dialect – to aggregate query results [across these systems](../concepts/federated-processing.md).

{{ yq-full-name }} is a fully managed cloud service, meaning that you need no running servers with software deployed. All the resources you need for your queries are allocated the moment you run them and vacated as soon as the queries are complete. The queries themselves start running instantly.

{{ yq-full-name }} allows you to:

* Use the same written query in scenarios for analyzing data stored in {{ objstorage-full-name }} and analyzing data in real time.
* Aggregate query execution results across different systems.
* Save on development thanks to using a common query language, YQL, and a common approach.

{{ yq-full-name }} combines data virtualization features and a real-time streaming data analysis system. This architecture is called [Unified Lambda](../concepts/unified-processing.md).

![](../../_assets/query/unified-delta.png)

The Unified Lambda model uses a unified SQL query text for processing streaming data and data stored in storage systems of different classes.


## Support for raw data storage

Companies prefer to store large volumes of rarely accessed data in object storage of the {{ objstorage-full-name }} class. Long-term storage of rarely processed data in storage systems like this is most cost-efficient. Data is stored in {{ objstorage-full-name }} in unstructured form and this data needs to be processed in a simple and analyst-friendly way.

## Streaming data processing

Streaming processing is based on grouping window functions that receive data streams, group them by source and time window, make computations, and send execution results to external systems. A distinctive feature of {{ yq-full-name }} is a unified text of SQL queries used for both streaming and batch processing.

## Integration with external systems

### Streaming processing

Streaming queries can get data from the following sources:

* {{ yds-full-name }}. Application logs, [Debezium](../tutorials/debezium.md) database CDC streams, or any other information can be used as input data.

Streaming processing results are exported to:

* {{ monitoring-name }} as metrics for creating charts and dashboards or alerting.
* {{ yds-full-name }}. Using {{ data-transfer-full-name }}, data from {{ yds-full-name }} can be sent to different systems, including various DBMS.

### Batch processing {#analytic}

Analytical queries in {{ yq-full-name }} can get data from {{ objstorage-full-name }} in [JSON, CSV/TSV, and Parquet formats compressed using different algorithms](../sources-and-sinks/formats.md). You can also run analytical queries against [{{ mch-name }}](https://yandex.cloud/en/services/managed-clickhouse), [{{ mgp-name }}](https://yandex.cloud/en/services/managed-greenplum), [{{ mmy-name }}](https://yandex.cloud/en/services/managed-mysql), [{{ mpg-name }}](https://yandex.cloud/en/services/managed-postgresql), and [{{ ydb-name }}](https://yandex.cloud/en/services/ydb) managed databases.

You can use {{ yq-full-name }} for cross-service data analytics, accessing all supported data sources in a single query.

You can download the query execution results from the {{ yq-full-name }} user interface. If required, you can also save them to {{ objstorage-full-name }}.

### {{ datalens-full-name }}
With {{ yq-full-name }}, you can visualize data stored in {{ objstorage-full-name }}.

{% include [clickhouse-disclaimer](../../_includes/clickhouse-disclaimer.md) %}
